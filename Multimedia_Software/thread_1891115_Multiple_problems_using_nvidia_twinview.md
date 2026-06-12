---
title: "Multiple problems using nvidia twinview"
date: 2011-12-04
forum: Multimedia Software
---

### Post by yorgmeister on 2011-12-04
System: 
asus m3n ht deluxe
amd Phenom 9600
Nvidia 9600 GT HDMI
Acer 2223W Monitor
Samsung 50" 3D HDMI
Ubuntu 11.04

I want to watch movies from my computer to my tv through my hdmi cable.

Problem 1:
When I select twinview and on all auto settings, and select apply the screen goes momentarily black then comes back to my desktop, twinview does not work. If i wait for 10 seconds and try again, the screens on both the tv and the monitor get all messed up for about 5 seconds and then the countdown timer appears on my tv and I click ok to keep the settings. My gnome panel disappears and the keyboard is disabled, but the mouse still works. I cant get anything to work. I have to hit the reset on my tower.

Problem 2:
Several times I have got twinview to start, and not kill gnome. the right side of my desktop on my monitor dissappears. Have to guess where scroll bar or restart button are. All dialogue windows will appear on my tv and not on my monotor where i'm working, It gets annoying always turning around and moving the mouse over to the second desktop, to drag the windows back to my monitor.

Problem 3: Hdmi sound is very sketchy sometimes it works but most of the time it will not. I quit onece in the middle of a movie and would not work again, another time it stopped when I finished watching one video and started watching another. Re-booting sometimes fixes it but mostly it will not.

I have been googeling and searching for a solution, typing in lengthy code and re-configuring nvidia server toll i'm blue in the face. I'm at my wits end I don't want to give up on UBUNTU but this problem has been plaguing me for 2 years and several versions of ubuntu.

Please anyone with some helpful info please help me!!

Thanks, George

---

### Post by inobe on 2011-12-04
the driver is the problem, unfortunately ubuntu can't fix it, because it's proprietary.

but of course you can try another driver?

the chances of getting better results are greater.

if your using the newest driver from additional drivers, there is a chance a newer version is available either from nvidia's site which will be the hard way to install it, or you can go the easy way and use a repository to get it updated.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

be sure to use the repository/ ppa correctly!

use the filter to get the correct ppa..

---

### Post by BicyclerBoy on 2011-12-05
Look in the log files...

/var/log/Xorg.0.log
dmesg

Note that nVidia 9600 does not have real HDA HDMI audio..it supports S/PDIF iec958 pass-thru' via internal link cable from mobo sound..
All the audio config is the same as std non-HDMI setup..
ELD is not supported.

I not sure if the video driver gets involved at all..

The lack of ELD means you have to find the limitations of your audio system.

Personally find twinview inappropriate for full screen video.

---

### Post by yorgmeister on 2011-12-06
What am I looking for in the /var/log/Xorg.0.log file, BicyclerBoy? What other way is there to view full screen movies other than twinview? Keep in mind I still like to have my monitor at the desk for work.

I tried to use the repository, and did a update like you suggested, inobe, but the install failed.

Thank you both for your responses I really appreciate your help, I will keep trying to update my nvidia driver.

---

### Post by inobe on 2011-12-06
> **yorgmeister said:**
> 
I tried to use the repository, and did a update like you suggested, inobe, but the install failed.


please be more specific, include all that happened, thanks

simply adding the ppa and checking for updates in terminal like this..

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

read the list, you should see nvidia as one of the listed updates, type **y** then hit enter, when updates are complete, restart.

---

### Post by yorgmeister on 2011-12-06
That's exactly what I did, but I got a list of errors 2 pages long and it said installation failed. I re-started it and x would not start, just a flashing cursor in the corner, luckily i have 2 separate installations on 2 different hard drives. Sorry can't remember the details and can't find the log file.

---

### Post by yorgmeister on 2011-12-06
I guess my problems were a little more serious then i thought. I've only had oneric oscelot installed for 4 weeks. Hmmmm....

---

### Post by yorgmeister on 2011-12-10
I.ve given up on twinview, it has caused me enough grief. now i just unplug my tv and restart. 
But I still have a problem with the s/pdif sound.

After re-installing oneric ocelot. and updating my drivers as inobe suggested above, my first movie played sound perfectly. But after re-starting and changing my sound back to the computer. I can not get sound out to my tv again. I change my hardware profile back to digital stereo duplex (IEC958) (that worked the first time). No sound. I have not changed a thing since the first movie played. I have opened alsamixer and made sure nothing was muted.

thanks for looking

---

### Post by BicyclerBoy on 2011-12-11
Try separate X screens..it is better for full screen video.

Explain what you mean by change the sound back to the computer..
Does this mean back to analogue output to desktop speakers ?
From S/PDIF iec958 ?

Your mobo has onboard chipset graphics (nVidia) & HDMI output jack,
The onboard HDMI would be a better audio link because it is HDA & supports ELD handshaking etc..
Getting an audio only link working may be fun. Do you have an AVR HT amp or just TV ?

That mobo chipset has (has had) problems with msi enabled interrupts.
You may need grub cmd line option: pci=nomsi.
This problem causes unreliable/missing audio etc..

Do you have a internal link cable from mobo s/pdif header to video card (2 or 3 wires) ?

---

### Post by yorgmeister on 2011-12-11
Yes I mean switching back from iec958, to analog 5.1 computer speakers. And yes i have my 2 wire s/pdif connected to my video card. You think my onboard video would be comparable in quality to my video card?

---

### Post by BicyclerBoy on 2011-12-12
Your on-board chipset GPU is VDPAU feature set B1. Your 9600GT is feature set A & has much higher opengl performance.

So yes your on-board has better video decode capability.
Both don't compare to GT430/440.

Your mobo was a popular HTPC mobo because the chipset graphics & HDMI audio was way ahead of other solutions. This chipset audio does not support ELD reporting.

The nVidia chipset mobos have problems with message signalled interrupts (msi). This is meant to be auto-handled but ..
Check kernel logs or dmesg etc, to see if your computer boots with nomsi..

A symptom of msi (nVidia chipset) is unreliable audio..

---

