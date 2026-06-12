---
title: "S-video output in black and white on TV screen"
date: 2008-05-25
forum: Multimedia Software
---

### Post by stefanos1990 on 2008-05-25
Hi all,

I have a problem which I've trying to solve now for a couple of days: getting my laptop to output video to my tv.

I have a TV which has a s-video input, and an Ati card with s-video output. I have the fglrx driver installed. In windows all works fine, but on Ubuntu I get a black and white image.

How can I fix this?

After that's fixed, I want to output a composite signal via s-video, so that my scart TV can also display my Ubuntu desktop in full color. Now it works, but also in black and white, but via scart is in black and white on Windows also.

Any help? Thanks!

---

### Post by 505 on 2008-05-25
I had the same problem as you, and only in Ubuntu I could get a TV out with scart in colour. For some reasons Windows can't do that. Hoever, I have a Nvidia card so things might be a bit different for you.

Since you have a laptop, check the BIOS of you laptop first and make sure the output format is correct (PAL or NTSC). If that is OK, in Ubuntu you need to edit the file /etc/X11/xorg.conf On every system the file will look different, but if you have a monitor and a TV both should be listed in the file. The "device" section controls how to output the signal to the TV. Mine looks like this:
```

Section "Device"
	Identifier	"TV Out"
	Boardname	"nvidia"
	BusID          "PCI:1:0:0"    
	Option         "TVOutFormat" "COMPOSITE" #COMPOSITE or SVIDEO etc
	Option         "TVStandard" "PAL-G" #or NTSC etc
	Option         "ConnectedMonitor" "TV"
	Driver		"nvidia"
	Screen	1
EndSection

```
PLay a little with the options there and read some guides on you to configure dual screen setups with xorg.

---

### Post by john methew on 2008-11-29
Buddy you can simple install Nvidia drivers in your system. First go to System > Administration > Hardware Drivers:

You'll then see that Nvidia drivers are not in use. Check (or tick) the box underneath Enabled to enable the drivers. 

You'll then be asked (after a brief explanation about desktop effects) if you want to enable the driver. Click Enable Driver.

Wait for the installer file to download.

Wait for the drivers to be installed. 

Then, click Close once the changes have been applied.

You'll then see that the drivers are enabled and will be available for use upon a reboot.

---

### Post by stefanos1990 on 2008-11-29
> **john methew said:**
> Buddy you can simple install Nvidia drivers in your system. First go to System > Administration > Hardware Drivers:

You'll then see that Nvidia drivers are not in use. Check (or tick) the box underneath Enabled to enable the drivers. 

You'll then be asked (after a brief explanation about desktop effects) if you want to enable the driver. Click Enable Driver.

Wait for the installer file to download.

Wait for the drivers to be installed. 

Then, click Close once the changes have been applied.

You'll then see that the drivers are enabled and will be available for use upon a reboot.

uhm, thanks for your help, but at the time I asked the question I had an Ati graphics card.

---

### Post by ugm6hr on 2009-03-17
I have found that different S-Video cables show pictures in B&W or colour; I have never tried in Windows and Ubuntu with the same computer and same cable though.

In total, I have bought 4 cables, and had differing success with them; 1 that worked  on one Gentoo laptop gave B&W with a different Ubuntu laptop, while the other 3 all worked in colour for all 3.  I never really understood why.

---

### Post by bukueOner on 2009-09-01
yea the same thing happens to me. cant wait for an answer.

---

### Post by galuzyaki on 2010-04-26
had the same results in windows :(

---

### Post by greenchilli on 2010-12-02
I've tried the following (changing physical cable -forget the Greek, just look at the picture)
[http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=2402](http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=2402)

Maybe I did not do it correctly - I used incorrect copper wire.

Speaking to another guy at work it ends up being two ways to resolve this. Get something to convert the s-video to composite signal (almost like patching the cable in above link) OR 
The other way is to configure the driver on the s-video output to push out composite signal. I have not figured that out yet - I'm running 10.04 on a Dell E5400 (Intel chipset) and everything works well. Getting rid of the black and white might require a bit more work than what I thought - Have not tried on Windows - I don't own a copy of it :-)

Seeing that I'm not using /etc/X11/xorg.conf, I might have to use xrandr instead.

Some forums suggested changing the config from NTSC to PAL, but that did not work - I mean - I could not get the xrandr config to accept the value. Maybe you can try this:

xrandr --output TV1 --set TV_FORMAT PAL; xrandr --output TV1 --mode 1024x768

---

