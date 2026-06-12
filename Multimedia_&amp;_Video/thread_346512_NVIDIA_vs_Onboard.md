---
title: "NVIDIA vs Onboard"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by piponline on 2007-01-25
Hi.
Newbie here. 
After having successfuly installed Ubuntu 6.06 I couldn't boot. I spent several nights experimenting all the hints picked up in the forums but the only thing that worked was to disable my nVidia GeForce4 MX 440 in the bios and to activate the onboard graphical card.

Now that I have ran, tested and approved Ubuntu I want to get it working with my nVidia.

I've been reading some posts and how to's about configuring nVidia cards (namely this one:[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)) but I have some questions.

First, after installing the driver, I can't enable it: the command "sudo nvidia-glx-config enable" just outputs 
```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
```

Now, the xorg.conf doesn't have the driver section with 'nv'. Instead it has this:
```
Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
```

Using the command 'lspci' I found the BusID of the nVidia card. Should I go ahead and change the lines above into these?
```
Section "Device"
	Identifier	"nVidia Corporation GeForce4 MX 440"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection
```
But then again the nvidia drive is not enabled yet, right?

Also,is it ok to do this if the nVidia isn't the first card in the bios?

This is killing because, to get totally weird, if I want to boot Windows XP I have to reset the bios as it was (giving priority to pci cards) because it doesn't like the onboard card (gives me a blank screen at the time of logging in). 
So I'm constantly changing the bios settings due to this problem: if I go to windows I have to use the nVidia; if I go to Ubuntu I have to use the onboard. It's a stupid thing, I know.

I hope someone can help me with this.

Thank you,

---

### Post by Ptero-4 on 2007-01-25
Try changing the xorg.conf file. since you said the ther driver was installed it should work after swithing the BIOS setting.

---

### Post by piponline on 2007-01-26
I'll give it a try tonight.

---

### Post by piponline on 2007-01-26
Hey all,

I'm still crashing with my nvidia geforce4 card.
I changed the xorg.conf like discussed above, then rebooted and went to bios to activate the card.
Unfortunetly, that took me right back to where I was some nights ago when I was struggling to boot for the first time. Here's my cry for help about that: [http://www.ubuntuforums.org/showthread.php?t=344314](http://www.ubuntuforums.org/showthread.php?t=344314)

If the nvidia is the active card in the bios, I crash at boot time while "Loading hardware drivers...". 
The verbose is totally criptical to me. "Sysenter_past_espx0x54/0x79", "Kernel panic", etc. In my other thread I detail these errors a bit more.

Boot options are of no effect, I can't even get to a text prompt. I have to finger reset the machine and put the onboard card alive in the bios again. Then I get a xserver error, of course, because the xorg.conf is still with the nvidia driver. But through the prompt I revert to a backup of that file which enables me to "startx" just fine.

Help?

Thanks!

---

### Post by piponline on 2007-01-26
Here's the output of the lspci command, in case it helps somehow:

0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
**0000:00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)**
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
**0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)**
0000:01:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
0000:01:03.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:01:03.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by piponline on 2007-01-26
:guitar: 

Ok, problem solved!!!!

Thank you so much [tseliot]("http://http://www.ubuntuforums.org/member.php?u=19388") for this [Howto]("http://doc.gwos.org/index.php/Nvidia_Intel_Integrated")!!!! ([http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated))

Many thanks also to the ["Post the way you got the Nvidia driver to work"](http://www.ubuntuforums.org/showthread.php?t=221313&page=3) thread that pointed out tseliot Howto.

---

