# guiAPI
Jednoduché vytváření uživatelského rozhraní pro computercraft (minecraft mod)

# Ukázka kódu
V souboru Designer se definují veškeré formulářové prvky. Každý formulářový prvek má metodu *new*, která funguje jako konstruktor.
Prvek s prázdným konstruktorem bude mít všechny hodnoty výchozí a vykreslí se do levého horního rohu.
```
local label = Label.new()
local button = Button.new({
    layoutX = 7,
})
```

Prvky se na formulář přidávají touto metodou:
```
Form.component.add(label)
Form.component.add(button)
```

To je vše. Po spuštění se vykreslí popisek a vedle tlačítko.

# Motivace
Na internetu existuje jen velmi málo projektů s touto tématikou. Zatím jsem nenašel projekt, který by byl dostatečně jednoduchý na použití a zároveň výkonný.

# Instalace

# API Reference
Každá formulářová kontrolka je potomkem třídy **Region**. Každá formulářová kontrolka která obsahuje text (Label, Button) je potomkem třídy **Labeled**. Region je potomkem třídy Node, který dědí z třídy BaseObject.

## Třída BaseObject
Základní objekt pro formulářové kontrolky.
- Vlastnosti
  - id - Každý objekt musí mít vlastní unikátní ID. Výchozí = náhodně generovaný řetězec o pěti znacích.
- Funkce
  - __tostring - Vrátí id objektu.

## Třída Node
Objekt definující základní vlastnosti a funkce.
- Vlastnosti
  - disabled - Použitelnost kontrolky (zda-li se s ní dá interagovat). Výchozí = false.
  - visible - Viditelnost kontrolky. Výchozí = true.
  - pageIndex - Index stránky, na které se kontrolka kreslí. Podpora více formulářů. Výchozí = 1.
  - layoutX - X-ová souřadnice kontrolky z levého horního rohu okna. Výchozí = 0.
  - layoutY - Y-ová souřadnice kontrolky z levého horního rohu okna. Výchozí = 0.
  - theme - Vzhled formulářového prvku. Výchozí = STANDART.
- Funkce
  - draw - Funkce která se stará o vykreslení prvku.
  - onKeyPress - Funkce volaná po stisku klávesy.
  - onKeyUp - Funkce volaná po uvolnění klávesy.
  - onMouseClick - Funkce volaná po stisku tlačítka na myši.
  - onMouseUp - Funkce volaná po uvolnění tlačítka myši.
  - onMouseScroll - Funkce volaná při skrolování.
  - onMouseDrag - Funkce volaná při pohybu se stisknutým tlačítkem myši.
  
## Třída Region
Objekt definující informace o velikosti kontrolky.
- Vlastnosti
  - width - Šířka kontrolky. Výchozí = 7.
  - height - Výška kontrolky. Výchozí = 7.
  - autosize - Automatické přizpůsobení se velikosti. Výchozí = true
- Funkce
  - getMinX - Vrátí X-ovou souřadnici levého horního rohu kontrolky.
  - getMinY - Vrátí Y-ovou souřadnici leveho horního rohu kontrolky.
  - getMaxX - Vrátí X-ovou souřadnici pravého spodního rohu kontrolky.
  - getMaxY - Vrátí Y-ovou souřadnici pravého spodního rohu kontrolky.
  - contains - Vrátí true, pokud kontrolka obsahuje zadané souřadnice.

## Třída Labeled
Objekt definující informace o textu.
- Vlastnosti
  - text - Text kontrolky
- Funkce
  - prepareRenterText - Připraví vykreslení textu - nastaví správné souřadnice a barvu textu a pozadí.
  - renderText - Vykreslí text na připravenou pozici.

## Třída Label
První formulářová kontrolka sloužící pro vykreslení jednoduchého popisku.
- Vlastnosti
  - background - Pozadí kontrolky bez textu.
  - textColor - Barva textu.
  - textBackground - Barva pozadí textu.
- Funkce

## Třída Button
Formulářový prvek pro tlačítko. Text v tlačítku je reprezentován jako popisek.
- Vlastnosti
  - background - Pozadí kontrolky bez textu.
  - textColor - Barva textu.
  - textBackground - Barva pozadí textu.
- Funkce

## Třída Util
Pomocná třída pro usnadnění některých rutinních čiností.
- Vlastnosti
- Funkce
  - printString - Vypíše řetězec na obrazovku.
  - printTable - Vypíše obsah tabulky. Používá rekurzi, takže je-li nějaká hodnota obsahu taky tabulka, vypíše se i její obsah.
  - randomString - vrátí náhodný řetězec o zadané délce.
  - dump - Zapíše obsah proměnný do souboru.
  - center - Vypočíta střední hodnotu pro zadaný text na zadané šířce.
  - shorterString - Vrátí podřetězec zadané délky.
