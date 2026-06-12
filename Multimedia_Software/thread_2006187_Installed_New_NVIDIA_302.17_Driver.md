---
title: "Installed New NVIDIA 302.17 Driver"
date: 2012-06-18
forum: Multimedia Software
---

### Post by LaJuan on 2012-06-18
Hi,

I saw there's a new driver from NVIDIA and install through the ppa method. Reboot my system and still can't seem to change my screen resolution. Here's the message I get in addition drivers menu:

[COLOR=Navy]This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

You need to install this driver if you wish to use the Unity desktop, enable desktop effects, or run software that requires 3D acceleration, such as some games.

Driver active but not currently in use.[/COLOR]

Can ANYBODY shed some light on this message or where I'm falling short?

Intel P3, Dell Precision 370, 2GB RAM, 180GB free space, running Ubuntu 12.04.

LaJuan
:confused::confused::confused::confused::confused::confused::confused:

---

### Post by eulu on 2012-06-19
Not sure what that means but I also updated through ppa from 295.59 to 302.17. Mine doesn't have description but does say it's active but not in use. Not sure if this is contributing to my problems..  I went through hell trying to get things stable with my card (GT7950), and finally did with the 295.59 set. Everything was finally stable so you'd think I would have been careful about not letting them get touched, but I didn't and this 302.17 set got into my system through the ppa and now I have troubles again.. When I first booted after the update I had to hard boot three times before it could pick up a default screen resolution  that could display on my monitors (I'd get black screens or flashing black screens) . Now when I try to load a video, or start the screensaver, or try to load an app in wine, the screens will just go black and start flashing and I am stuck until a few more hard reboots until a default resolution comes back.. Fun stuff

Update:  I've been messing around with settings and decided to try deleting my conf file and resaving it. It said something about conflicts in modes and wanted to autofix. I allowed it to autofix and then saved the conf file and things seem much more stable now.

---

### Post by andyhelloween on 2012-06-19
I too installed through ppa the new nVidia driver 302.17. I haven't experienced what you guys are saying, but what I did notice is when connecting the LCD through HDMI... I lose my gnome theme.

Perhaps somebody is experiencing the same thing as me?

---

### Post by andyhelloween on 2012-06-20
By the way... I decided to downgrade the nVidia driver to the previous version. Here are the steps:

[http://ubuntuforums.org/showpost.php?p=12041521&postcount=3](http://ubuntuforums.org/showpost.php?p=12041521&postcount=3)

Cheers!

---

### Post by Yellow Pasque on 2012-06-20
Googling precision 340 looks like you probably have a Quadro NVS 280 card (based on NV34 which is equivalent to Geforce FX 5k-series).

I'm guessing that you should be using 173-series nvidia driver and that you're suffering from this bug: [https://bugs.launchpad.net/bugs/948053](https://bugs.launchpad.net/bugs/948053)

Please show output of:
```
lspci
```

Extra credit: Post /var/log/Xorg.0.log

---

### Post by LaJuan on 2012-07-12
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation NV38GL [Quadro FX 1300] (rev a2)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

---

### Post by Yellow Pasque on 2012-07-14
You need to be using this driver: [ftp://download.nvidia.com/XFree86/Linux-x86/173.14.35/NVIDIA-Linux-x86-173.14.35-pkg0.run](ftp://download.nvidia.com/XFree86/Linux-x86/173.14.35/NVIDIA-Linux-x86-173.14.35-pkg0.run)

---

### Post by LaJuan on 2012-07-21
Thanks!!!!!!!!! I'll get it a go today and let you know my results....

---

