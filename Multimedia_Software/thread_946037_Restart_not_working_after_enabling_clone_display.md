---
title: "Restart not working after enabling clone display"
date: 2008-10-12
forum: Multimedia Software
---

### Post by blastfm on 2008-10-12
I've enabled cloning of my video so I can see the same display on 2 monitors. This worked, but I noticed after that re-start no longer works. Whenever I choose "Restart" the system would shutdown normal, then freeze right before it starts again (power and HDD LED are on, blank display on the monitor). 

My video card is an on-board Nvidia 6150 with VGA and DVI output and I used the NVIDIA X Server Settings (/usr/bin/nvidia-settings) tool to get clone to work and modify the xorg.conf.

This is getting to be a pain especially when updates come in requiring a re-start. System would shutdown successfuly but when the re-start begins, it just freezes. I have to power down my PC and power it up again.

---

### Post by cariboo on 2008-10-13
Just out of curiosity if you type in a terminal:

```
sudo shutdown -R now
```

Does the computer restart?

Jim

---

### Post by blastfm on 2008-10-13
Carboo907, thanks for the quick reply.

Unfortunately no. Shutdown completes but right befor the system starts up again, it just halts. Pressing the hard reset button doesn't do anything either. 

I have to hold the power button several seconds for a hard shutdown and press it again to re-start.

---

### Post by blastfm on 2008-10-19
Anybody? Seems odd I'm the only one experiencing this?

I'm pretty sure it's not the hardware since I have a dual-boot with XP and displaying in both monitor and restart works fine on this other OS.

---

