# NoName EPG

Automatski TV vodič (XMLTV) za aplikaciju NoName. GitHub ga svaki dan u 03:30 UTC
ponovno skupi i spremi kao `guide.xml.gz`. Program se uzima sa stranica MAXtv-a
(Hrvatska), Telemacha i m:tela (BiH) te mts-a (Srbija), pomoću alata otvorenog
koda [iptv-org/epg](https://github.com/iptv-org/epg).

## Postavljanje (jednom)

1. Napravi **javni** repozitorij na GitHubu, na primjer `noname-epg`.
2. Prenesi u njega datoteke `channels.xml`, `README.md` i `.github/workflows/epg.yml`
   (točno s tom putanjom mapa).
3. Otvori karticu **Settings → Actions → General** i pod *Workflow permissions*
   odaberi **Read and write permissions**, pa spremi.
4. Otvori karticu **Actions**, odaberi *Osvježi TV vodič* i klikni **Run workflow**.
   Prvo pokretanje može potrajati 30 do 90 minuta.
5. Kad završi, u repozitoriju se pojavi `guide.xml.gz`.

## Link za NoName

```
https://raw.githubusercontent.com/KORISNIČKO-IME/noname-epg/main/guide.xml.gz
```

Zamijeni `KORISNIČKO-IME` svojim GitHub imenom i upiši link u polje
*TV vodič, XMLTV adresa* kod M3U izvora.

## Povezivanje s kanalima

Oznaka svakog kanala u vodiču jednaka je njegovom nazivu, na primjer `HRT 1`,
`RTL`, `Federalna TV`, `RTS 1`, `Pink`. Kanal koji postoji kod više izvora
uzet je samo jednom, redom Hrvatska, BiH, Srbija. NoName povezuje vodič s kanalom ako se
`tvg-id`, `tvg-name` ili naziv kanala u M3U listi točno podudara s tom oznakom
(velika i mala slova nisu bitna).

Ako se naziv u tvojoj listi razlikuje, možeš:
- u `channels.xml` promijeniti vrijednost `xmltv_id` u naziv iz svoje liste, ili
- u M3U listi postaviti `tvg-id` na naziv iz `channels.xml`.

## Manje kanala, brže osvježavanje

Obriši iz `channels.xml` retke kanala koje ne gledaš. Manje kanala znači brže
pokretanje i manju datoteku.
