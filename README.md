# stratum-releases

Fertig gebaute Versionen von stratum für Linux x86_64 samt Installationsskript.
Das Binary braucht glibc 2.31 oder neuer, läuft also unter Ubuntu ab 20.04 und
Debian ab 11, auch in WSL2.

## Installation unter WSL2

In der WSL-Konsole (Ubuntu oder Debian) als normaler Benutzer:

```sh
curl -fsSLO https://github.com/yalmn/stratum-releases/releases/latest/download/install.sh
bash install.sh
```

Das Skript

- installiert PostgreSQL, YARA (ab 4.5), nslookup, whois und prlimit,
- lädt das Release-Archiv und prüft dessen SHA-256,
- legt Datenbank, Konfiguration (`/etc/stratum/stratum.toml`) und die Ordner
  unter `~/stratum` an,
- startet den Server und prüft am Ende die ganze Installation.

Danach im Windows-Browser `http://localhost:8080` öffnen.

**Demo-Betrieb:** Diese Versionen laufen mit der Anmeldung
`superadmin` / `superadmin` ohne Pflicht zum Passwortwechsel. Sie sind nur für
Vorführungen gedacht, nicht für echte Fallarbeit. Der Server lauscht
ausschließlich auf 127.0.0.1.

## Image bereitstellen

Das Image nicht direkt von `C:\` analysieren, sondern im Windows-Explorer nach
`\\wsl.localhost\<Distribution>\home\<Benutzer>\stratum\faelle\DEMO-001`
kopieren. In stratum dann den Fall mit diesem Fallordner anlegen und das Image
unter Evidence auswählen.

## Bedienung

```sh
stratum-demo start     # PostgreSQL und Server starten
stratum-demo stop      # Server beenden
stratum-demo status
stratum-demo log       # Serverprotokoll verfolgen
```

Das WSL-Fenster während der Arbeit offen lassen. Nach einem Neustart von
Windows oder WSL genügt `stratum-demo start`.
