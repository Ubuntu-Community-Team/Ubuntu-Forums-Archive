---
title: "Upgrade from 10.04 to 10.10 - Kernel still 2.6.31?"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 7bn on 2010-09-05
Did I do something wrong? I thought the kernel would update to 2.6.35-19.28. Do I need to update manually? Upgrade went fairly smooth. I would say I'm a novice at best, any help is much appreciated.

brian@DEXTER:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu maverick (development branch)
Release:	10.10
Codename:	maverick

brian@DEXTER:~$ uname -r
2.6.31-11-rt
brian@DEXTER:~$ uname -a
Linux DEXTER 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 12:28:53 UTC 2010 i686 GNU/Linux

- B

---

### Post by cariboo on 2010-09-05
Try running:

```
sudo update-grub
```

to see if that makes a difference.

---

### Post by 7bn on 2010-09-05
I tried it earlier but just to double check.


brian@DEXTER:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-11-rt
Found initrd image: /boot/initrd.img-2.6.31-11-rt
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
done
brian@DEXTER:~$ uname -r
2.6.31-11-rt


I did catch this earlier but the kernel still shows 2.6.31:

brian@DEXTER:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-libc-dev
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 813kB of archives.
After this operation, 8,192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main linux-libc-dev i386 2.6.35-20.29 [813kB]
Fetched 813kB in 4s (195kB/s)                       
(Reading database ... 279891 files and directories currently installed.)
Preparing to replace linux-libc-dev 2.6.35-19.28 (using .../linux-libc-dev_2.6.35-20.29_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up linux-libc-dev (2.6.35-20.29) ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB
------------

Thanks!
- Brian

---

### Post by sawtdk on 2010-09-05
> **7bn said:**
> Did I do something wrong? I thought the kernel would update to 2.6.35-19.28. Do I need to update manually? Upgrade went fairly smooth. I would say I'm a novice at best, any help is much appreciated.

brian@DEXTER:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu maverick (development branch)
Release:	10.10
Codename:	maverick

brian@DEXTER:~$ uname -r
2.6.31-11-rt
brian@DEXTER:~$ uname -a
Linux DEXTER 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 12:28:53 UTC 2010 i686 GNU/Linux

- B

It's because 2.6.31 is the latest real-time kernel in the ubuntu repositories. Also in Maverick.

To install the 2.6.35 generic kernel run "sudo apt-get install linux-generic"

---

### Post by 7bn on 2010-09-05
Thanks! It worked like a champ. I should know that too. :( Appreciate your help. - Brian

---

### Post by 7bn on 2010-09-05
Of course, now that I go to remove it, I see it in the Synaptic Package Manager when I put linux-image in the search field. Hehe

/noob

Thanks again!

---

### Post by ranch hand on 2010-09-05
Yes  I think you want to go to synaptic and remove the old kernels.

Too late, you got it.  Good work.

---

### Post by rtimai on 2010-09-05
ranch hand,

Why should one remove old kernels after upgrading to a beta? Aren't the previous kernels a recovery measure in case the beta fails? Just curious...

---

### Post by 7bn on 2010-09-05
I removed the old to save disk space.

My logic/perspective - either ride it out until a fix is in place or wipe. So far, I've made it through several upgrades without wiping.

---

### Post by cariboo on 2010-09-05
It is recommended that you keep at least one old working kernel, just in case, but I guess most of us that have been here since the toolchain was uploaded usually get rid of old kernels asap, we usually have a fallback install in case things get to the point where the testing version gets unusable  and we can use it to fix problems.

---

### Post by ranch hand on 2010-09-05
> **rtimai said:**
> ranch hand,

Why should one remove old kernels after upgrading to a beta? Aren't the previous kernels a recovery measure in case the beta fails? Just curious...
I have seen folks with kernels in 10.04 that went back to late 8.10.  I have serious doubts that those kernels are going to be good for much.

In this case the kernel might work, but how much good it is going to be, compared to the LiveCD, as a rescue tool I do not know.

I would rather have a little more closely related kernel to attempt recovery with.  The live CD provides that.

I have one kernel back on this install.  Have nothing against it at all.

This is a dev release.  Slide by for a few days with just a Live CD for recovery and you will have, at least, one more kernel.  And that one and the current will be closely related so that hopefully all tools used will be supported by the old kernel.

---

