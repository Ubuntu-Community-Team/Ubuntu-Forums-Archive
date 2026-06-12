---
title: "ATI Radeon Xpress 200M Graphic driver"
date: 2009-01-11
forum: Multimedia Software
---

### Post by hemajith on 2009-01-11
My Toshiba laptop has ATI Radeon Xpress 200M graphics. When I installed Hardy Heron, it worked through a default driver but never gave me the full performance. Full screen video images were not sharp.

Can anyone tell me how to install the drivers for this in Intrepid Ibex? I need to be able to play back video files very clearly.

---

### Post by mikewhatever on 2009-01-11
System -> Admin -> Hardware Drivers.

---

### Post by hemajith on 2009-01-12
I do not have the Xpress 200M driver. Can you tell me where to download it OR whether Interpid Ibex supports it?

---

### Post by mikewhatever on 2009-01-12
> **hemajith said:**
> I do not have the Xpress 200M driver. Can you tell me where to download it OR whether Interpid Ibex supports it?

How do you know you don't have it? Your card should be supported by the driver from the restricted section. In short, make sure you have the xorg-driver-fglrx package installed.

---

### Post by mc4man on 2009-01-12
We have a laptop here with that card. Drivers were available in system -> admin -> hardware drivers -> ati/amd ....

> doug@doug-laptop:~$ sudo lshw -C display
[sudo] password for doug: 
  *-display               
       description: VGA compatible controller
       product: Radeon XPRESS 200M 5955 (PCIE)
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
doug@doug-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes




---

### Post by hemajith on 2009-01-21
I managed to install the fglrx diver. And everything seems to work fine, EXCEPT when I play video in full screen mode, the video play back seem to play in a slow frame rate per second... kind of like when you are playing back a video without the proper VGA drivers!
This happens only in full screen mode. I played avi files in VLC player, in the smaller default screen its very sharp and plays well, but as soon as it's on full screen, the video tends to run slow. Can you help me with this?

---

### Post by jmhkk on 2010-02-14
I've finally lobotomized my old laptop and installed ubuntu 9.10 and I love it... except for a few problems:
 
I've been reading up on the ATI/AMD Radeon Xpress 200M and it looks like a LOT of people are having problems with it.
I've been installing all kinds of upgrades and tried running scripts to no avail.
My trouble seems to be the System -> Admin -> Hardware Drivers doesn't show any ATI drivers. On the plus side, quite a few Radeon drivers apear in the Synaptic Package Manager.

Platform: 
Compaq Presario V2000 with AMD Turion64 1.8MHz with ATI/AMD Radeon Xpress 200M Video card (Yes, it's dated, but still worked with Windows and I wanted to use this to play around instead of my new work laptop)

Symptoms:
- Glitchy and choppy display during movies and when I max a streamed video and I put it full screen.
- Cannot activate the S video port to show movies on the TV
- When I try to run "System -> Preferences -> Monitor Settings" I get a message indicating:
-------------------------------
No monitor supporting DDC/CI available.

If your graphics card need it, please check all the
required kernel modules are loaded (i2c-dev, and your 
framebuffer driver)
-------------------------------

I've loaded all the i2c related packages and none indicate "i2c-dev"

I've also installed the atitvout package from synaptic that doesn't do anything.

Before I remove all the files I've transfered to the laptop and re-install Ubuntu 9.10, does anyone have any suggestions or explanations?

Thanks

---

### Post by jmhkk on 2010-02-15
Update:
I've purged the "Monitor Settings" app, I've read up on it and it won't work anyway.
I ran EnvyNR and now my graphics driver is not configured at all and nothing I've done could get it back, so I'm transfering al my files back onto my network backup drive and I'll try to install Ubuntu as a secondary OS. It's sad, but I've got no other option at this point but to *gulp* re-install Windows XP. I'Ll then re-install Ubuntu 9.10.

If anyone has any insight for me, please don't be shy.

---

### Post by benmoran on 2010-02-15
I've got a similar card (Xpress 1150), and to be honest the Catalyst drivers for Linux always sucked. The latest Catalyst to support our cards was 9.3, which I believe was last supported in 8.10. 

These days i'm running Karmic with the latest open source ATI drivers from the Xorg-Edgers PPA, and my video card is working better than it ever was. Even 720p stuff plays fine. Haven't tried 1080i/p. 

I'd give Karmic a try. For most folks, the open source drivers are better than the proprietary ones in every aspect besides raw 3D and power management (being worked on now).


Edit: I see you're already running Karmic. Did you try the Xorg-Edgers PPA?

---

### Post by jmhkk on 2010-02-15
Thank you Benmoran for your support.
I've scrapped Karmic and I've installed Hardy Heron (Ubuntu 8.04) that I'd downloaded over a year ago and had decided to wait to install.
The driver for ATI seems to be working now, but I'm still not able to activate an S-Video.
It seems my motherboard-integrated ATI Radeon Xpress 200M is not fully supported on Karmic so I'm still checking a few things out... but I'm not sure about this statement since I could get a somewhat clear and working image on my monitor.
Persistence is required when venturing unknown territory. Fortunately, one can always restart when it's about a computer system.
I'm not sure if I tried Xorg-Edgers PPA, I tried everything I could get my hands on and eventually the whole thing crashed.
My next step will be to use the 8.10, as you mentioned, since it had the supported drivers with Cathalyst 9.3

Is your Xpress 1150 an motherboard-integrated device or a seperate device?


edit: I've tried to get things moving with 8.04, but now my wireless card doesn't want to connect to my network. I'll be trying 8.10 tomorrow.

---

