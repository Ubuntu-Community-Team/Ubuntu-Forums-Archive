---
title: "Odd flash problem - sync issue maybe?"
date: 2008-12-01
forum: Multimedia Software
---

### Post by dbutler1986 on 2008-12-01
Hello,

I recently upgraded to 8.10. It took awhile to get everything working with my video card (nVidia GeForce 8 series) but now everything works superbly, except for one problem: flash content displayed in Firefox flickers, tears, stutters, and otherwise looks like crap, as well as running ridiculously slowly. Flash FLV players (such as Youtube) don't flicker, but they do tear and stutter, as well as causing Firefox to become unresponsive for 30 seconds at a time at several points throughout the video. I haven't any idea how to figure out what the problem is, although since everything else works perfectly I *assume* the problem is either Firefox or the Flash plugin. Any ideas?

---

### Post by dbutler1986 on 2008-12-07
Well. If anybody's interested, this is fixed by setting Compiz to indirect rendering and setting the InitialPixmapPlacement to 2.

---

### Post by river_plate_2005 on 2008-12-07
I have this same problem and i think i have you same card!..... gforce 8200m on my compaq cq laptop...
how to you change compiz's rendering ?
thanks a lot..cant wait to see if this works...sooo happy

---

### Post by dbutler1986 on 2008-12-07
Put "nvidia-settings -a InitialPixmapPlacement=2" into your ~/.profile file, and sudo aptitude install fusion-icon. Then you'll get a system tray icon for controlling Compiz and Emerald.

---

### Post by 900donuts on 2008-12-07
I have the same flash problem but my comptuer is different 

I turned compiz off and I have a geforce 4400ti graphics card and i'm running 8.04

---

### Post by dbutler1986 on 2008-12-07
I don't know that a 4400 is powerful enough to run Compiz well.

---

### Post by river_plate_2005 on 2008-12-07
i still dont get it to work...i dont know why...why doesnt this workkkkkk.....any other ideas? need any info..lemme know
thanks a lot again

---

