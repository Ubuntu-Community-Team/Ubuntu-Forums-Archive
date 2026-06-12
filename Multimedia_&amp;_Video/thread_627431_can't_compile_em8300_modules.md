---
title: "can't compile em8300 modules"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by deadland on 2007-11-30
Hi I use gutsy and I want to set up a VDR, but I can't build the gutsy em8300-source:

```
root@vdr:/usr/src/modules/em8300# make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/modules/em8300 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/modules/em8300/adv717x.o
In file included from /usr/src/modules/em8300/adv717x.c:50:
/usr/src/modules/em8300/em8300.h:269: Fehler: expected specifier-qualifier-list before »snd_card_t«
/usr/src/modules/em8300/adv717x.c: In Funktion »adv717x_setup«:
/usr/src/modules/em8300/adv717x.c:573: Fehler: »struct em8300_s« hat kein Element namens »card_nr«
/usr/src/modules/em8300/adv717x.c:575: Fehler: »struct em8300_s« hat kein Element namens »card_nr«
/usr/src/modules/em8300/adv717x.c:580: Fehler: »struct em8300_s« hat kein Element namens »card_nr«
/usr/src/modules/em8300/adv717x.c:585: Fehler: »struct em8300_s« hat kein Element namens »card_nr«
/usr/src/modules/em8300/adv717x.c:586: Fehler: »struct em8300_s« hat kein Element namens »card_nr«
/usr/src/modules/em8300/adv717x.c:588: Fehler: »struct em8300_s« hat kein Element namens »card_nr«
/usr/src/modules/em8300/adv717x.c:591: Fehler: »struct em8300_s« hat kein Element namens »card_nr«
make[2]: *** [/usr/src/modules/em8300/adv717x.o] Fehler 1
make[1]: *** [_module_/usr/src/modules/em8300] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
make: *** [build] Fehler 2

```

Anyone can help me? 

I also tried the source from [http://dxr3.sourceforge.net/download.html](http://dxr3.sourceforge.net/download.html) but the dxr3-source doesn't fit to the kernel 2.6.22. It says:

```
root@vdr:/usr/src/em8300-0.16.3/modules# modprobe em8300
FATAL: Error inserting em8300 (/lib/modules/2.6.22-14-generic/em8300/em8300.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

So no chance with the gutsy-source neither with the original source. What can I do?

---

