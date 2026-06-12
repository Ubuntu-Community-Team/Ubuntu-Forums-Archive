---
title: "Tovid menu fails"
date: 2010-12-30
forum: Multimedia Software
---

### Post by richardgundersen on 2010-12-30
Hi, I'm trying to make a DVD menu with Tovid (makemenu) and it fails with this:

makemenu -debug -noask "One" "Two" -out MyMenu

To mpeg:
ppmtoy4m -S 420mpeg2 -A 10:11 -F 30000:1001 -n 119 -r "/home/acme/me/dvdexport/MyMenu.0/menu.ppm" 2>>makemenu.log | mpeg2enc -a 2 -f 8 -F 4 -n n -o "/home/acme/me/dvdexport/MyMenu.0/video.m2v" >> makemenu.log 2>&1
**ERROR: [ppmtoy4m] Failed to open '/home/acme/me/dvdexport/MyMenu.0/menu.ppm': No such file or directory
INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: system error (failed read/write)!


Mux:
mplex -V -f 8 -o "/home/acme/me/dvdexport/MyMenu.0/menu.mpg" "/home/acme/me/dvdexport/MyMenu.0/video.m2v" "/home/acme/me/dvdexport/MyMenu.0/audio.ac3" >> makemenu.log 2>&1
INFO: [mplex] mplex version 1.9.0 (2.2.7 $Date: 2006/02/01 22:23:01 $)
**ERROR: [mplex] Unable to open file /home/acme/me/dvdexport/MyMenu.0/video.m2v for reading

Does anyone have an idea what might be going wrong?

Thanks

---

