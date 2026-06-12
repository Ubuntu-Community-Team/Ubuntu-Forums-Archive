---
title: "Can't get display to work"
date: 2008-11-20
forum: Multimedia Software
---

### Post by fishwebby on 2008-11-20
Hello,

I can't get my display to work in Xubuntu (I've posted about this before, but a recent update seems to have killed it again). If I boot into recovery mode, drop to a root shell prompt, type

```
dpkg-reconfigure xserver-xorg
```

and answer the questions (it only asks me about the keyboard), then type

```
startx
```

it works. So that proves that it does work and it's not a hardware problem. However, if I boot normally, it changes between a black and grey screen for a while then stays black. Ctrl-Alt-Fn do nothing, other than change from black to grey. Sometimes. I've tried so many things to get this working, but to no avail. I even tried writing my own xorg.conf, which did nothing either. The last few lines of /var/log/Xorg.0.log (after lots of stuff about fonts) are

```
(II) Primary Device is: PCI 00@00:02:0
(EE) No devices detected.

Fatal server error:
no screens found
```

Here is the xorg.conf file that I created myself:

```
Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	DefaultDepth	24
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

that I made from getting information from running the following commands:

```
> sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)845G/845GL/845GE/845GV Graphics Controller Hardware Version 0.0
memory: 8000kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail

> sudo lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

I don't know if the xorg.conf that I came up with is valid, but as nothing that I try works it's difficult to tell.

Please please please could someone help me to try and fix this - happy to provide any information at all about my setup, just ask.

Many (hopeful) thanks in advance
Dave

---

### Post by fishwebby on 2008-11-21
I've managed to get it working! (well, once - we'll see if it breaks again) - it occurred to me that if I can start X as root after doing the

```
dkpg-reconfigure xserver-xorg
```

thing, then perhaps it wasn't the xorg.conf that was at fault, as it did work. When I did the above the only difference was that I had selected "recovery mode" from the grub boot menu. So... I had a look in /boot/grub/menu.lst and these were the two boot options:

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c4711601-b818-4045-9a1f-5c59a6da33f0 ro vga=792 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c4711601-b818-4045-9a1f-5c59a6da33f0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
```

Note the "vga=792" after the first one. I noticed in a menu.lst backup file that this didn't used to be there, and instead said "quiet splash". I changed the file accordingly, rebooted and here I am, back in Xubuntu with the screen working nicely! :-) I certainly didn't add that line to menu.lst, but I have used the startup manager program which I believe manages that file - won't be using that again in a hurry!

---

### Post by Jvsquire on 2008-11-23
well new to linux and ubuntu. well installed it on my intel tower that has mob845g. and well it only gives me one resolution. how do i change to a different. i mean the desktop is huge can see everything.

---

### Post by fishwebby on 2008-11-24
Hi,

well, to change resolution you should be able to go to "Desktop settings" in the configuration manager, which as well as the main menu I think you can access via right-clicking on the desktop. You should be able to choose the resolution in there. If not, then I'm afraid I don't know - if you need more help with this, please start a new thread, as otherwise I don't think people will see this (as this thread isn't really related).

Cheers
Dave

---

### Post by tpd2049 on 2009-01-17
Hi,

I am having the same problem and want to try the same fix (82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device)...how do I get to this file to edit the script...I'm new to Linux...

Thx!!

---

### Post by fishwebby on 2009-01-19
Hi,

well, xorg.conf is in /etc/X11/ and menu.lst is in /boot/grub/. You'll need to be root to edit them - the way I do it is to use the "nano" editor, like this:

```
sudo nano /etc/X11/xorg.conf
```

Cheers
Dave

---

