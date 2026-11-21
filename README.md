# PDN naar Word

`pdn-naar-word` zet een PDN-bestand met dampartijen om naar een
Word-document (`.docx`). Het document bevat alle partijen, tags, zetten,
varianten, commentaren en uitslagen. Een markering `{[#]}` of `{#}` in een
commentaar wordt een diagram van de stand op die plek, ook binnen varianten.

Deze repository bevat alleen de downloads; de broncode staat elders.

## Downloaden

Download de nieuwste versie onder
[Releases](https://github.com/tobyhage/pdn-naar-word/releases/latest):

- `pdn-naar-word-windows-x64.zip`: het programma voor Windows 10/11 (64-bit),
  samen met de stijl `style-damkunst`;
- `SHA256SUMS.txt`: controlecijfers.

Pak de zip uit in een map naar keuze. Installeren is niet nodig.

Het programma is niet digitaal ondertekend. Windows kan daarom bij de eerste
start waarschuwen. Kies dan **Meer informatie → Toch uitvoeren**, of
rechtsklik op `pdn-naar-word.exe` → **Eigenschappen** → **Blokkering
opheffen**.

## Gebruik

Open PowerShell in de map met het programma en de PDN:

```powershell
.\pdn-naar-word.exe partijen.pdn
.\pdn-naar-word.exe partijen.pdn --output boek.docx
.\pdn-naar-word.exe partijen.pdn --style style-damkunst --piece-fit 0.8
```

- Zonder `--output` komt `partijen.docx` naast het PDN-bestand. Na afloop
  meldt het programma `Word-document opgeslagen: …`.
- Een bestaand `.docx` wordt nooit overschreven; dan verschijnt een
  foutmelding.
- Het PDN-bestand moet UTF-8 zijn.

| Optie | Standaard | Betekenis |
|---|---|---|
| `--output` | `<naam>.docx` | Pad van het Word-document. |
| `--style` | ingebouwd | Map met `board.svg`, `wM.svg`, `wK.svg`, `bM.svg` en `bK.svg`. |
| `--diagram-width-cm` | 5 | Breedte van een diagram in Word. |
| `--dpi` | 300 | Resolutie van de diagrammen. |
| `--piece-fit` | 0.9 | Grootte van een steen binnen een veld (groter dan 0, hoogstens 1). |

## Problemen

Verschijnt er geen document en ook geen melding, typ dan direct na het
commando `$LASTEXITCODE` en geef dat getal door:

- `-1073741795` betekent dat het programma een instructie gebruikt die de
  processor niet kent. Vanaf versie 0.1.0 zou dat niet meer moeten gebeuren.
- `-1073741515` betekent dat er een systeembestand (DLL) ontbreekt.

## Stijl `style-damkunst`

De stenen zijn de ronde "fabirovsky"-stenen van de Damkunst-diagrammaker.
Het bord gebruikt blauwgrijze velden.
