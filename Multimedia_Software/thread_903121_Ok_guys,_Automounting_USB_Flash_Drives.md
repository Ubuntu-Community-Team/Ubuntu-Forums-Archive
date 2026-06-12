---
title: "Ok guys, Automounting USB Flash Drives"
date: 2008-08-28
forum: Multimedia Software
---

### Post by arch.stanton on 2008-08-28
Hey there. For all you people out there that don't feel like manually mounting USB flash drives but DO use the search tool; this is the thread to watch. I've used the search tool for months trying to find a simple solution, and when i gave up on that i tried to look for a complicated solution. 

But so far I'm getting band-aid answers.

This is what happens

(insert Sandisk USB drive)
Alert: Invalid Mount Option
(open terminal)
sudo fdisk -l
sudo mount /dev/sdb1 /media/usb

problem bandaid'd.

So then i edited fstab and did something. But i still dont have permission to read/write files unless im root. PLUS it doesnt automount on being plugged in. Someone told me to do it specifically for this device but i deal with a lot of devices, i want everything to automount ASAP.

Ok. Are you ready to solve this problem and make it a sticky? Well alright

on your mark, get set... GO!!

---

### Post by arch.stanton on 2008-08-28
lets answer this and put this issue to rest once and for all, also sticky it.

---

### Post by mc4man on 2008-08-28
> lets answer this and put this issue to rest once and for all, also sticky it.
The problem with that is with the exception of a few usb flash drives there is no general issue, only local. It should be automounting w/ rw permissions for the active console (current user). Maybe you should post what model of sandisk drive you have. (or run>  sudo lshw -C disk with the drive in (doesn't need to be mounted

Have you been doing an unsafe removal in windows or have you altered the partitioning? (using encryption

I've never had any issue with sandisk flash drives, even those with the U3 partition. There is a peculiarity with the U3 drives in that they are seen as 2 devices, a disk drive @ /dev/sdxx (usb mass storage, what should be automounting) and a cdrom drive @ /dev/scdx (the U3 partition) which can only be mounted by root and is of no value anyway.

---

### Post by arch.stanton on 2008-08-28
so i did what you say. that command didnt really do ANYTHING though. it said some stuff but my flash drive still isnt automounting.

Alert:Cannot mount volume. 

This is what happens now.

---

### Post by arch.stanton on 2008-08-31
so yes i have altered the partitioning. Also when i try to mount Kingston drives it dont work either.

---

### Post by jbor7755 on 2008-08-31
Yep i have a Dell XPS 1330 with a clean install of Ubuntu x64, and the exact same problem.

Not a single one of my USB drives (3x flash - two brand new, and a brand new 320 GB Western Digital passport) will mount, all giving the same error which arch.stanton mentions.  They DO work, however, in ubuntu 32bit.

They can be manually mounted but this is not an acceptable solution.  I have never done an "unsafe" removal from Windows either.

The Ironic thing is that one of the flash drives was used as the live USB for installation and it worked fine for that.

---

### Post by Uncle Che on 2009-01-07
And four months on, this problem still exists. Doesn't anyone have a solution? I have the problem when mounting a flash drive(several different brands) and mounted cards inserted into my card reader. Nothing will mount. This is a clean install of 8.04 upgraded to 8.10.

---

