---
title: "With 2.6.37-10 kernel the screen goes black."
date: 2010-12-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2010-12-18
I just updated to 2.6.37-10 kernel, the grub menu displays properly, but when I select the default or the recovery mode the screen goes completely black, and it will not accept keyboard or mouse input.

This happens on an Intel Atom Mini-ITX board running 64 bit Natty.  My other test system, a Via Mini-ITX board runs 32 bit Natty kernel 2.6.37-10 without a problem.

---

### Post by MacUntu on 2010-12-18
(user error)

---

### Post by davideotape on 2010-12-18
Getting the same here, but the problem seems to be with all kernels here :S Looks like it's time to chroot :(

---

### Post by kansasnoob on 2010-12-18
> **JRV said:**
> I just updated to 2.6.37-10 kernel, the grub menu displays properly, but when I select the default or the recovery mode the screen goes completely black, and it will not accept keyboard or mouse input.

This happens on an Intel Atom Mini-ITX board running 64 bit Natty.  My other test system, a Via Mini-ITX board runs 32 bit Natty kernel 2.6.37-10 without a problem.

I get the same thing with an Atom 230 and i945, but 2.6.37-9 still boots. Even recovery mode with the -10 boots to a black screen. I can hear the drum roll but keyboard input does nothing, not even Alt+SysReq+B.

---

### Post by JRV on 2010-12-18
> **kansasnoob said:**
> I get the same thing with an Atom 230 and i945, but 2.6.37-9 still boots. Even recovery mode with the -10 boots to a black screen. I can hear the drum roll but keyboard input does nothing, not even Alt+SysReq+B.

Mine is an Atom 330 and i945, 2.6.37-9 boots for me too.

---

### Post by macroshaft on 2010-12-18
I'm getting this on an AMD processor but using recovery mode and failsafe graphics works ok for me

---

### Post by talkeetnik on 2010-12-19
After upgrade from 2.6.37-9 to -10
Grub menu boots to blank purple, sometimes blinking upper left cursor
whb@GWM6309:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

Booting from previous kernel works fine.

WH Bouterse

---

### Post by cariboo on 2010-12-19
> **talkeetnik said:**
> After upgrade from 2.6.37-9 to -10
Grub menu boots to blank purple, sometimes blinking upper left cursor
whb@GWM6309:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

Booting from previous kernel works fine.

WH Bouterse

This sounds like a different problem from the others, it sounds like update-grub didn't work. I'd suggest you open a terminal, and type:

```
sudo update-grub
``` 

and watch to see if the latest kernel is detected.

---

### Post by talkeetnik on 2010-12-20
grub-update was tried again
appears to see and process everything without errors
upon reboot Same freeze at maroon blank screen
booting recovery mode freezes at 
----
[end trace df6eb6836e1d38cb]
Fixing recursive fault but reboot is needed!
----
freeze and cold reboot with same balnk screen freeze

edit grub with xxx-9-generic and f10 reboots successfully

#inxi gives
CPU[-Dual core Intel Pentium Dual T2330 (SMP) clocked at 800.000 Mhz-] Kernel[-2.6.37-9-generic x86_64-] Up[-7 min-] Mem[-437.6/1999.8MB-] HDD[-320.1GB(26.2% used)-] Procs[-155-] Client[-Shell-] inxi[-1.3.2-] 

?????

whb

---

### Post by cariboo on 2010-12-20
You shouldn't need to, but have you tried adding nomodeset to the end of the kernel line in grub?

I had a similar problem to what some of the others are reporting back around the .6 kernel, since .8 things have been working the way they should on my netbook with i945 graphics chipset.

---

### Post by JRV on 2010-12-20
> **cariboo907 said:**
> You shouldn't need to, but have you tried adding nomodeset to the end of the kernel line in grub?


I tried it and it boots with low graphics, it says it can not run unity and runs the classic desktop with 1600x1200 resolution.  My monitor is 1680x1050. Then I set it to run the classic desktop and both panels are gone.

---

### Post by drs305 on 2010-12-20
> **JRV said:**
> I tried it and it boots with low graphics, it says it can not run unity and runs the classic desktop with 1600x1200 resolution.  My monitor is 1680x1050. Then I set it to run the classic desktop and both panels are gone.

If you end up on the classic desktop try opening a terminal with CTRL-ALT-T and then typing "gnome-panel". If it reports it's already running: "killall gnome-panel".

---

### Post by Catharsis on 2010-12-21
Just edit the kernel you're trying to boot into at the grub menu (press 'e') and remove "quiet splash" and then boot it (Ctrl+x). That should print out dmesg to the screen while it's booting and should show you where the DRM is erroring (or at least switch to Xorg.0.log and show any errors there).

