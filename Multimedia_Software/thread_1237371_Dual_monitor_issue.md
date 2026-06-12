---
title: "Dual monitor issue"
date: 2009-08-11
forum: Multimedia Software
---

### Post by bracc0 on 2009-08-11
Hello,
I have a strange issue with my laptop, a FUJITSU-SIEMENS Lifebook C1410.

When I work from office I place the laptop in its docking station with a Wide-screen monitor (1680x1050 capable).

When I change something in "Configure the display settings" I see a pop-up that ask to close the session and restart it. The problem is that closing and restarting the session doesn't help: my modification is not registered. I tried to reboot after the modification: nothing changes.

My graphic card (onboard)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

My xorg.conf:

...
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


Thanks to anyone that can help
Claudio

---

### Post by eldragon on 2009-08-11
do you have compiz enabled?

are you trying to set them one screen next to the other one?

if both of these are true, your hardware does not support texture sizes bigger than 2048x2048, try stacking them one display on top of the other one (adjust your virtual size settings in xorg.conf), you could also disable compiz.

---

### Post by babujbf on 2009-08-11
what brand is your integrated video card? for me I have to run sudo nvidia-settings and I have no problems.

---

### Post by bracc0 on 2009-08-11
eldragon,
thank you for having answered so quickly.

> **eldragon said:**
> do you have compiz enabled?

ehm, I don't know! How can I check if compiz is enabled?

> **eldragon said:**
> are you trying to set them one screen next to the other one?

Bingo! This is exactly my last try. I had no idea how to describe this in a decent english. You made this task for me, thanks for the english lesson :-)

> **eldragon said:**
> if both of these are true, your hardware does not support texture sizes bigger than 2048x2048, 

I forgot to mention that I have a partition with windows XP (the company sadly force me to use it), and with this primitive operating system I can put the screen one next to the other. So I guess the hardware can support thw wide screen (1680x1050) next to the laptop display (1280x800).
Does this reasonment make sense?

> **eldragon said:**
> try stacking them one display on top of the other one (adjust your virtual size settings in xorg.conf), you could also disable compiz.

The two screen one on top of the other work fine.
Can you kindly suggest how I could edit the xorg.conf? Which value I should put in replacement of "Virtual	2960 1050", assuming you meant to modify this?

Thanks again for your help
Claudio

---

### Post by bracc0 on 2009-08-11
> **babujbf said:**
> what brand is your integrated video card?

This is the whole description of my graphic card from "lspci -v":

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Fujitsu Limited. Device 1381
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

Thanks for the answer
Claudio

---

### Post by eldragon on 2009-08-11
> **bracc0 said:**
> eldragon,
thank you for having answered so quickly.



ehm, I don't know! How can I check if compiz is enabled?



Bingo! This is exactly my last try. I had no idea how to describe this in a decent english. You made this task for me, thanks for the english lesson :-)



I forgot to mention that I have a partition with windows XP (the company sadly force me to use it), and with this primitive operating system I can put the screen one next to the other. So I guess the hardware can support thw wide screen (1680x1050) next to the laptop display (1280x800).
Does this reasonment make sense?



The two screen one on top of the other work fine.
Can you kindly suggest how I could edit the xorg.conf? Which value I should put in replacement of "Virtual	2960 1050", assuming you meant to modify this?

Thanks again for your help
Claudio

well, it appears you have compiz enabled.

go to system / preferences / appearance and disable any hardware acceleration (i dont have ubuntu around here so i cant point you directly to the option). after doing that, try setting your dispaly to your liking.

the reason windowsxp can place them one next to the other is because winxp does not texturize your desktop. compiz does that in order to pull the 3d magic on it (basic install of compiz is hardly noticeable, and it does not do much of that, yet it makes a texture out of the entire desktop ;)). 

tbh, ive got the same problem you have, ive stacked the screens instead of disabling compiz, and taught myself to go down in order to move to the laptop screen. but each to its own and you might find disabling compiz better.

EDIT

about editing xorg, yes i meant that line. but since you managed to stack the displays succesfully, i guess there is no point in editing it. but those numbers relate to the added squared framebuffer size of both screens, you dont need to edit it unless the display settings helper complains about framebuffer size. EOEDIT

---

### Post by bracc0 on 2009-08-11
> **eldragon said:**
> well, it appears you have compiz enabled.

go to system / preferences / appearance and disable any hardware acceleration (i dont have ubuntu around here so i cant point you directly to the option). after doing that, try setting your dispaly to your liking.

the reason windowsxp can place them one next to the other is because winxp does not texturize your desktop. compiz does that in order to pull the 3d magic on it (basic install of compiz is hardly noticeable, and it does not do much of that, yet it makes a texture out of the entire desktop ;)). 

tbh, ive got the same problem you have, ive stacked the screens instead of disabling compiz, and taught myself to go down in order to move to the laptop screen. but each to its own and you might find disabling compiz better.

EDIT

about editing xorg, yes i meant that line. but since you managed to stack the displays succesfully, i guess there is no point in editing it. but those numbers relate to the added squared framebuffer size of both screens, you dont need to edit it unless the display settings helper complains about framebuffer size. EOEDIT

eldragon,
thanks for your time.
Compiz appears to be already disabled.
"System-->preferences-->Appearance-->Visual Effects" is set to "none"

Following your advice I definitely won't bet with xorg.conf editing (yes, I know I can safely do a backup copy but reboots/gdm restarts take time and I'm so lazy...).

By the way, after a little practice is not so unconfortable to scroll down with the mouse instead of scroll right :-)

Thank you
Claudio

---

