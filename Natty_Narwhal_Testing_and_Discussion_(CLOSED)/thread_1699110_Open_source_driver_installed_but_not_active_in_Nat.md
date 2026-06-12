---
title: "Open source driver installed but not active in Natty"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by snlzkn on 2011-03-03
Hello,

I upgraded to Natty and my screen shows weird glyphs every now and then, my scrolling is extremely slow and glxgears gives only ~700 FPS. I have ATI HD 3650, I open CompizConfig Settings manager change stuff it does not affect anything. I tried compiz --replace it says:
```
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (opengl) - Fatal: Software rendering detected
compiz (bailer) - Info: Ensuring a shell for your session

```
compiz-check tells me that currently used driver is vesa.

There is no proprietary driver for Natty yet and people say that their open source drivers work fine. I am using LabVIEW on my Natty and after some time screen just becomes random pixels. I need to refresh it all the time.

The official page is not helping at all. It says how to remove fglrx and install the driver but after doing that my system is still using vesa :S
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The open source drivers don't need xorg.conf and I don't know what I can change or edit to make it running :D Any ideas?

---

### Post by Harry33 on 2011-03-03
> **snlzkn said:**
> Hello,

I upgraded to Natty and my screen shows weird glyphs every now and then, my scrolling is extremely slow and glxgears gives only ~700 FPS. I have ATI HD 3650, I open CompizConfig Settings manager change stuff it does not affect anything.
...
compiz-check tells me that currently used driver is vesa.
There is no proprietary driver for Natty yet and people say that their open source drivers work fine. I am using LabVIEW on my Natty and after some time screen just becomes random pixels. I need to refresh it all the time.
The official page is not helping at all. It says how to remove fglrx and install the driver but after doing that my system is still using vesa :S
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
The open source drivers don't need xorg.conf and I don't know what I can change or edit to make it running :D Any ideas?

Well ~700 fps (frames per second) is very good reusult. Even half of that is more than enough for fast gaming. :)

The system chooses vesa, if ati (or radeon) cannot be loaded.
Could you print here dmesg.log?
You can also force the system use radeon by creating xorg.conf into the folder /etc/X11/

---

### Post by snlzkn on 2011-03-03
I entered dmesg | grep radeon

```
[    5.628578] [drm] VGACON disable radeon kernel modesetting.
[    5.629654] [drm] Initialized radeon 1.33.0 20080528 for 0000:01:00.0 on minor 0
```

I have attached the full output dmesg > dmesg.log.txt. I had to compress it since it was big.

Later I may try opening the backup conf file and try to change it to use radeon but it should be possible without having to do that. 

I see updates on unity but I updated my ubuntu and nothing changed for me. I don't have unity launcher and Super button does nothing. I believe all of these are related. 

I was using compiz with lots of effects when I had proprietary drivers on lucid. So it must be possible to solve this issue :)

---

### Post by Harry33 on 2011-03-03
> **snlzkn said:**
> I entered dmesg | grep radeon

```
[    5.628578] [drm] VGACON disable radeon kernel modesetting.
[    5.629654] [drm] Initialized radeon 1.33.0 20080528 for 0000:01:00.0 on minor 0
```

I have attached the full output dmesg > dmesg.log.txt. I had to compress it since it was big.
...


I found the following odd lines in the dmesg (vesafb, vesa frame buffer):

```
[    3.485721] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.485742] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.486693] vesafb: framebuffer at 0xe05a3c00, mapped to 0xffffc90011100c00, using 5824k, total 5824k
[    3.486695] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    3.486697] vesafb: scrolling: redraw
[    3.486699] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    3.486813] Console: switching to colour frame buffer device 175x65
[    3.486840] fb0: VESA VGA frame buffer device
...
[    5.590364] [drm] Initialized drm 1.1.0 20060810
...
[    5.628578] [drm] VGACON disable radeon kernel modesetting.
[    5.629515] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.629520] pci 0000:01:00.0: setting latency timer to 64
[    5.629649] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.629651] [drm] No driver support for vblank timestamp query.
...
[    6.087442] uvesafb: monitor limits: vf = 60 Hz, hf = 65 kHz, clk = 119 MHz
[    6.087524] uvesafb: scrolling: redraw
[    6.087528] uvesafb: cannot reserve video memory at 0xe0000000
[    6.087533] uvesafb: probe of uvesafb.0 failed with error -5
```

I have one ATI HD2600Pro setup, and non of those lines referring to vesafb, VGACON or uvesafb exist in my dmesg.
So I think this is where the problem is.

---

### Post by snlzkn on 2011-03-04
Any ideas why I have them? I keep getting updates and one of the updates fixed my touchpad. May be I just have to wait and hope it will get fixed :D

---

### Post by snlzkn on 2011-03-04
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/686164](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/686164)
Here they said KMS has to be active and when I run 
grep -R modeset /etc/modprobe.d/
I don't get any output. I tried this
```
sudo echo options radeon modeset=1 > /etc/modprobe.d/radeon-kms.conf
bash: /etc/modprobe.d/radeon-kms.conf: Permission denied
```

But I used gedit and created that file and put the setting and restarted. Now compiz-check says driver is radeon. But still no compiz no new unity. compiz-check says this error:

Error: Software Rasterizer in use

I still have same entries in my dmesg. I created a xorg.conf file too. Maybe that's why compiz-check that's the driver in use. But I still think radeon is not active.

---

### Post by Harry33 on 2011-03-04
> **snlzkn said:**
> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/686164](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/686164)
Here they said KMS has to be active and when I run 
grep -R modeset /etc/modprobe.d/
I don't get any output. I tried this
```
sudo echo options radeon modeset=1 > /etc/modprobe.d/radeon-kms.conf
bash: /etc/modprobe.d/radeon-kms.conf: Permission denied
```

But I used gedit and created that file and put the setting and restarted. Now compiz-check says driver is radeon. But still no compiz no new unity. compiz-check says this error:

Error: Software Rasterizer in use

I still have same entries in my dmesg. I created a xorg.conf file too. Maybe that's why compiz-check that's the driver in use. But I still think radeon is not active.

And your xorg.conf looks like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

About your graphics card.
Is it a single card system (only radeonHD3650)
or is it some kind of hybrid card system (like radeon hd3200/3650)?
Is it integrated in mobo?

---

### Post by snlzkn on 2011-03-08
Sorry for the late reply again. It is only radeon HD3650. I have ASUS M50SA laptop it has only one graphics card. I believe it is integrated in mobo since it is a laptop and it cannot be changed later.
I added ForceGallium option under the section sector later. Also the Display subsection but I don't think any of them matters...

---

### Post by snlzkn on 2011-03-12
Latest updates made my unity working somehow. I did not change anything though. I said somehow because whenever I try to reorder my applications it crashes. Sometimes it does not even run when I login. I am always logged in to tty1 and I keep entering 
unity --replace
every time it crashes. Sometimes it even crashes when I click the Windows button. Maybe next update will fix this one too :D

---

