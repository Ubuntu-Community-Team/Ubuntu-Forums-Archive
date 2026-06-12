---
title: "copywritten DVD issues"
date: 2010-02-13
forum: Multimedia Software
---

### Post by rtz2rbbl on 2010-02-13
I have a pioneer DVD burner/reader and a lite-on Bluray player, running karmic koala with all updates. I can't get any form of legit DVD to play in either drive with movie player, VLC or Mplayer (Real DVDs wont play, but non copy protected stuff does). Sometimes i get this error with movie player "Could not read location: you might not have permission to read the file". Other times movie player just closes. VLC and Mplayer just dont do anything at all.

---

### Post by mc4man on 2010-02-13
Run this and then try vlc again, - if no good start vlc from a terminal like this and try to play, post output 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

```
vlc -vv
```

---

### Post by rtz2rbbl on 2010-02-13
everytime it asks me for my sudo password i try to type it in...but nothing types.

---

### Post by rtz2rbbl on 2010-02-13
nevermind...guess letters arent supposed to show up

---

### Post by rtz2rbbl on 2010-02-13
the first part fixed it! Thanks sooo much!

---

### Post by d0ubl3a on 2010-02-13
Hello, I encountered the same problem. The difference is that I can't make it work whatever I try. I installed the Medibuntu repositories, I installed libdvdcss, I tryed installing libdvdcss2... etc. I tried quite a lot of multimedia players. I played non-encrypted dvds with VLC and it worked just fine. But when I start this one... or these ones... because it is a 14 DVD piano course...  I get the menu... but I can't press any of the buttons. If I open the dvds and go to video... there are a couple of .bup, .info and .vob files, and I can't open them with VLC.
I tried to play them with totem, but it does not work. If I want to open the disc I get the error:
"Could not open location; you might not have permission to open the file."
And if I try to open the .vob files I get the error:
"Could not read from resource"
I tried opening the disc with totem from the terminal... and this is what I get:


libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: no file info
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(361): rsn_dvdsrc_start (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: File exists

libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(361): rsn_dvdsrc_start (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: File exists

Please help me... it's really bugging me... and I need those courses...

---

