---
title: "Video performance drop in Ludic Lynx"
date: 2010-05-03
forum: Multimedia Software
---

### Post by angry_norwegian on 2010-05-03
I was quite happy with the lucid upgrade from karmic, until I tried watching videos. They play normally in windowed mode, but in fullscreen it starts to jitter and lag with fps around 1 or even lower.

This happens on all video formats in any program I've tried. Youtube, Vimeo, VLC playing local files in different formats, you name it, I can't play it.
Also, it happened on two quite different computers too: One is a five year old stationary Pentium4 3.0 GHz with Ati HD2400 gfx, the other's a 6 month old Intel Core 2 Duo laptop with a GeForce G 105M.

Downgrading to 9.10 solved the problem, but 9.10 has other problems I'd like to get rid of.
I've googled my eyes out without finding a relevant hit.

So is there some way I can identify the problem with videos in 10.04, and resolve them? I'd be happy to provide more information if that helps.

---

### Post by tgalati4 on 2010-05-03
Lucid has a PAE-enabled kernel so the 32-bit version can see more RAM.  This might affect RAM handling speed.  Watching fullscreen videos can be RAM intensive.

I presume that you are running 32-bit on your machines.

What were the problems in Karmic?

---

### Post by angry_norwegian on 2010-05-03
Yes, I'm on 32-bit machines.

Can I disable PAE?

The problems in Karmic is that side-scrolling isn't working on my thinkpad, that window buttons in gnome-panel sometimes becomes unresponsive, and that for some reason indicator-applet lost its shutdown/sleep/hibernate options. Plus some other few quirks I've forgotten.

---

### Post by tgalati4 on 2010-05-03
I don't think there is a simple switch to turn off PAE.  You need to recompile the kernel without PAE.  I'm just guessing.  I have Jaunty on my thinkpad t43p.  I've decided to wait until others get beat up by Lucid.

And they have.

What is side scrolling?  My edge scrolling works.  My two-finger scrolling works.  You can simply add the on/off button to the panel:  right-click on a blank spot on the panel and "Add to Panel".  Unresponsive window buttons could be lack of RAM on a slower machine.  There are some tweaks to improve it, but you really need to max out RAM first.

---

### Post by angry_norwegian on 2010-05-05
Side scrolling is using trackpoint + middle button to scroll horizontally. gpointing-device-setting gives me vertscroll.

I tried running with the 9.10-kernel on the server, but it still was quite laggy. Installing xubuntu 9.10 gave me the same performance I used to have, so I'll stick with that.

On my laptop I'll try xubuntu 10.04, too see if it's the kernel or desktop that bogs down video.

---

### Post by Amael on 2010-05-09
Hello, 

same problem here : since I installed the new Lucid Lynx I have noticed a video performance drop when I'm playing fullscreen videos (VLC, totem, ...).
I have an Ati video chipset :

```
amael@amserv:~$ cat /var/log/Xorg.0.log | grep Chipset
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200 5974 (PCIE)" (ChipID = 0x5974)
amael@amserv:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200] [1002:5974]
amael@amserv:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: DRI R300 Project
amael@amserv:~$ 

```


Edit : Just found the solution !

I installed the ATI fglrx driver using command-line (not proposed in the proprietary hardware drivers), and now my problem is solved !
```

sudo apt-get install fglrx

```

Hope this will help you too.

---

### Post by Amael on 2010-05-11
Bad news... the fglrx driver made my graphics work faster, but I had some minor graphic bugs and the system was in an unstable state. Trying to run glxgears made it crash with a segmentation fault, as for glxinfo.

I found a bug on launchpad explaining that I was probably using parts of the fglrx driver and parts of the open source radeon driver, and that these were incompatible.

I'm now trying to find a stable solution...

---

### Post by denied on 2010-05-11
Just a tip, did you try the PPM in this bug report ?

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

It did wonders for me (still havent solved my issue 100% but at least its very workable now).

---

