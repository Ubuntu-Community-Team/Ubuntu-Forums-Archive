---
title: "7600 GS &amp; 32 Bit Depth"
date: 2009-04-24
forum: Multimedia Software
---

### Post by drs305 on 2009-04-24
I recently started noticing 32 bit depth advisories when opening certain apps. They could have always been there and I didn't notice, the drivers may have changed capabilities, or perhaps newer apps are asking for 32 bit depth that didn't previously.

One of the first places I noticed it was when opening VirtualBox, which said I should run in 32 bit depth if possible. I don't remember seeing that when I first started using VBox.

I have an nvidia GeForce 7600 GS running the nvidia 180-44 driver from the ubuntu packages. 

I tried manually changing 24 to 32 in xorg but that didn't work and I couldn't get a 32 bit option when trying to change it via nvidia-settings and nvidia-xconfig.
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Can this card just not run higher than a depth of 24 on ubuntu?

Thanks for any inputs.

---

### Post by drs305 on 2009-04-26
This is an update to the original post. I've done even more searching.

I found information indicating nvidia in linux designates 24 bit and won't use "32 bit" since this is a "more honest" representation of the true abilities of color representation - even though it has essentially 32 bit depth abilities.

So my real question becomes, if I can't get xorg and nvidia to designate 32 bit depth, how can I run apps that require 32 bit depth and give me errors when I try to run them. A bit less problematic is that VirtualBox also gives me messages saying that I should be running 32 bit depth (of course, I can elect to remove the notification should I choose).

---

