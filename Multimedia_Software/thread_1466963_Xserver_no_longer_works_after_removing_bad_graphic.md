---
title: "Xserver no longer works after removing bad graphics card."
date: 2010-04-30
forum: Multimedia Software
---

### Post by Intelligitimate on 2010-04-30
Ok, I usually only come here to ask questions when I've lost all hope. I've been asking questions in #ubuntu, searching the internet and trying things, etc, for days now. I fixed some of the problems on my own, but one is persisting. I know you guys like information, so I am going to try and include as much as possible in a story-like format.

It all started Tuesday morning. I woke up and turned my computer on. Normally I just leave it on all the time, but I turned it off the previous night for some reason. When I turned it on, everything worked fine for about 10 minutes, until my monitor said "Monitor Working Out of Scan Range." I messed with the settings on the monitor to try and get it back, but to no avail. Restarting would make it work, but for even shorter periods. It eventually would display the manufacturer image (Everex), and then go dead again with the same message.

I thought it was the monitor at first, and got a new one. The new one is a wide screen 18.5 inch Dell IN1910N. The problem persisted, so I knew it wasn't this. I kinda figured it out when I started smelling something burning coming from my computer, and discovered it was the graphics card I installed awhile back. It is the pci ATI X1550, and its fan no longer worked.

So I figured, well, I will just remove it and go back to the onboard video. Doing this worked fine, until I got to the stage where it tried to boot to the Xserver, and then the computer just hangs. No sounds indicate I ever get to a logon screen or anything.

Now, I tried commands like sudo dpkg-configure xserver-xorg, and it asked me a lot of questions about my keyboard, but didn't fix my video. I also tried the "Xfix" option in recovery mode, and it purged all the old fglrx drivers, but that didn't help either.

I am currently using a live CD (I was doing straight command-line for awhile, after I also played hell getting the wireless working). I tried literally coping and pasting the entire contents of the X11 folder over, but that didn't work either (the xorg.conf files were the same anyway). I don't know what to do to get my old partition to boot X correctly.

All the commands I was copying before are not in my terminal now, and I'm not sure exactly what command-line information you need. I know that Openchrome is supposed to run the onboard VIA video, but I don't recall the command that tells me everything about it.

---

### Post by Intelligitimate on 2010-04-30
I'm pretty sure also my original version was either Hardy Heron or Intrepid Ibex. The Live CD is Intrepid.

---

### Post by Intelligitimate on 2010-05-01
bump

---

### Post by Intelligitimate on 2010-05-01
bump

---

### Post by Intelligitimate on 2010-05-02
bump

---

### Post by lidex on 2010-05-02
What is the output of this command:
```
lspci -nn | grep VGA
```

---

