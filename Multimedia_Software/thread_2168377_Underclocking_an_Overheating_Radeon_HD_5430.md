---
title: "Underclocking an Overheating Radeon HD 5430"
date: 2013-08-17
forum: Multimedia Software
---

### Post by batbrownbear on 2013-08-17
My current graphics card is a Radeon HD 5430, fanless.  I occasionally run into a problem where the graphics card overheats.  I see it on a graphics intensive game when booted into Windows (just had to drop the graphics quality on the game), but I don't game all that much and don't really see that as a problem.  The main time I see the problem is when using Plex Media Server in Ubuntu and try and stream a video on my tablet using the transcode option.  It just seems to be too much for the card.

I'm wondering, are there ways I can underclock the card to prevent overheating when doing tasks like transcoding/streaming videos from the media server?  I currently am running the current fglrx driver and am running laptop battery mode to try and prevent the overheating (despite being a desktop), but it's not stopping the problem.  I've tried installing the current nvidia driver through Software Center and tried adding coolbits 5 to Xorg.conf to see if I could get some settings to play with, but nvidia-settings never seems to work with that driver installed.  I'm not even sure if there would be a setting worth playing with if the card is fanless.

Just wondering if someone has a method I should try first before bellying up and buying a better card with a fan?  If so what might be a good card?  Known methods to get settings I could play with on the new card to prevent a similar problem?

---

### Post by Petro Dawg on 2013-08-17
It might be a bit of a poor-boy fix, but small PC fans can be obtained pretty inexpensively (a few bucks), you could just screw one directly to the heat-sink.  An ordinary wood screw will typically do the trick.

Like so...

Before

[ATTACH=CONFIG]245444[/ATTACH]


After

[ATTACH=CONFIG]245442[/ATTACH][ATTACH=CONFIG]245443[/ATTACH]

Just be sure to buy a fan of reasonable size with a power cord compatible with an open power adapter in your PC.  I actually used that same fan mounted on my on-board GPU heat-sink in the same manner.

---

### Post by tgalati4 on 2013-08-17
I would go one step further.  I have many a graphics card given to me because of intermittent behavior.  Typically I find the heat paste has worn out.  Remove the heat sink, clean the paste off with a cotton swab and alcohol.  Put new, better quality paste, and then add the fan.

As far as declocking, I know my ATI card has a dynamic clock (one that steps up and down depending on load), but I'm using the open source driver.  Look in /etc/X11/xorg.conf for settings:

Section "Device"
	Identifier	"Configured Video Device"
	Driver "ati"
	Option "DynamicClocks" "on"

I know that lowers the temperatures on my FireGL card by 5 to 7C.

---

### Post by Yellow Pasque on 2013-08-17
>  I've tried installing the current nvidia
But it's not an nvidia GPU...

Those small fans are noisy, so an alternative (assuming your computer case doesn't move) is to use a bigger/quieter 120mm fan and sit it on the bottom of the case.

---

### Post by JDorfler on 2013-08-18
Have you checked your thermal paste and thermal pads on your GPU.  These wear out just as fast, if not faster, as your CPU/APU.

---

