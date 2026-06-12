---
title: "Lost other OS during Natty Upgrade?"
date: 2011-03-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jercubsfan1 on 2011-03-11
Hi, I was dualbooting Joli OS 1.2 alongside with Ubuntu 10.10. Then last night, I decided to upgrade to Natty 11.04 Alpha 3. Now, when I turn on my computer, it doesn't even give me the grub menu. It just boots me straight into Ubuntu. When I go into the *boot menu*, I don't see any options at all... Has Joli OS been deleted? I Don't think so because I still only have half my memory on the Ubuntu filesystem. So i'm wondering how i can get it back, or delete Joli, and get my whole space back.... :confused: Thanks for the help.

---

### Post by andrewthomas on 2011-03-11
Post the output of 

```
sudo fdisk -l
```

The contents of your /etc/default/grub  file

The contents of your /boot/grub/grub.cfg file

after you have updated your grub.

```
sudo update-grub
```

---

### Post by beew on 2011-03-11
Why did you upgrade from a stable release which is only a few months old to an alpha?

Just asking.

---

### Post by anders_c_ on 2011-03-11
I have a triple boot on this machine with Natty, Maverick and Windows 7. Natty and Windows 7 both show up in grub but my Maverick has dissapeared =)
These things are often easily fixed with a stable live CD and chroot into the OS that has dissapeared.

---

### Post by Harry33 on 2011-03-11
> **jercubsfan1 said:**
> Hi, I was dualbooting Joli OS 1.2 alongside with Ubuntu 10.10. Then last night, I decided to upgrade to Natty 11.04 Alpha 3. Now, when I turn on my computer, it doesn't even give me the grub menu. It just boots me straight into Ubuntu. When I go into the *boot menu*, I don't see any options at all
... 

Just a few words:

In Grub (GRand Unified Bootloader) menu you can choose the operating systems that are installed.
In Boot menu (BIOS menu) you can choose the media (hard disk, cd, usb) where to boot.

Although Natty is in a pre-beta stage now, there are a number of show-stopper bugs waiting to be solved.
After all, a development stage is for testers and experienced users.

---

### Post by thonuz on 2011-03-12
> **Harry33 said:**
> Just a few words:

In Grub (GRand Unified Bootloader) menu you can choose the operating systems that are installed.
In Boot menu (BIOS menu) you can choose the media (hard disk, cd, usb) where to boot.

Although Natty is in a pre-beta stage now, there are a number of show-stopper bugs waiting to be solved.
After all, a development stage is for testers and experienced users.

Just boot from the live cd and see if your windows files are there. I always make a backup then.

---

### Post by jerrylamos on 2011-03-12
> **beew said:**
> Why did you upgrade from a stable release which is only a few months old to an alpha?

Just asking.
1.  Looking for bugs to help Ubuntu Development.
2.  Learning a lot about linux from tussling with problems.
3.  I find using a linux that always works and no new features a bit boring.
4.  I don't like Unity 3D but I run it just to see if anything breaks that I can write a launchpad bug about.

Enjoy...

Jerry

---

