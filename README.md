# Richi PWA

Progressive Web App mit Schnellzugriff auf:

- Richi Docker – https://docker.richi.be
- Leihkiste – https://r118-leihkiste.lovable.app
- Quartierraum – https://r118.ch/quartierraum/
- Bastelraum – https://r118.ch/bastelraum/

Reine statische Seite, kein Build-Schritt. Alle Pfade sind relativ, daher läuft sie unter `https://<user>.github.io/<repo>/` ebenso wie unter einer eigenen Domain.

## Deployment (GitHub Pages)

1. Neues Repository auf GitHub anlegen und diesen Ordner pushen.
2. *Settings → Pages → Build and deployment*: Source **Deploy from a branch**, Branch `main`, Ordner `/ (root)`.
3. Nach ca. 1 Minute erreichbar unter `https://<user>.github.io/<repo>/`.

## Links ändern

Die Kacheln stehen direkt in `index.html` (`<ul class="grid">`). Nach Änderungen an Dateien in `sw.js` die Konstante `VERSION` erhöhen, damit der Cache erneuert wird.

## Icons neu erzeugen

`logo.png` ersetzen und die Icons aus der linken, quadratischen Illustration neu schneiden (Pillow):

```python
from PIL import Image
im = Image.open("logo.png").convert("RGB"); h = im.size[1]
art = im.crop((0, 0, h, h))
```

## Lokal testen

```bash
python3 -m http.server 8080
```

Dann http://localhost:8080 öffnen (Service Worker funktioniert auf `localhost`).