P.S. Just making sure, you can't switch to a TTY with Ctrl+Alt+1, right?

---

### Post by talkeetnik on 2010-12-21
tried the nomodeset parameter with no change
Downloaded 11.04 Daily Build 122110...
Same problem at boot up. Same freeze point as well with splash removed 
to see stopping point.
Working through f6 menu of live cd
Positive results with the acpi=off 
Have not had to use that in years.
Definitely a change between 2.6.37-9 and 2.6.37.10 kernels ?
Subsequent success at hd boot with changed parameters.

So...???

WH Bouterse
Talkeetnik
Alaska

---

### Post by Ishamael on 2010-12-22
I also have this problem, since this morning.
No matter which kernel I select I always end up with a blank screen before KDM.
All that I did this morning was to upgrade a bunch of packages (the only I think could be related are linux-firmware (1.44), udev (165-0ubuntu1) and possibly dbus (1.4.0-0ubuntu2)) 

Setting "acpi=off" or "nomodeset" in grub makes it go away but then I am forced to use a resolution of 800x600, which makes everything stretched on my screen.

---

### Post by Harry33 on 2010-12-22
> **Ishamael said:**
> I also have this problem, since this morning.
No matter which kernel I select I always end up with a blank screen before KDM.
All that I did this morning was to upgrade a bunch of packages (the only I think could be related are linux-firmware (1.44), udev (165-0ubuntu1) and possibly dbus (1.4.0-0ubuntu2)) 

Setting "acpi=off" or "nomodeset" in grub makes it go away but then I am forced to use a resolution of 800x600, which makes everything stretched on my screen.

Seems odd to me. But I doubt very much linux-firmware has anything to do with that.
What graphics card are you using and what driver?
Confirm, you do see plymouth?

---

### Post by ronacc on 2010-12-22
I have had this for awhile , what I found is if I edit the line in /boot/grub/grub.cfg  that reads set gfxpayload=$linux_gfx_mode  to set gfxpayload=1920x1080  I can boot normaly , you can aslo edit it at the boot menu to try it before changing your grub.cfg of course  use the correct res for your setup like this  set gfxpayload=your resolution  . Trying to figure out how to edit /etc/grub.d/10_linux so this sticks through grub updates .

---

### Post by Ishamael on 2010-12-22
> **Harry33 said:**
> Seems odd to me. But I doubt very much linux-firmware has anything to do with that.
What graphics card are you using and what driver?
Confirm, you do see plymouth?
I have an Intel 945GME. Using the standard Intel driver I guess, haven`t changed it.
Edit: Nevermind, I was mistaken. I don`t see Plymouth when starting.

> **ronacc said:**
> I have had this for awhile , what I found is if I edit the line in /boot/grub/grub.cfg  that reads set gfxpayload=$linux_gfx_mode  to set gfxpayload=1920x1080  I can boot normaly , you can aslo edit it at the boot menu to try it before changing your grub.cfg of course  use the correct res for your setup like this  set gfxpayload=your resolution  . Trying to figure out how to edit /etc/grub.d/10_linux so this sticks through grub updates .
Thanks, I`ll try that.
I am pretty sure you should add that to the line "GRUB_CMDLINE_LINUX_DEFAULT" in /etc/defaults/grub

---

### Post by dino99 on 2010-12-22
you can try grub-gfxpayload-lists

---

### Post by Ishamael on 2010-12-22
Neither setting gfxpayload to my screens normal resolution nor installing the grub-gfxpayload-lists helped.
Thanks for the suggestions though.

---

### Post by ronacc on 2010-12-22
probably that wouldn't fix your problem , what I was getting was black screen shortly after grub , never got to gdm  or log in , keyboard unresponsive except for ctrl>alt>del or alt>sysreq>b   it was never starting the xserver .

---

### Post by Catharsis on 2010-12-22
I just triaged a bug yesterday which sounds like this (one of you might have filed it). It's [lpbug]693093[/lpbug].

Notice the bug is only for Intel 945gme graphics cards. If you're experiencing the exact same symptoms with a different chipset, please file a new bug report.

Please just click "Does this bug affect you?" at the top and subscribe; this is the preferred way to "me too" a bug report, instead of spamming the comments section, which is only reserved for new information you can provide.

If any of the symptoms are different, please just file a new bug report. If the symptoms are different, the bugs are different, and you'd be undermining both reports by posting comments in the original.

---

### Post by ronacc on 2010-12-22
me too'd and added comment , nvidia 7600 gs here .

---

