---
title: "btrfs Installations Ready for Testing"
date: 2010-06-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-06-21
With basic support in GRUB2 for booting btrfs filesystems in place, btrfs installations are now ready for testing through the manual partitioning mechanism in the installer.
 
Below is [Colin Watson]("https://launchpad.net/~cjwatson")'s [call for testing]("https://lists.ubuntu.com/archives/ubuntu-devel/2010-June/030918.html") to the [ubuntu-devel mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel"). I have emphasized some key points in bold.

[QUOTE=Colin Watson]With current daily builds of Maverick, you should be able to perform installations with a btrfs root filesystem.  This is still **NOT RECOMMENDED FOR PRODUCTION USE and MAY EAT YOUR DATA**, but **we're making the option available by way of manual partitioning only** so that we can experiment with btrfs more easily, contribute fixes to various tools as needed (as we've already done with grub2 in order to at least get this minimal level of support in place), and the like, and hopefully to encourage some more people to get involved in its development.

**You cannot yet use btrfs for /boot** (although we're working on this), so you'll need to create an ext3 or similar /boot filesystem. I assume
anyone able to use an experimental filesystem can cope with doing that in the installer's manual partitioner.

Please file bugs as you encounter them!  I expect that ext4 will remain the default filesystem for Maverick, but btrfs is doing a lot of things
that are interesting for us down the line, so the sooner we can help to iron out problems with it the better.[/QUOTE]

---

### Post by jfernyhough on 2010-06-22
I'm going to suggest interested people have a read through this howto: [http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279)

I used it a couple of weeks ago and the only difficulty I had was remembering to reinstall the kernel after repartitioning to include a /boot partition.

Currently I'm set of with ext2 /boot, btrfs /, and ext4 /home. Everything seems to be working as expected (and certainly more stable than back when I tried reiser3).

---

### Post by psyke83 on 2010-06-22
> **jfernyhough said:**
> I'm going to suggest interested people have a read through this howto: [http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279)

I used it a couple of weeks ago and the only difficulty I had was remembering to reinstall the kernel after repartitioning to include a /boot partition.

Currently I'm set of with ext2 /boot, btrfs /, and ext4 /home. Everything seems to be working as expected (and certainly more stable than back when I tried reiser3).

Yes, but a great deal of that tutorial will not apply when testing the latest Maverick builds.

The manual partitioning section is useful to illustrate how to set up a /boot partition, but the rest of the instructions on creating/converting a btrfs filesystem will not apply (since the procedure is carried out within the graphical installer). Sections pertaining to GRUB2 and initramfs modifications should also be ignored. 

I hope that people will keep such things in mind.

---

### Post by donniezazen on 2010-06-22
> **jfernyhough said:**
> I'm going to suggest interested people have a read through this howto: [http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279)

I used it a couple of weeks ago and the only difficulty I had was remembering to reinstall the kernel after repartitioning to include a /boot partition.

Currently I'm set of with ext2 /boot, btrfs /, and ext4 /home. Everything seems to be working as expected (and certainly more stable than back when I tried reiser3).

Do we have to go through this How to? Is Btrfs available as one of the way to format the drive in drop down menu with ext4/ext3/ext2/ntfs, etc? If yes. Is it ok to format /, /home and swap as Btrfs and proceed to regular install? Besides advanced features are there other features like speed, etc.?


Thanks.

---

### Post by psyke83 on 2010-06-22
I booted a daily-live image from yesterday (21st), and discovered that Ubiquity does not support  btrfs installations. From reading Colin Watson's post I had assumed that when he mentioned "manual partitioning", he was referring to the manual partitioning option within Ubiquity's interface. I was mistaken.

With no other option, I set up a new installation with separate /boot and / filesystems (both ext4), then followed the first step of ibuclaw's tutorial to convert my / filesysten to btrfs. This worked, but once I mounted and chrooted into the filesystem, I received segmentation faults upon making any changes to the filesystem (such as editing /etc/fstab).

Well, to cut a long story short - the call for testing appears to have meant the alternate (i.e., daily, and not daily-live) image. The debian-installer (from today's daily image, at least) has an option to format btrfs directly, which is what I am trying right now.

---

### Post by psyke83 on 2010-06-22
> **soham_1207 said:**
> Do we have to go through this How to? Is Btrfs available as one of the way to format the drive in drop down menu with ext4/ext3/ext2/ntfs, etc? If yes. Is it ok to format /, /home and swap as Btrfs and proceed to regular install? Besides advanced features are there other features like speed, etc.?


Thanks.

Aside from the segmentation fault I received from following the tutorial, there are other reasons why you may want to reconsider using btrfs...

I'm still installing via the alternate daily image onto a fresh btrfs partition, and the unpacking stage is much slower than ext4. I've performed many installations on this machine, so I can easily notice the difference in speed.

Edit: installation completed after about 1hour 30 minutes; a typical install from the alternate image to a stable filesystem (ext3/4) usually takes 15 minutes on this machine...

---

### Post by donniezazen on 2010-06-24
Is btrfs only for / partition?

---

### Post by LKjell on 2010-06-24
> **soham_1207 said:**
> Is btrfs only for / partition?

Anything except /boot

---

### Post by VH-BIL on 2010-06-24
Is there any advantage in using it over EXT4?

---

### Post by psyke83 on 2010-06-24
> **VH-BIL said:**
> Is there any advantage in using it over EXT4?

If you want to test and help fix bugs, yes. If you're looking for better performance, etc., it depends. On my system it feels quite slow, but other benchmarks indicate that it offers slight improvements over EXT4 (and even better improvements when compression is enabled).

This may be helpful: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1010_btrfs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1010_btrfs&num=1)

---

### Post by donniezazen on 2010-06-24
There are no alternate CD on cdimages.ubuntu.com. Can you write alternate CD to usb stick like live CD?

---

### Post by psyke83 on 2010-06-24
Performance is incredibly bad on my system with btrfs. 

At this moment I'm installing 57 updates (60mb). User/system CPU usage doesn't exceed 15% or so, but iowait is maxed and the system is incredibly laggy. Even as I write this message, there is a delay between typing and seeing the characters rendered on-screen. The updates began installing 15 minutes ago and still haven't finished.

How can I begin to troubleshoot this?

---

### Post by psyke83 on 2010-06-24
> **soham_1207 said:**
> There are no alternate CD on cdimages.ubuntu.com. Can you write alternate CD to usb stick like live CD?

Yes, it appears that the images aren't available... weird.

When they re-appear, you will be able to boot the alternate image from USB as long as you add the following to the kernel boot line:
```
cdrom-detect/try-usb=true
```

If you don't do that, debian-installer will get stuck at the cdrom detection stage. The daily image from the 23rd also didn't install the full system properly (it only installed the base packages). I had to manually install ubuntu-desktop from terminal (after importing the packages from the cd image manually).

If you're not experienced with alternate installs, I really don't recommend that you try this at the moment (unless you're prepared for some trial and error, as well as a few headaches).

---

### Post by donniezazen on 2010-06-24
> **psyke83 said:**
> Yes, it appears that the images aren't available... weird.

When they re-appear, you will be able to boot the alternate image from USB as long as you add the following to the kernel boot line:
```
cdrom-detect/try-usb=true
```

If you don't do that, debian-installer will get stuck at the cdrom detection stage. The daily image from the 23rd also didn't install the full system properly (it only installed the base packages). I had to manually install ubuntu-desktop from terminal (after importing the packages from the cd image manually).

If you're not experienced with alternate installs, I really don't recommend that you try this at the moment (unless you're prepared for some trial and error, as well as a few headaches).

Thanks.

---

### Post by gnomeuser on 2010-06-24
Once full grub2 support lands this is going to be great. I know it is a big work and I just want to express my thanks to the people doing it. I can't wait to test it.

I am currently aiming to wait for the full support then upgrade and use the btrfs migration instructions from the btrfs wiki after a backup. That just seems like the most fun. Not to mention the least effort if it works considering that I use a custom environment.

---

### Post by ranch hand on 2010-06-24
> **gnomeuser said:**
> Once full grub2 support lands this is going to be great. I know it is a big work and I just want to express my thanks to the people doing it. I can't wait to test it.

I am currently aiming to wait for the fll support then upgrade and use the btrfs migration instructions from the btrfs wiki after a backup. That just seems like the most fun. Not to mention the least effort if it works considering that I use a custom environment.
I do not know where you guys come up with this stuff.  What in flinderation is fll?

---

### Post by gnomeuser on 2010-06-24
> **ranch hand said:**
> I do not know where you guys come up with this stuff.  What in flinderation is fll?

My apologies, a mere typo. Naturally it was meant to say "full support".

---

### Post by psyke83 on 2010-06-24
> **gnomeuser said:**
> Once full grub2 support lands this is going to be great. I know it is a big work and I just want to express my thanks to the people doing it. I can't wait to test it.

I am currently aiming to wait for the full support then upgrade and use the btrfs migration instructions from the btrfs wiki after a backup. That just seems like the most fun. Not to mention the least effort if it works considering that I use a custom environment.

When I converted my ext4 partition to btrfs, it seemed to convert properly (with no errors), and I was able to remount the partition as btrfs successfully, but any attempt to write to the filesystem triggered a kernel crash. 

I would suggest that you make a full  backup of your partition before converting (whenever you decide to jump in ;)).

---

### Post by ranch hand on 2010-06-24
> **gnomeuser said:**
> My apologies, a mere typo. Naturally it was meant to say "full support".
Thanks.

I now feel really silly after running a number of searches for fll that just didn't turn up anything useful at all.  At least I now know why.

I really should know a typo when I see one.  They are something I am particularly good at.

I just figured it was my non fluent status when it comes to the language "geek" that needs a dictionary in Ubuntu.  Not this time I guess.

---

### Post by donniezazen on 2010-06-26
> **psyke83 said:**
> When they re-appear, you will be able to boot the alternate image from USB as long as you add the following to the kernel boot line:
```
cdrom-detect/try-usb=true
```


Where is this kernal boot line added?

Thanks.

---

### Post by psyke83 on 2010-06-26
> **soham_1207 said:**
> Where is this kernal boot line added?

Thanks.

I'm not sure if this exists on Maverick daily images, but if you see the graphical menu screen (similar to [this screenshot]("http://www.psychocats.net/ubuntu/images/alternatetextmode.png") from an earlier release), simply press the F6 key and append the text.

I created the USB image with unetbootin (which creates a custom boot  menu [like this]("http://www.raymond.cc/images/unetbootin-boot-menu.png")), so the procedure was different to the above. In my case, I  highlighted unetbootin's "Default" profile, pressed the tab key to edit,  appended the text and pressed return to continue booting.

---

### Post by donniezazen on 2010-06-26
I am trying btrfs file system. I am using Alternate CD (on a USB stick) for installation. I made 500 MB /boot, 8 GB /, 2.5 GB Swap and rest /home. The problem is its been 2 hours and installation is still going on. Installation has not stuck but its been really slow. Is this normal?

---

### Post by scradock on 2010-06-26
> **psyke83 said:**
> 

When they re-appear, you will be able to boot the alternate image from USB as long as you add the following to the kernel boot line:
```
cdrom-detect/try-usb=true
```

If you don't do that, debian-installer will get stuck at the cdrom detection stage. 

That's an interesting trick! Is there anything similar that can be used to boot from a USB stick using a BIOS that doesn't offer the USB boot option?

---

### Post by gnomeuser on 2010-06-27
> **soham_1207 said:**
> I am trying btrfs file system. I am using Alternate CD (on a USB stick) for installation. I made 500 MB /boot, 8 GB /, 2.5 GB Swap and rest /home. The problem is its been 2 hours and installation is still going on. Installation has not stuck but its been really slow. Is this normal?

That is normal, installation onto a btrfs partition can take much longer than other filesystems, I am unsure of the exact reason but I have heard this reported before.

---

### Post by psyke83 on 2010-06-27
> **scradock said:**
> That's an interesting trick! Is there anything similar that can be used to boot from a USB stick using a BIOS that doesn't offer the USB boot option?

In the case of booting a Linux system, you would first need to find a way to boot the kernel from another bootable source. This page should help you: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by psyke83 on 2010-06-27
> **soham_1207 said:**
> I am trying btrfs file system. I am using Alternate CD (on a USB stick) for installation. I made 500 MB /boot, 8 GB /, 2.5 GB Swap and rest /home. The problem is its been 2 hours and installation is still going on. Installation has not stuck but its been really slow. Is this normal?

If you read my previous posts, you'll see that our experience is identical.

I'm also seeing a lot of messages in the kernel logs about btrfs checksum mismatches. Considering that btrfsck doesn't actually repair filesystem errors yet, I'm glad that I only installed this filesystem onto my spare hard drive.

---

