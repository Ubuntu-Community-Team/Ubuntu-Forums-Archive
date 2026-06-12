---
title: "SiS, WinTV, TV Card, tvtime, video output, xorg, x11"
date: 2005-11-23
forum: Multimedia &amp; Video
---

### Post by motionsiren on 2005-11-23
[SOLVED]
Simple stuff. Firstly, from a command prompt, type: gstreamer-properties and then select the Video tab...
test each setting and apply on the best solution.

Nice gstreamer central app. made things easier then I thought ;)





A fresh 5.10 install with my WinTV card installed, running a GeForce fx5200 AGP card. Things ran flawlessly. Video, sound.. it all worked out of the box. I was impressed.

The second time around, I used all the same hardware - except for the GeForce fx5200 video card. Im now using my onboard video, which lspci reports is a

```
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
```

The problem: the video display will now show any video, however, taking screenshots within tvtime work perfect (nice feature BTW)... 

The solution (best guess): This is related to my crummy on-board video. I think, either within tvtime, xorg.conf or the kernel (doubtful) should fix the 'overlay(?)' problem. 

Back when I used mplayer (pretty much a VLC user now) i remember modifying it's user-land conf, switching the video output from x11 to xv, er vice versa.. er.. something like that. Am I on the right track here?

Starting tvtime in verbose mode shows nothing wrong (another reason to beleive the TV card and my sound card work just fine (and remember, i can take screenshots....)


just can't see anything on the screen itself ;)


thanks for any help I may get on this.

---

### Post by ranf on 2005-11-24
I also have this SiS card (but no TV card).
I have installed Sisctl from this source:
```
#deb http://www.winischhofer.net/sis/debian/unstable ./  #SiS
```

It lets you change some settings and gives hints for modifying `xorg.conf'.

---

### Post by motionsiren on 2006-04-05
Nice! Thanks! Will look into this.

---

