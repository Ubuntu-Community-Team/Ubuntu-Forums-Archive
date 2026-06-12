---
title: "Ubuntu 9.10 x64, Samsung LN40C530"
date: 2010-04-15
forum: Multimedia Software
---

### Post by SmelliRelli on 2010-04-15
First time posting; hope I'm going about this right!
 
Video card: nVidia G86 GeForce 8500 GT (rev a1) (lspci | grep VGA)
Monitor: Samsung LN40C530, recently switch to from a generic Gateway 17" monitor that worked fine
 
I've been using 9.10 x64 from a clean install since it came out and it's been working great. I recently upgraded my monitor from a generic 17" Gateway monitor to a Samsung 40" widescreen HDTV (LN40C530), and that's when the trouble began.
 
At first, the screen would lock up and become inactive. I could move the mouse, but clicking did nothing and the clock wouldn't update. I also could not switch to a terminal via Alt+F1, I could only do a hard reboot.
 
Then, when it started booting up, I would get horizontal black and white lines (which I'm still getting). Usually, it boots to the white glowing Ubuntu logo as files load in the background (@ 640x480, 60hz). When it tries to bring up the login screen (autodetected 1920x1080, 60z), I get horizontal white lines across. (see pics) Happens booting off both Live CD and HDD. When I use safe graphics mode on live cd, it boots okay @ 1600x1200, 60hz. After installing under safe graphics mode, it gives me a message "no modes available, resolution unsupported".
 
Right now, I'm back at trying to install 9.10 x64 (Karmic Koala) with either 1920x1080 or 1360x768 @ 60hz. I'm using a DVI out to a DVI/VGA adapter, and a VGA cable between the adapter and the PC port on TV. 
 
I've tried default configurations, restricted drivers 173, 185, and nVidia's 195. When I'm able to get to a terminal, I've tried sudo X -configure, but testing w/ X -config yields the same broken result. When I Alt+k+PrntScr, it does refresh but brings up the same white lines. Sometimes it boots just fine and even autodetects as "Samsung 40", but not as of the last 30 or so boots.
 
Let me know where I can start for proper troubleshooting; I'm not sure which log files are important for this issue. Do you think I might just need to create a customized X config with exactly what I need?
 
P.S. please provide any links that describe how X or nVidia displays the screen in 9.10, I've noticed that there isn't an xorg.conf by default and was wondering why. Thank you very much ahead of time; this user community is great!
 
[ATTACH]153314[/ATTACH]
 
[ATTACH]153315[/ATTACH]
 
[ATTACH]153316[/ATTACH]

---

### Post by SmelliRelli on 2010-04-21
After days of messing w/ drivers and xorg.conf settings, I packed it in and bought a new video card w/ HDMI out. For some reason now, everything is being detected wonderfully. Sorry to those looking for an actual answer; maybe you'll find some help at this thread:
 
[http://ubuntuforums.org/showthread.php?t=1181631](http://ubuntuforums.org/showthread.php?t=1181631)

---

