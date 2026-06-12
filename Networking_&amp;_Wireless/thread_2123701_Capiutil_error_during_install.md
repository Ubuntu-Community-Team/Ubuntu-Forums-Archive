---
title: "Capiutil error during install"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by wangom on 2013-03-08
Hey there.

I am trying for a few Days to install Capiutils on my System.
Its importand for by using a ISDN Fritz!Card, for usig my Computer as Fax Device.

i have Ubuntu 12.10 with 3.8.0-030800-generic Kernel.

So this is the Error Message:

```

Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Die folgenden NEUEN Pakete werden installiert:
  capiutils
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0 B von 62,0 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 237 kB Plattenplatz zusätzlich benutzt.
Vormals nicht ausgewähltes Paket capiutils wird gewählt.
(Lese Datenbank ... 208276 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von capiutils (aus .../capiutils_1%3a3.12.20071127-0ubuntu11_i386.deb) ...
Trigger für ureadahead werden verarbeitet ...
Trigger für man-db werden verarbeitet ...
capiutils (1:3.12.20071127-0ubuntu11) wird eingerichtet ...
Note: running MAKEDEV to create CAPI devices in /dev...
mount: unbekannter Dateisystemtyp „capifs“
invoke-rc.d: initscript capiutils, action "start" failed.
dpkg: Fehler beim Bearbeiten von capiutils (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 32 zurück
Fehler traten auf beim Bearbeiten von:
 capiutils
E: Sub-process /usr/bin/dpkg returned an error code (1)



```
 
Thanks all

---

