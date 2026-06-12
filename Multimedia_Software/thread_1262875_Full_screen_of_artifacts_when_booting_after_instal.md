---
title: "Full screen of artifacts when booting after install"
date: 2009-09-10
forum: Multimedia Software
---

### Post by jbohren on 2009-09-10
I recently installed Ubuntu 9.04 on a Quad 2.66 Mac Pro with an ATI x1900XT gpu.

When I boot from the livecd, everything displays correctly, but when booting from disk, I see nothing but white, green, and purple artifacts. It's not a problem with X since I can't even switch to the text prompt.

What is the livecd doing to load up the graphics drivers that the install wouldn't be doing?

thanks

---

### Post by tgalati4 on 2009-09-10
The live CD is probably using "safe" graphics mode, probably using the VESA driver.

Boot the live CD and examine the contents of /var/log/Xorg.0.log

Boot from the disk and do the same.  Compare the two and report back.

---

### Post by jbohren on 2009-09-10
> **tgalati4 said:**
> The live CD is probably using "safe" graphics mode, probably using the VESA driver.

Boot the live CD and examine the contents of /var/log/Xorg.0.log.

So the Xorg.0.log on the livecd shows that it's successfully loading the driver for the ATI x1900. On the system that I've tried booting from a couple times now, Xorg.0.log doesn't even exist.

---

### Post by tgalati4 on 2009-09-10
So that's good news, the ATI driver is loading OK in the live CD.  xorg also controls the mouse/touchpad and keyboard (including special keys) so perhaps there is something loading that's crashing the X server before it can even start logging.

You should have a file called .xsession-errors in your home directory.

cd
cat .xsession-errors

also

dmesg | tail      (spacebar to go forward, q to quit)

Look for any obvious errors during boot.

Also check for an interrupt problem:

cat /proc/interrupts

---

### Post by jbohren on 2009-09-10
> **tgalati4 said:**
> 
cd
cat .xsession-errors


On the installed disk, no such file exits, and on the livecd just the usual gtk warnings.

> **tgalati4 said:**
> 
dmesg | tail      (spacebar to go forward, q to quit)

On the installed disk, /var/log/dmesg just reads: "(Nothing has been logged yet.)" The livecd doesn't show much related to video.

> **tgalati4 said:**
> 
Look for any obvious errors during boot.

Also, the text output never comes up, it goes right into the messed up display mode.

> **tgalati4 said:**
> 
Also check for an interrupt problem:

cat /proc/interrupts
No spurious interrupts on the livecd, again, nothing to check on the boot disk.

thanks for your continued help

---

### Post by tgalati4 on 2009-09-11
I'm not familiar with the Quad Mac Pro.  Is this ppc or intel architecture?

During boot from the hard disk, did you hit Alt-F1 to see the boot messages scroll by?  You can hit the "pause" button (near scroll-lock) to stop the screen so you can watch what is happening.

Will it boot into rescue mode on the hard disk?  Have you run memtest to ensure that your RAM is working OK?

I would regress to Intrepid or Hardy and try installing those.  You could put them on another partition.  Regressions are common with rapid development of the kernel taking place.

If your machine is brand new, then try koala.  Could be some kernel stuff that has only recently been added.

The difference between the live CD and hard disk boot is how the filesystem is mounted.  If you are having a SATA/disk controller issue, then that would show up in a normal boot, but may not show up on the Live CD which is running entirely in RAM disk.

---

### Post by jbohren on 2009-09-11
> **tgalati4 said:**
> I'm not familiar with the Quad Mac Pro.  Is this ppc or intel architecture?

Nope, its a quad Xeon.

> **tgalati4 said:**
> 
During boot from the hard disk, did you hit Alt-F1 to see the boot messages scroll by?  You can hit the "pause" button (near scroll-lock) to stop the screen so you can watch what is happening.

I can't even get into console mode during boot.

> **tgalati4 said:**
> 
Will it boot into rescue mode on the hard disk? 

I'm not familiar with this, what would that test?

> **tgalati4 said:**
> 
Have you run memtest to ensure that your RAM is working OK?

Yeah, memory looks fine.

> **tgalati4 said:**
> 
I would regress to Intrepid or Hardy and try installing those.  You could put them on another partition.  Regressions are common with rapid development of the kernel taking place.

Yeah, sorry for not saying it, but that was the first thing I tried.

> **tgalati4 said:**
> 

If your machine is brand new, then try koala.  Could be some kernel stuff that has only recently been added.

It's about 2 years old at this point.

> **tgalati4 said:**
> 
The difference between the live CD and hard disk boot is how the filesystem is mounted.  If you are having a SATA/disk controller issue, then that would show up in a normal boot, but may not show up on the Live CD which is running entirely in RAM disk.

Would that be possible if I could mount, read and write files from and to the installed disk?

Thanks

---

### Post by tgalati4 on 2009-09-12
The rescue mode is a limited-driver boot (similar to safe mode in windows) that gives you a root console.  No X server, few drivers so it allows you to troubleshoot.  It shows up in the GRUB menu when you boot.  You have 3 seconds to hit the down arrow once until it auto-boots into normal mode.

Here's my 2 cents:  Xenons (Duals and Quads) are really server processors and generally found in server hardware.  Apple put them in a high-end workstation.  

Servers have raid controllers built in.  I know that some controllers are fiddly.  If you can't talk to a disk because of an unknown raid controller, then you can't boot.

The live CD doesn't need to load any disk controllers other than the CD ROM to read the disk.  If you can read the disk then you can boot off of it since the disk becomes the file system and everything is run out of RAM.

Do a google search and find out what kind of I/O chipset/raid controller your machine contains and then do a search on that.  It could be as simple as a kernel boot switch.

I know that some older Dell poweredge servers are fiddly as well because of the built-in controllers.

I presume you are running/installing the 64-bit kernel since the Xenon is a 64-bit processor with large memory addressing.  I'm pretty sure the RAID controller is expecting 64-bit addressing.

---

### Post by jbohren on 2009-10-03
I'm back to trying to work on getting this thing up and running. One thing that could help that I hadn't noticed before, is that the artifacts pop up BEFORE grub even loads. So the boot menu (after rEFIt) never even appears.

---

### Post by jbohren on 2009-10-03
OK.

So after a bunch of searching, it looked like it wasn't getting into the bootloader for some reason because there was some disconnect between rEFIt and GRUB. So rEFIt has problems when you want to boot into linux from a hard drive other than the first one. Additionally, the Ubuntu Jaunty installer seems to not deal with this situation either. Even if you install to another disk, it puts the bootloader on the wrong one: (hd0).

So to recap:
Once getting in this situation,
 - blow away rEFIt and linux
 - re-install rEFIt
 - use boot camp to format the first drive (if you want to use another one, just swap it with the first one)
 - install ubuntu to the first drive
 - tell it to use the entire disk
 - all defaults from there

To anyone else who encounters this, good luck.

-j

---

