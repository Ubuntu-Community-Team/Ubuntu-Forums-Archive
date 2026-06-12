---
title: "Problem installing fglrx driver on Thinkpad T400"
date: 2010-01-12
forum: Multimedia Software
---

### Post by opentux on 2010-01-12
I have a Thinkpad T400 laptop with an ATI Mobility Radeon HD 3400 graphics card. I had been using the default open source drivers without problem but recently decided to activate the proprietary fglrx driver in System->Administration->Hardware Drivers.

I rebooted the computer. It got as far as the booting Ubuntu symbol and hung. The screen went blank except for a couple of half-drawn lines. The machine was unresponsive and had to be rebooted by the power button.

I booted into recovery mode and replaced the "fglrx" driver with "ati" in xorg.conf, but still the problem remained. I [uninstalled fglrx with apt-get and reinstalled the mesa drivers]("https://help.ubuntu.com/community/RadeonDriver#Removing the proprietary fglrx driver"), but to no avail. Running startx from the CLI quit with the error "(EE) No drivers available".

I removed the /etc/X11/xorg.conf file to allow X to auto-detect my hardware and the system booted normally.

I have a working system again, but I would like to understand what went wrong. Why didn't the fglrx driver work, and how did my xorg.conf file get screwed up?

Could it have something to do with the other Intel device listed below?
```

>lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

```

```

>cat /etc/X11/xorg.conf 

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"ati"
EndSection

```

---

### Post by opentux on 2010-01-12
Well, I discovered what was going wrong. My Thinkpad T400 has a feature called [switchable graphics]("http://lenovoblogs.com/insidethebox/?p=154"), which allows the OS to change between an integrated and a discrete GPU to save power. (This explains the two devices listed in lspci.)

Unfortunately only Windows Vista supports switchable graphics. For Ubuntu I need to [choose between the GPUs in the BIOS]("http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_(Karmic_Koala)_on_a_ThinkPad_T400#Before_Installation").

The error I encountered was probably the result of having switching enabled in the BIOS. The Intel GPU was in use but seeing the ATI GPU Ubuntu allowed me to install fglrx. The next reboot then tried to apply the fglrx driver to the Intel device.

Presumably fglrx would work if I chose only it in the BIOS. But for now I think I will stick with the Intel device and save some battery life.

---

### Post by Stonedancer on 2010-02-24
Wow it took me 3 days of swearing until I found someone else with the same problem as me. Exactly the same laptop and chipset. I have a "requirement" ok "want" to have flashy graphics and 3d games in Ubuntu so that's why I went for the ATI chip on this machine.

I've guessed after a while that it was the graphics that was causing the problem so I tried all three options in the bios and neither one seemed to work.

I know you want to stick with the intel but could you do me a favour and see if the fglrx driver works on YOUR system and which bios option works for you?  This problem (plus some cairo-dock issues) almost made me want to go back to xp but when doing research using xp I was reminded how slow everything is. hehe.:D

---

### Post by opentux on 2010-02-25
> **Stonedancer said:**
> could you do me a favour and see if the fglrx driver works on YOUR system and which bios option works for you?
I gave it a try and everything worked as I had expected. My system worked fine in all of the following configurations:
[LIST=1]
[*]BIOS set to "switchable" and OS using integrated graphics + open source driver
[*]BIOS set to "integrated" and OS using integrated graphics + open source driver
[*]BIOS set to "discrete" and OS using ATI graphics + open source driver
[*]BIOS set to "discrete" and OS using ATI graphics + fglrx driver
[/LIST]

So yes, the proprietary fglrx driver works for me when I disable switchable graphics.

Note: you may need to disable the "Enable graphics switching" option in the BIOS to prevent the computer changing back from discrete to switchable graphics after each reboot. It is directly below the "Graphics: Switchable/discrete/integrated" option.

---

### Post by Stonedancer on 2010-02-25
Awesome, Cheers man. I have XPsp3 and Ubuntu 9.10 working.

I think I was so focused on the graphics type (switch-able etc) that I didn't realise it was turning it back on each time.  I was convinced I had a hardware malfunction and because we bought 4 identical units I was swapping hard drives around so probably got myself confused about which machine I'd made which changes on.
Thanks again for your input.

---

### Post by pumrum on 2010-04-03
I have the same setup and was wondering if you see the following:

When I have a Nautilus file browser open, and I click/drag a file or folder around -- if I pass over another folder (with the left mouse button still held), the screen takes about 1 second to "paint" the shading over the window. Once it paints, the shading disappears. If I continue to move the file over another folder, it will "paint" again. I did some googling, but didn't come up with much. Here's what I have:

[LIST]
[*]T400
[*]Intel T9600 2.80GHz Core2Duo CPU
[*]8GB RAM
[*]256MB ATI Radeon 3470HD
[*]Discrete enabled in BIOS
[*]Switchable graphics disabled
[*]Ubuntu 9.10 64bit
[*]fglrxinfo driver 2.1.9016 (installed by Ubuntu)
[/LIST]

```
user@hostname:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3400 Series
OpenGL version string: 2.1.9016
```

```
user@hostname:~$ cat /etc/X11/xorg.conf 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection
Section "Module"
	Load	"glx"
EndSection
Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
```


I have been running a T60 with the Open source drivers and Ubuntu 8.10 32bit, so I'm not exactly sure what to expect on the new version, architecture, and hardware. Thanks!

---

### Post by opentux on 2010-04-06
> **pumrum said:**
> I have the same setup and was wondering if you see the following:

When I have a Nautilus file browser open, and I click/drag a file or folder around -- if I pass over another folder (with the left mouse button still held), the screen takes about 1 second to "paint" the shading over the window. Once it paints, the shading disappears. If I continue to move the file over another folder, it will "paint" again.

I have no such problem with drag and drop.

My system appears identical to yours except that I am using the 32bit OS and you are using 64bit, so perhaps the problem is in that?

---

