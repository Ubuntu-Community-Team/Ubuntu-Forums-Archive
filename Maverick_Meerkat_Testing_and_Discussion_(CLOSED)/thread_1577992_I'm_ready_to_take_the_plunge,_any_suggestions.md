---
title: "I'm ready to take the plunge, any suggestions?"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by RJ12 on 2010-09-19
Ok, so I was going to install the Maverick Beta about a week or to ago, but there was a bug in NDISWrapper that was causing wireless to not work. Well according to the bug report on launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/613796") it has been sorted out on the daily ISO. So what I was hoping to do was take my current Karmic install and shrink it. Then use the unallocated space to make my self a new root partition. I know that you might be thinking that if I am asking these questions, then I shouldn't be installing an Daily ISO of Ubuntu onto my computer. I have heard that it is very stable and I am running it off of my Live USB as I post this and have not found any problems. Uptime says I have been running for 26 minutes, with no problems. Now here are my current questions

________________________________________________________________Questions________________________________________________
1. Can I shrink my current Karmic install and make a new root partition for Maverick? I was hoping to also name the partition "MAVERICK" (does GRUB hate labels?) so that when I go back and make a clean install of Maverick when it comes out, I don't delete Karmic.

2. I hope to be "Triple" Booting Windows 7, Karmic, and Maverick, will GRUB show me all of my OSes? 

3. I currently have Karmic's GRUB in control, will Maverick's take control and work the same? I don't want to have a "GRUB" mess.

4. Am I asking to much? I will have an attachment of `sudo fdisk -l` in this post, so if there is anything I am about to mess up. 

5. Do you have any suggestions on what I am about to do? I have heard they got a new installer (so this is the second new installer in this release :)  ) from the beta, is this installer even a fraction stable? I am using today's build (using zsync) so that is what LiveUSB I am using.

Edit: So the installer is not new, it just has a new slideshow

Thanks




sudo fdisk -l


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb7b6216

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       16480   130835456    7  HPFS/NTFS
/dev/sda3           16481       29345   103338112+   5  Extended
/dev/sda4           29346       30402     8479744    7  HPFS/NTFS
/dev/sda5           16481       16865     3092481   82  Linux swap / Solaris
/dev/sda6           16866       29345   100245568+  83  Linux

Disk /dev/sdb: 2022 MB, 2022702592 bytes
63 heads, 62 sectors/track, 1011 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005590e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1011     1974452    c  W95 FAT32 (LBA)

``` 


Thanks!

:)

---

### Post by kouter on 2010-09-19
Here ya go,

#1 - Yes, you can use gparted to do this.  sudo apt-get install gparted

#2 - Grub and Mav installer will take care of setting up your triple boot.

#3 - You can choose not to install Grub with Maverick, but that will involve some extra steps to get it listed and recognized from Karmic's Grub.  If you don't care, Maverick will re-write the boot sector and will list all OS's it detects (Windows, Karmic, and Maverick)

#4 - Besides splitting Karmic's root partition, you really won't be changing the partition table.  You'll be able to use the same swap space and you really don't need much space for an Ubuntu install - I keep my root under 20GB and have a separate /home partition that is roughly 100GB.

#5 - Be patient.  If you haven't tested beta's before, then make sure to read bug reports and other documentation as there are still quite a few things to be worked out.  I'm still experiencing serious kernel crashes, problems with laptop battery, and some touchpad problems (no right-click).  Even with the consideration that this is a beta, Karmic (IMO) is the most complete, most working release to date.

Hope that helps.

---

### Post by mikewhatever on 2010-09-19
Maveric is still a beta for a reason, it's not stable yet.
> Uptime says I have been running for 26 minutes, with no problems.
That's yet another reason why you shouldn't install it.

---

### Post by RJ12 on 2010-09-19
So I can label the Maverick partition without any trouble? When I resize Karmic, will that mess it up? Also is it possible to access Karmic files from Maverick? I probably won't need to do that though and it would probably be hard with permissions. I thank you for your words about being patient, I want to be able to help Canonical and the community by testing the newest release and reporting bugs. Unfortunately I have not encountered any anomalies, but if I do I will report it here and on Launchpad. Although I must warn you, I have a Launchpad account, but have never filled a bug so I will need you guy's help with that. I will be installing soon! Although I will be disconnecting from the Internet because I heard there is a bug with the installer where it wants to get stuff and it hangs.

---

### Post by kouter on 2010-09-19
> **mikewhatever said:**
> Maveric is still a beta for a reason, it's not stable yet.

That's yet another reason why you shouldn't install it.

I'd be happy to get 1 minute without a bug....

---

### Post by 23dornot23d on 2010-09-19
Mine for the record has been running pretty well for the last hour using ...
Linux keith-laptop 2.6.35-22-generic #32-Ubuntu SMP Wed Sep 15 23:39:25 UTC 2010 i686 GNU/Linux

The last month has been pretty reasonable .... upto where the graphics stopped working
between around 16 to 20 generic. mainly due to the xorg 1.9 issue.

Sound still does not work properly and I have to edit a file .....

But everything else I use 3D wise seems reasonable ..... 
compiz conky and cairo-dock work well together too ...... looking forward to the full release.

Oh ..... I did have one incident earlier where a USB drive shut down for no apparant reason ...... 
( I am wondering if this was a power management issue , but no idea how to check it  I was using QCAD at the time it went off with Blender and Wings3D running plus firefox with about 26 tabs open ...... )

All rebooted again ok though ..... only 25 days 
(edit date was wrong on my machine after latest install lols 20 days that link says for me now - and we are there ..... ;)

Just had the USB die on me again straight after writing this .... went off at 1:03 and 2:10 ..... its lasting roughly an hour and
then just shuts itself down ..... its not even warm .... so its not overheating .... weird ..... will see if it happens in another hour.

Will check the logs too ....

---

### Post by RJ12 on 2010-09-19
Well, I am going to go start installing. The counter on [my]("http://techkid.digitaldojos.com") website says 21 days though? 

Wish me luck!

---

### Post by RJ12 on 2010-09-19
Well I have successfully installed! I am loving it!!


Thanks everyone:KS

---

### Post by 23dornot23d on 2010-09-19
Best of luck .... (boot loader is the only thing I ever worry about .... but that seems to be a lot better nowadays :grin:

Wow that was fast well done ..... I was a bit late at wishing you the best .... but its good to hear its ok

---

### Post by RJ12 on 2010-09-19
> **23dornot23d said:**
> Best of luck .... (boot loader is the only thing I ever worry about .... but that seems to be a lot better nowadays :grin:

Wow that was fast well done ..... I was a bit late at wishing you the best .... but its good to hear its ok


Thanks! I usually am worried about the boot loader, silly me!

---

### Post by KegHead on 2010-09-20
Hi!

I've used 10.10 on a dell mini9 for about a week w/o issues.

Sounds like the same for you.

KegHead

---

