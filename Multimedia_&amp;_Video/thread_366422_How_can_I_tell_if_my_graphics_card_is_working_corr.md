---
title: "How can I tell if my graphics card is working correctly?"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by kwilliam on 2007-02-20
I'm running Dapper, and recently installed a Nvidia GeForce FX 5200 to replace my onboard graphics (ProSavage something) so I can try installing Beryl. I know the grahpics card "works" because I had to edit xorg.conf in order to get my original screen resolution back, and I now get the Nvidia splash screen, however, I was a little confused by some of the output of commands I found in related forum threads.  Basically, I want to make sure that I have the "right things" installed and working.

```
$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```
(This is Good, I think.)

```
$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
```

**This is what confuses me.** Should the "Driver" be something like "NVIDIA"?  What is "AGPGART"? Are "Fast Writes" and "SBA" disabled because the graphics card is too old to know what they are, or should they have been enabled?

```
$ fglrxinfo
bash: fglrxinfo: command not found
```
I've no idea what this command means; I just saw it used in another graphics card thread.

```
$ glxinfo | grep -i direct
direct rendering: Yes
```
I assume this is good?

[b]***
Question: How do I tell if I have the open source Nvidia drivers installed, or am I using the new "binary" drivers, and which should I use to run Beryl?
***[/b]

Lastly, here are the FPS for glxgears -printfps.  Are these reasonable, given the age of the graphics card and that the rest of the compouter is 5 years old?  (AMD Athlon XP 2400+)

```
$ glxgears -printfps
6030 frames in 5.2 seconds = 1162.640 FPS  // normal window
6419 frames in 5.0 seconds = 1283.640 FPS
6666 frames in 5.0 seconds = 1333.140 FPS
6663 frames in 5.0 seconds = 1332.544 FPS
9653 frames in 5.0 seconds = 1930.595 FPS // minimized
19140 frames in 5.0 seconds = 3827.926 FPS
19151 frames in 5.0 seconds = 3830.113 FPS
19096 frames in 5.0 seconds = 3819.004 FPS
19099 frames in 5.0 seconds = 3819.650 FPS
9171 frames in 5.0 seconds = 1831.242 FPS // maximized
601 frames in 5.0 seconds = 120.159 FPS 
599 frames in 5.0 seconds = 119.631 FPS
601 frames in 5.0 seconds = 120.080 FPS
```

I'm pretty sure that the card has been an "upgrade": Video playback is much better (I got lots of bizzare purple and green lines during playback with the onboard graphics, probably a driver issue) and PyDance use to occasionally freeze or jump, but no longer does. So I'm 99% sure that I'm "good to go" but wanted to double check with someone who actually knows about graphics cards before I try to install Beryl on Dapper.

---

### Post by barney_1 on 2007-02-21
I am also interested in the answers to these questions.  Sometimes I feel like I'm not getting the performance from my Geforce 7800 GTX that I should.

---

