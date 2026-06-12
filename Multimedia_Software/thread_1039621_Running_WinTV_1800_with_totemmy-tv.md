---
title: "Running WinTV 1800 with totem/my-tv"
date: 2009-01-14
forum: Multimedia Software
---

### Post by Mechina on 2009-01-14
Hey guys, i've been trying to get my WinTV 1800 card to work but no luck so far. I'm using Ubunti 8.10 and installed drivers like so: ([http://ubuntuforums.org/showthread.php?t=785476](http://ubuntuforums.org/showthread.php?t=785476))

```
hg clone http://linuxtv.org/hg/v4l-dvb/
cd v4l-dvb
make
sudo make install
```

but when I try to run TV with totem I get an error saying:

```
Totem is missing a channels listing to be able to tune the receiver.
```

and also provides a link, so i went there and it said to to download w_scan to make a channel listing, but when I run w_scan I get the following error:

```

w_scan version 20081106
Info: using DVB adapter auto detection.
   Wrong type, ignoring frontend /dev/dvb/adapter0/frontend0
main:2762: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

```

I also installed my-tv but when I run it just keeps saying:
```

Failed to tune to transponder at (some memory location)
```

and it just keeps repeating that, anyone know how I can get it to run? Thanks.

---

### Post by wirbel2 on 2009-02-14
wintv 1800 means most probably an **ATSC **frontend, so you have to choose the matching frontend type '-f a' in w_scans command line options.

[code]
w_scan version 20081106
Info: using DVB adapter auto detection.
   Wrong type, ignoring frontend /dev/dvb/adapter0/frontend0
main:2762: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
[/QUOTE]

you need -f a for ATSC, please read w_scans command line help.

---

