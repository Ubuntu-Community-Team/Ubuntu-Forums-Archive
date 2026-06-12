---
title: "graphics in games messed up"
date: 2010-10-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by libihero on 2010-10-05
when i try to play games like supertux 2, it flickers A LOT
any way of fixing this?
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

---

### Post by efflandt on 2010-10-05
I imagine X1200 is a legacy chip.  If it is even remotely similar to the X1300 on my Athlon64 desktop or Mobility X1300 on my company laptop it might not like kernel mode setting (which became the default in Lucid).

I haven't run Maverick on that PC except briefly from a USB hard drive to see if it worked (that drive currently has nvidia driver for newer PC).  But in Lucid for the ATI X1300 I had to use **nomodeset** (or more chip specific **radeon.modeset=0**) kernel boot parameter to avoid sluggish video on the desktop and so it could suspend/hibernate, and for the laptop to avoid occasional graphic glitch/hang during boot.  So you might try that.

To test that hit **e** during grub menu and add **nomodeset** on the same line after **quiet splash**.  Then hit Ctrl+X to boot.

---

### Post by libihero on 2010-10-06
wohoo thank you SO MUCH!

---

### Post by libihero on 2010-10-08
i know it sounds stupid, but how do i change it permanently?

---

### Post by ktp on 2010-10-08
for GRUB 2: 
> edit /etc/default/grub
add nomodeset to GRUB_CMDLINE_LINUX
run sudo update-grub

for GRUB 1:
> edit /boot/grub/menu.lst
add nomodeset to the line beginning with # kopt=
run sudo update-grub

---

### Post by libihero on 2010-10-09
Thanks!

---

### Post by libihero on 2010-10-09
@efflandt when i put "radeon.modeset=0", it ends up breaking my suspend, is there any fix for that?

my chip is also a legacy and i think its very similiar to yours.

thanks again and sorry for the bother!

---

### Post by efflandt on 2010-10-09
What happens with suspend, does it not fully go into suspend, or does it not wake up when you press your power button (keyboard or mouse may not normally wake it from suspend)?

With the ATI X1300 on my desktop in Lucid (10.04) with its default kernel mode setting, suspend would make my LCD screen go dark, but video would not turn off completely (my HDTV still had a signal) and the computer would not completely go into suspend.  Similarly with hibernate, it would dark the screen and go though the motions, but still a signal to screen and no power down.  2D video was also slow, for example moving cards in Solitaire was sluggish and left a tail of rectangles during card motion.  For me nomodeset or radeon.modeset=0 solved all that [back up to Karmic (9.10) speed and successful suspend/hibernate].

You might check /var/log/pm-suspend.log (or similar log with number at the end if that is empty) to see if that reveals anything.  But when I had problems resuming from suspend or hibernate in a low end laptop with Karmic using some sort of ATI 200 video with default driver, it did not even log anything when resume or waking failed.  It also had issues with dropped keys and delayed/jumpy mousepad in Karmic.  Strangely suspend/resume work fine in Lucid using nomodeset, although, it would get video tearing in games like supertuxkart (maybe because it only had 512 MB total including shared video RAM).

Sorry I do not know much about suspend problems other than hearing that it is often video related.  Although, on another old laptop with nvidia it was a combination of an xorg.conf setting needed for that nvidia, and a system error regularly checking for non-existing floppy in a hot swap drive bay (had to totally disable floppy module).

---

### Post by libihero on 2010-10-09
d'oh
trade-off.... either have no tearing in games or have suspend working fine..... :(
i need a new laptop haha

---

