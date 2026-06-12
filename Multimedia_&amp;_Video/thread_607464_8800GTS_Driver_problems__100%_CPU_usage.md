---
title: "8800GTS Driver problems / 100% CPU usage"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by charper_99 on 2007-11-08
Ok... I'm running Gutsy on an Asus P5E, a dual core CPU, and an 8800GTS card.  Compiz works flawlessly, and only utilizes 1-2% of my CPU at the most.  Transparent cube with gears in the middle uses about 1%.  So... here's my problem.

Despite this success, some things appear to use far too much CPU.  Glxgears uses 100% of my CPU, with 100% to glxgears, 55ish to Xorg, and 45ish to compiz.real, Load just above 2.0.  Getting about 16k FPS.  Euphoria (screensaver) is the same way - it uses an entire core (but the other core is idle).  Sometimes (not always - can't figure it out) the system hard locks (no console, no exiting X, anything) when I exit the screensaver preview window.

I've run this on 2.6 generic and rt kernels with the same results.  I don't have xserver-xgl package installed.  NVidia settings manager agrees that I'm running current drivers (100.14.19).  This problem is present using the restricted drivers, compiling Nvidia drivers manually, and allowing Envy to install.  

I'm out of ideas; here's to hoping somebody more knowledgeable and creative comes along.
Thanks in advance guys...

---

### Post by phelge on 2007-11-09
Hello, you seem to have the problem described here : [http://www.nvnews.net/vbulletin/showthread.php?t=87865](http://www.nvnews.net/vbulletin/showthread.php?t=87865)
I'm in the same kind of situation with my Quadro FX1600M (~8700GT).

---

### Post by charper_99 on 2007-11-09
No... not quite.  That's a good forum topic though, and I definitely appreciate it.  My problem may certainly be intertwined with theirs, but it's not as severe.  I couldn't find any 2d apps that would hurt my performance, but I tried a few of their suggestions anyway w/ no impact.  I guess I could get over the screensaver problem - but the random crashes when *closing* the screensaver preview window are unacceptable.  I can't even find a log file containing anything about the error.

---

