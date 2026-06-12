---
title: "[SOLVED] nVIDIA AGP initialization failed"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by duffrecords on 2008-04-12
I'm running Gutsy and I just installed a new nVIDIA GeForce FX 5500 and installed the driver from nVIDIA's website.  I'm trying to force it to use the nVIDIA driver rather than agpgart, so I added
```
Optiion     "NvAGP"    "1"
```
to my xorg.conf.  The nvidia module and the agpgart module load during boot but when I type
 ```
cat /proc/driver/nvidia/agp/status
```
It still says
```
1. Status: Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem. 
```

I don't see any nVIDIA error messages when I use dmesg.  I got it to work one time but then while I was rebooting to fix another issue it reverted back to disabled.  What kind of further diagnostics should I try?

---

### Post by duffrecords on 2008-04-14
So, to update, I managed to get the card working and enjoyed some impressive desktop cube effects for about a day.  Yesterday I came home and found the system was powered off and now it restarts during the boot process!  The computer can run the BIOS utility, Memtest86+, and can boot from a floppy, but after I select any option from the GRUB loader, it restarts itself.  I can't boot Ubuntu, Ubuntu (recovery mode), Windows XP, Windows XP safe mode, or any live CD.  I'm afraid the nVIDIA card must have caused some damage to the hardware.

Since then I've removed the graphics card, updated the BIOS and loaded the default settings, and ran Memtest86+ (no memory errors) but it still won't boot beyond the GRUB loader.  What should I troubleshoot next, and how?

---

### Post by duffrecords on 2008-05-02
I'm going to mark this as SOLVED because technically speaking, it has been solved.  Several of the capacitors on my motherboard failed, leaking electrolytic fluid and preventing any OS from booting beyond the BIOS check.    Although this is not related to the NVIDIA card or Ubuntu, perhaps someone will find this post helpful.  If you find yourself in this situation, take a look at the electrolytic capacitors on your motherboard (the cylindrical components that look like miniature soda cans connected by two leads).  If the tops are bulging out or they are emitting a liquid, that's bad news.

---

