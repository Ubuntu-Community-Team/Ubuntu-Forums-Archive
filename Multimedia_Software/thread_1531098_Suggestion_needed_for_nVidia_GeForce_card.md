---
title: "Suggestion needed for nVidia GeForce card"
date: 2010-07-14
forum: Multimedia Software
---

### Post by shreepads on 2010-07-14
Hi folks

Am feeling the need for some extra grunt on my home desktop in the graphics area, especially for games (Need for Speed etc). The on-motherboard Intel GMA 3100 is good enough for most times, except when the car splashes thru a puddle in NFS :-) or when I move to full res and detail

Current System Spec:
a. Ubuntu 8.04 Kernel Linux 2.6.24-28 generic
   - Occasional Win XP dual boot
b. Intel DG33FB motherboard
   - Intel G33 Express Chipset
   - Intel GMA 3100 onboard graphics card
   - One PCI Express x16 connector (PCI Express v1.1)
c. Intel C2D E7200 @ 2.53Ghz
d. 2 GB RAM
e. 2 x 3 Gbps SATA drives
f. LG Flatron Wide 19" LCD monitor with DVI-D sockets

I believe I should also specify my power supply specs but they are pretty well hidden away inside the cabinet for now!

Requirements
- nVidia GeForce based card
- Works with very little tweaks in 8.04 and hopefully none in 10.4 (especially Wine)
- Willing to live with low res and detail in very demanding games like Crysis
- Mid-prices, as you can see from the rest of the specs, aiming to get the most bang per buck
- PCI Express v1.1 only support is acceptable, motherboard doesn't support 2.0 and not planning to upgrade any time soon
- Ideally one that is easily available in India, but pls don't hold back if you are not familiar with whats easily available here

One last question, existing power supply is one of those no-brand ones. Would it be better to also upgrade that as a part of the install?

Thanks!

---

### Post by ratcheer on 2010-07-14
In the US, I bought a Sparkle brand nVidia 9400GT card for $40 via Amazon.com. It is working just fine with my PCI-x 1.1 motherboard, even though it is a 2.0 card. It worked just fine with Karmic and now it is working with Lucid and Maverick. With the nVidia proprietary driver, it has good speed and 3D effects.

Tim

---

### Post by shreepads on 2010-07-16
Thanks Ratcheer!

Put in some more research and upped the budget a bit so looking at the following two options, both in pretty much the same price range (Rs 6K - 7K)

- Zotac: 9800 GT: 1GB
- Galaxy: GT 240: 1GB

Reading thru the newegg reviews and comparing to my existing kit it looks like both would work, except that the 9800 GT would run hotter and require more power. Also it is slimmer while the galaxy one is thicker but requires less power.

So still a bit confused.

Also everywhere I look at the entry level the ATI Radeon cards are always mentioned as being more capable at the same price point e.g. Radeon HD 5670. But what's the Ubuntu compatibility for the ATI cards in 8.04 and 10.04?

---

### Post by shreepads on 2010-07-16
Sorry one more question... My LCD Monitor comes with a single-link DVI-D cable, but all the current graphics cards have a dual-link DVI-D socket.

I guess I can still fit the single-link cable to the socket on the graphics card (as the card has the female socket) but will it work? Or do I need to start looking for a dual-single adapter.

---

### Post by shreepads on 2010-07-19
After reading several posts on the topic am convinced that nVidia is the way to go for Ubuntu due to better support nVidia and issues with setting up Radeon 5xxx series in Ubuntu.

However this is a little irrelevant now as I have discovered that the stock PSU in the cabinet (rated at 450W) has a 14A 12V rail, while even the lower powered GT 240 requires a minimum 18A 12V rail.

A decent power supply in the 500-600W range is another 4.5K taking the total hit to approx 11K.

I think I'd rather spend the cash on upgrading my current UPS which is now no longer able to deal with power cuts.. And I had 6 such power cuts yesterday.. Very tiresome...

So I'll mark this as closed for now... Final choice is to go for a GT 240 card (1GB, DDR3) due to lower power reqmts.

