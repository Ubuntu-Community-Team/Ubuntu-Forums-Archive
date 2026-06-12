---
title: "Flickering video"
date: 2009-08-17
forum: Multimedia Software
---

### Post by robyngran on 2009-08-17
A friend installed Xubuntu 9.04 on a HP Pavilion 7940 (chipset Intel 810E) w/HP L1706 monitor. I'm noticing some video flickering and slow jerky video playback from Youtube. I'm using the onboard video.

I have a nvidia FX5200 video card. Would that be better? 

How can I correct this problem?

---

### Post by RedSingularity on 2009-08-17
Did your friend get the drivers for the chip?

And yes, usually Nvidia chips work much better with linux than ATI and Intel.

---

### Post by robyngran on 2009-08-17
> **Shadow121 said:**
> Did your friend get the drivers for the chip?

And yes, usually Nvidia chips work much better with linux than ATI and Intel.

How do I get the drivers for the intel video? If I go with the nvidia FX 5200 card, does Xubuntu find the drivers for that one or do I need to go synaptic and get that driver?

---

### Post by RedSingularity on 2009-08-17
Well before giving him your card try this: 

On his computer go to System>Admin>Hardware Drivers.  See if you can activate the intel driver there.  
If there is no option to do that you can install your card and get the drivers the same way as i said above.

---

### Post by robyngran on 2009-08-18
> **Shadow121 said:**
> Well before giving him your card try this: 

On his computer go to System>Admin>Hardware Drivers.  See if you can activate the intel driver there.  
If there is no option to do that you can install your card and get the drivers the same way as i said above.

Can't plug in nvidia fx5200 because its AGP plug and the HP only has pci plugs on the board. Did check hardware drivers  for intel 810 and nothing was listed. Can I get them from the HP site. Or are we stuck with the way it is?

---

### Post by RedSingularity on 2009-08-18
Post the output of your xorg config file

It is located at /etc/X11/xorg.conf

---

### Post by geovino on 2009-08-18
> **Shadow121 said:**
> Post the output of your xorg config file

It is located at /etc/X11/xorg.conf

thanks, I'll check it and send it tomorrow morning.

---

### Post by robyngran on 2009-08-20
> **geovino said:**
> thanks, I'll check it and send it tomorrow morning.

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Let me know what is needed to add. Thanks

---

### Post by RedSingularity on 2009-08-21
In synaptic package manager make sure you have "xserver-xorg-video-intel" installed.  

If it is not, then install it and reboot.  If still nothing add this line to your xorg-config.
------------------------------
Section     "Device"
    Identifier   "Configured Video Device"
**Driver       "intel"  **
EndSection
--------------------------
 and reboot again.

---

### Post by robyngran on 2009-08-21
> **Shadow121 said:**
> In synaptic package manager make sure you have "xserver-xorg-video-intel" installed.  

If it is not, then install it and reboot.  If still nothing add this line to your xorg-config.
------------------------------
Section     "Device"
    Identifier   "Configured Video Device"
**Driver       "intel"  **
EndSection
--------------------------
 and reboot again.

and yes, the xserver-xorg-video-intel  is installed
OK, now its:

Section "Device"
	Identifier	"Configured Video Device"
        Driver       "intel"  

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

But it still flickers... what else is needed? the monitor which is HPL1706

---

### Post by RedSingularity on 2009-08-21
Ok let try this....make a copy of your xorg file.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Once that is done try executing this command to reconfigure xorg.

```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

Then reboot.  If it still doesnt work then you may need to put in the Nvidia card.

---

### Post by robyngran on 2009-08-27
Can't use nvidia card, since this pc has no agp slot. I'm afraind to try the reconfigure of xorg beacause the screen may go black.

I thought I could add some other lines to the xorg.conf file. isn't there an xorg-config command to try out?

---

