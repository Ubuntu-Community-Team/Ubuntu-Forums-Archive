---
title: "poulsbo video driver"
date: 2009-06-11
forum: Multimedia Software
---

### Post by metalfan_ on 2009-06-11
Hi,

ive added the ubuntu mobile ppa repository in jaunty, but running:

```

sudo aptitude install psb-modules

```

results in:

```

sudo aptitude install psb-modules
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Lese erweiterte Statusinformationen      
Initialisiere Paketstatus... Fertig
Die folgenden teilweise installierten Pakete werden konfiguriert:
  psb-kernel-source 
0 Pakete aktualisiert, 0 zusätzlich installiert, 0 werden entfernt und 0 nicht aktualisiert.
Muss 0B an Archiven herunterladen. Nach dem Entpacken werden 0B zusätzlich belegt sein.
Schreibe erweiterte Statusinformationen... Fertig
Richte psb-kernel-source ein (4.40-0ubuntu1~904um1) ...
Loading new psb-kernel-source-4.40 DKMS files...

Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.40 does not exist.
dpkg: Fehler beim Bearbeiten von psb-kernel-source (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 psb-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ein Paket konnte nicht installiert werden. Versuche zu lösen:
Richte psb-kernel-source ein (4.40-0ubuntu1~904um1) ...
Loading new psb-kernel-source-4.40 DKMS files...

Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.40 does not exist.
dpkg: Fehler beim Bearbeiten von psb-kernel-source (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 psb-kernel-source
Paketlisten werden gelesen... Fertig             
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Lese erweiterte Statusinformationen      
Initialisiere Paketstatus... Fertig

```


what can i do?

---

### Post by metalfan_ on 2009-08-06
Got it working with unbuntu intrepid, dont know what i changed...

---

