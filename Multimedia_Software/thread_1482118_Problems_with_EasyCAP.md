---
title: "Problems with EasyCAP"
date: 2010-05-13
forum: Multimedia Software
---

### Post by treaki on 2010-05-13
hi,

i have the same problem like
[http://ubuntuforums.org/showthread.php?t=662531](http://ubuntuforums.org/showthread.php?t=662531)

but i cant compile the driver:

```

treaki@tjarksrechner:~/stk11xx-2.1.0$ make -f Makefile.standalone clean
make -C /lib/modules/2.6.28-18-generic/build SUBDIRS=/home/treaki/stk11xx-2.1.0 clean
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.28-18-generic'
  CLEAN   /home/treaki/stk11xx-2.1.0/.tmp_versions
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.28-18-generic'
treaki@tjarksrechner:~/stk11xx-2.1.0$ make -f Makefile.standalone 
make -C /lib/modules/2.6.28-18-generic/build SUBDIRS=/home/treaki/stk11xx-2.1.0 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.28-18-generic'
  CC [M]  /home/treaki/stk11xx-2.1.0/stk11xx-usb.o
  CC [M]  /home/treaki/stk11xx-2.1.0/stk11xx-v4l.o
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c: In Funktion »v4l_stk11xx_ioctl«:
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1662: Warnung: Übergabe des Arguments 1 von »video_usercopy« von inkompatiblem Zeigertyp
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1662: Warnung: Übergabe des Arguments 2 von »video_usercopy« erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1662: Warnung: Übergabe des Arguments 4 von »video_usercopy«  erzeugt Ganzzahl von Zeiger ohne Typkonvertierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1662: Fehler: Zu wenige Argumente für Funktion »video_usercopy«
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c: In Funktion »v4l_stk11xx_register_video_device«:
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1686: Warnung: Zuweisung von inkompatiblem Zeigertyp
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c: Auf höchster Ebene:
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1728: Fehler: Variable »v4l_stk11xx_fops« hat Initialisierung, aber unvollständigen Typ
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1729: Fehler: unbekanntes Feld »owner« in Initialisierung angegeben
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1729: Warnung: Elementüberschreitung in struct-Initialisierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1729: Warnung: (nahe der Initialisierung für »v4l_stk11xx_fops«)
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1730: Fehler: unbekanntes Feld »open« in Initialisierung angegeben
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1730: Warnung: Elementüberschreitung in struct-Initialisierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1730: Warnung: (nahe der Initialisierung für »v4l_stk11xx_fops«)
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1731: Fehler: unbekanntes Feld »release« in Initialisierung angegeben
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1731: Warnung: Elementüberschreitung in struct-Initialisierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1731: Warnung: (nahe der Initialisierung für »v4l_stk11xx_fops«)
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1732: Fehler: unbekanntes Feld »read« in Initialisierung angegeben
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1732: Warnung: Elementüberschreitung in struct-Initialisierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1732: Warnung: (nahe der Initialisierung für »v4l_stk11xx_fops«)
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1733: Fehler: unbekanntes Feld »poll« in Initialisierung angegeben
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1733: Warnung: Elementüberschreitung in struct-Initialisierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1733: Warnung: (nahe der Initialisierung für »v4l_stk11xx_fops«)
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1734: Fehler: unbekanntes Feld »mmap« in Initialisierung angegeben
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1734: Warnung: Elementüberschreitung in struct-Initialisierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1734: Warnung: (nahe der Initialisierung für »v4l_stk11xx_fops«)
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1735: Fehler: unbekanntes Feld »ioctl« in Initialisierung angegeben
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1735: Warnung: Elementüberschreitung in struct-Initialisierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1735: Warnung: (nahe der Initialisierung für »v4l_stk11xx_fops«)
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1737: Fehler: unbekanntes Feld »compat_ioctl« in Initialisierung angegeben
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1737: Warnung: Elementüberschreitung in struct-Initialisierung
/home/treaki/stk11xx-2.1.0/stk11xx-v4l.c:1737: Warnung: (nahe der Initialisierung für »v4l_stk11xx_fops«)
make[2]: *** [/home/treaki/stk11xx-2.1.0/stk11xx-v4l.o] Fehler 1
make[1]: *** [_module_/home/treaki/stk11xx-2.1.0] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.28-18-generic'
make: *** [driver] Fehler 2

```what do i make wrong?

thx treaki

---

### Post by rmt1947 on 2010-05-14
There is a more up-to-date and much longer thread relating to the EasyCAP DC60 device (USB ID 05e1:0408) at

[http://ubuntuforums.org/showthread.php?t=924504](http://ubuntuforums.org/showthread.php?t=924504)

---