---

### Post by shreepads on 2010-07-23
OK so I've stretched the budget a bit more and got

UPS - APC 650VA: Rs 3.5K
PSU - Corsair CW 400w: Rs 3K
Graphics Card - Palit GT 240 1GB DDR5 Sonic: Rs 6K

So a total spend of Rs 12.5K, a bit expensive!!

UPS installed, will do PSU tomorrow and graphics card a bit later. Lets see...

---

### Post by efflandt on 2010-07-23
Someone had recommended GT220 or GT240 for Linux, so I bought a new PC with i5 cpu and GT220.  I don't know how much power it actually needs or rail spec's on the 375 watt OEM psu on my Dell.  But my entire PC only uses 50 watts at the wall outlet idling and peaks at 100 watts (1/3rd less than my old Athlon64 3200+ single cpu w/slower legacy ATI X1300 AGP video).

I don't really know what to use for a benchmark, but alien-arena was more a matter of seconds per frame, instead of frames per second, with the old X1300, and it is smooth with the GT220 and nVidia(195) driver.  But I don't know how to play it yet because it has been a long time since I played Quake or Doom and I forgot the movement commands.  FarCry2 in Win7 plays well 1080p at high graphics (haven't tried 2 higher graphics qualities yet).  I have just been using DVI to HDMI cable because I have separate speaker system anyway and have not figured HDMI sound in Linux (which I heard needs newer alsa).

You do not really need dual channel DVI unless you have a monitor with resolution somewhere beyond 1080p, depending upon resolution and frequency (single channel can handle 1600x1200 @ 60 Hz).

---

### Post by shreepads on 2010-07-31
Re efflandt
- Yes power requirements are quite minimal for these cards but hard to get a good quality power supply at lower wattage
- Re single/ dual DVI am not so worried as the Palit card has an old monitor port as well

Well I got the damned thing installed in the PC, ran first in dual-boot Win XP and was working perfectly there so no hardware issues.

Then I booted up Ubuntu Hardy 8.04 and the login screen came up but with very low res (800 x 600). Could not change the resolution from Screen Settings so decided to go for the proprietary drivers.

Went to System > Admin > Hardware Drivers and couldn't find a damn thing listed.

Saw that the default nVidia proprietary drivers in the repository (v169.12) don't support GT 240 so instead decided to go with envy.

Install envyng-core and ran envyng.

- First tried to let the system pick the right driver for the card but it gave up with an error: " Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk."

- So I tried the manual install and was prompted with these choices:
" 1 - 173.14.12 (latest)
                2 - 96.43.05 (new legacy)
                3 - 71.86.04 (legacy)
"

- I chose 173.14.12 even though the list at the link below doesn't list my card
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html)

- Ran thru with the installation and reboot. On restarting the system seemed to try a few times to get it working but gave it up and presented an error message stating that it could not get the card to work and was going to start in a low res mode.. This is where I'm typing from now!!

Any suggestions, apart from moving to 10.04? I don't want to do that till 10.04.1 is out...

---

### Post by shreepads on 2010-07-31
Sorry forgot to add, output from lspci:

> sudo lspci -vvnn | grep -i nvidia
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0ca3] (rev a2) (prog-if 00 [VGA controller])
01:00.1 Audio device [0403]: nVidia Corporation Unknown device [10de:0be4] (rev a1)

---

### Post by shreepads on 2010-07-31
Just to try it out put in the 10.4 LiveCD and booted. Came up perfectly with full res (1440 x 900). Also prompted me to install the nVidia proprietary drivers, which I did and the same went thru smoothly.

Then to give them a push I tried to enable desktop effects from System > Preferences > Appearance > Visual Effects. Tried both Normal and Extra settings but both came back with a "Desktop effects could not be enabled" error.

So what's the cussing point of getting a graphics card on Ubuntu I wonder...

---

### Post by shreepads on 2010-08-04
Got it working fully, details here:
[http://ubuntuforums.org/showthread.php?t=1544086](http://ubuntuforums.org/showthread.php?t=1544086)

---

