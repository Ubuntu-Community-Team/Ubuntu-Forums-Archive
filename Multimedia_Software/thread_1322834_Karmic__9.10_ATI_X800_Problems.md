---
title: "Karmic / 9.10 ATI X800 Problems"
date: 2009-11-11
forum: Multimedia Software
---

### Post by mr_muddle on 2009-11-11
I decided to switch my main desktop PC to Ubuntu so I popped in a spare drive and I've done a clean install of 9.10. Super easy install but I'm having trouble getting things how I want them. One of the most important things is the right display settings. Having read through this [http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931) thread I can see that AMD have dropped support for my card in their driver that will work with the latest version of Ubuntu. That's annoying and leaves me with some questions.

Display Preferences GUI:
Ubuntu detects one of my monitors and allows me to select resolutions from 1152x864 - 720x400. I cannot change the refresh rate from 75Hz. My second display is not detected because it uses a VGA->BNC lead I can select resolutions from 1360x768 - 640x480, I cannot change the refresh rate from 60Hz.
Why can't I change the refresh rate for either screen? Is this an Ubuntu 'safety' limitation? Or a driver issue?
I wonder why doesn't Ubuntu use the 'can you still see this?' timeout method?
How can I set them both to display 1280x960 @ 85Hz, as I used to in XP?

Visual Effects:
I can turn on the 'Extra' mode and windows wobble and go boing, it's all good fun - but how can I tell if it's utilising my cards 3D acceleration? or just relying on the CPU?
A couple of times after booting I find the Visual Effects are set back to 'none' for no apparent reason. I'm not really that fussed about the fancy stuff but that it does this does seem a little... odd?

Drivers/xorg/3D/eh?
So I know I can't use AMD's proprietary driver, so I am assuming that I'm using the open source one? I'm intending on getting some games working in the future and apps like google earth etc so I'd like to know that my 3D will be working before I 'settle in' with this release as it were. I thought I'd have a little poke around with xorg.conf to try to solve my issues but the file doesn't look like anyone else's that I've seen posted:

----8<--------------------------------------8<----

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2304 864
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

----8<-------------------------------------8<----

What gives? I assume this could be where some of my Display Preferences troubles arise from but I could do with a little help with where to begin tackling this situation.

Notes:
I know I could resolve this by getting an nVida card but sadly my current financial situation (skint!) prohibits that at the moment. Needless to say I shall not be investing in any ATI products when it does come to upgrade time though!

I also presume I could sort this by using an older version of Ubuntu, but that leads me to think I'm only going to run into further problems down the line then when I want to install some 'latest&greatest' software etc. If I take that route.

Any helpful advice would be much appreciated.

---

