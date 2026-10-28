# Szamizdat-adatbázis – feltöltőfelület

Böngészős feltöltő- és szerkesztőfelület egy magyar–lengyel szamizdatkiadvány-adatbázishoz.
Az adatok egy Supabase (PostgreSQL) adatbázisban vannak; a felület csak bejelentkezett,
a munkatársak listáján szereplő felhasználóknak mutat és enged szerkeszteni adatot
(sorszintű jogosultságkezelés, minden módosítás naplózva).

## Mit tud

- **Tételek** hierarchiában: periodika (s) → szám (b) → cikk (a), illetve önálló kiadvány (m);
  a cikk a számtól örökli a kiadói, dátum- és előállítási adatokat.
- **Entitások** (személy, testület, hely, fogalom, esemény) névváltozatokkal, külső azonosítókkal
  (Wikidata, VIAF, GND, GeoNames, FactGrid, ISNI) és bővíthető, forrásolt állításokkal.
- **Wikidata-egyeztetés** a böngészőből (további azonosítók és adatok átvételével).
- **Dátumkezelés** EDTF-ben (ISO 8601-2) + legkorábbi/legkésőbbi lehetséges nap; a MARC 008/06
  dátumtípust az export számolja.
- **Export**: MARC 21 (MARCXML, ISO 2709 `.mrc`, MarcEdit `.mrk`) és lapos CSV.
  Wikidata-URI a `$1`, VIAF/GND/ISNI a `$0` almezőben.
- Ellenőrzendő kérdések, szótárkezelés, változásnapló.

## Hozzáférés

Új munkatárs: a Supabase-projektben *Authentication → Users → Add user* (Auto Confirm),
majd a felületen *Szótárak → munkatársak* alatt felvenni.

A felületben szereplő Supabase-kulcs nyilvános (publishable) kulcs; az adatokhoz
csak bejelentkezéssel és munkatársi jogosultsággal lehet hozzáférni.
