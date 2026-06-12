---
title: "radeon 9200pro with dri"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by ahnkle on 2005-11-18
Hi,

New to kubuntu: not too bad so far...

After struggling with getting DRI working, I think I did it. i tried the ati binary driver fglrx, but it complained about DRI version mismatch, so went back to the xorg radeon driver.

My xorg.conf driver section loks like this:

[HTML]
Section "Device"
  Identifier   "xorg-radeon"
  Driver       "radeon"
  BusID        "PCI:1:0:0"

  option "monitorlayout" "TDMS, CRT"

  option "noaccel" "false"
  option "agpmode" "4"
  option "agpfastwrite" "true"
EndSection
[/HTML]

Not completely sure 3d acceleration is on; I haven't seen a definitive test (although tuxracer works fine). But glxinfo seems to indicate it's there:

[HTML]
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
[/HTML]

---

### Post by giftnudel on 2005-11-23
Hi,

yes it is working, so what is your question?

giftnudel

---

### Post by Teroedni on 2005-11-23
If you can run tuxracer i would say it is okay:)
I have found tuxracer to demand quite a lot from the graphics card so if it works , you should be satisfied.

Could you mark this thread as [Solved]?

Thanks:KS

---

