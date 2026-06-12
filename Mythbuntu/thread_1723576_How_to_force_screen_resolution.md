---
title: "How to force screen resolution"
date: 2011-04-07
forum: Mythbuntu
---

### Post by porker on 2011-04-07
Hi,

I just did a complete reinstall of mythbuntu 10.10.  I'm struggling to get the system to run my screen at its nativ resolution ( 1366x768 ).  The graphics card is a GeForce 6200 and the closest i can get is 1366x720 which leaves me with band at the top and bottom of the screen.

I'm certain that my last install (stock ubuntu 9.04 with mythtv) used to let me set the correct resolution so I'm struggling to work out whats changed.  I'm a bit of a newb when it comes to linux so dont even know where to begin if things dont just work :rolleyes:

I'm using a DVI-HDMI lead and the TV is a Phillips 32PF5531D.

Any help greatly appreciated,

Cheers

P

---

### Post by LowSky on 2011-04-07
Did you install the Nvidia drivers?

if yes open a terminal and type

```
gksu nvidia-settings

```
see if you can then set the TV to 768... If no go to GPU 0 - (Geforce 6200) DFP-0
Look for Overscan compensation at the bottom and adjust to fill screen
then go to nvidia-setting Configuration and save the current configuration

---

### Post by porker on 2011-04-07
> **LowSky said:**
> Did you install the Nvidia drivers?

if yes open a terminal and type

```
gksu nvidia-settings

```
see if you can then set the TV to 768... If no go to GPU 0 - (Geforce 6200) DFP-0
Look for Overscan compensation at the bottom and adjust to fill screen
then go to nvidia-setting Configuration and save the current configuration

I'm pretty certain that I've tried the nvidia-settings (although not as root) and couldnt get anywhere.  I'll try again later.

Am i right in saying that xorg.conf contains all the possible resolutions as when i looked in there it was basically empty.  I'll post its contents when i get home if its useful!

Thanks again

P

---

