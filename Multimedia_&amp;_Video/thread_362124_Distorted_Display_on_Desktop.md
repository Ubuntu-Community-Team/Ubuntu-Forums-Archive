---
title: "Distorted Display on Desktop"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by n3cr0fil3 on 2007-02-15
I am wanting to try using Linux again, and I liked Ubuntu the last time I messed around with it, so I got 6.10 and went to install it with the LiveCD and had a distorted display once the desktop appears. I saw that using the Alternative disc would help, so I got it, got Ubuntu installed, but when I get to the desktop the same graphical distortions come back (hard to explain. I can see mostly brown (the desktop I'm sure) with the task bar on the bottom (or at least a solid color stripe on the bottom of the screen that resembles the task bar) and everything that appears on the screen other than vague shapes and colors, like text and I am assuming the log in box as well as mouse cursor, are squished vertically, stretched horisontally and there are multi-colored "scan lines" running through everything. I tried using the recovery console to run the command:

```
sudo dpkg-reconfigure xserver-xorg
```

It went through it's thing and so I entered "startx" and it came back saying that no device was detected!

So I figure that maybe X doesn't work in this mode and go back to the normal boot and, while I no longer have the SAME distortions, I now I have the black Ubuntu loading screen with a green dotted line running down the center with red dotted lines appearing every few minutes just above or below the green line.

I don't know what the heck I need to do to get it running. I am guessing I am to install the drivers for my video card, but I can't do that without seeing what's going on it seems. I have nothing set up that I could do most of the possible solutions I have found blindly (that is, if everything is working fine behind the googly eyes I am seeing the situation from) because they require me to have internet access for apt-getting stuff, but since I haven't even set-up my wireless connection yet (and don't know how or if I can from the command line)... 

I am pulling my hair out trying to fix this, but I am pretty much on noob on Linux so I can't do it alone.

SPEC TIME:

CPU: Intel Pentium D 975 Dual Core (3.4GHz)
MOBO: Abit IP-95
GPU: HIS ATI Radeon x1650 XT
RAM: 1536MB DDR400
HDD: 2x 250GB SATA1.5 Seagate Barracudas

---

### Post by n3cr0fil3 on 2007-02-15
bump

---

### Post by n3cr0fil3 on 2007-02-15
bump 2: electric boogaloo

---

