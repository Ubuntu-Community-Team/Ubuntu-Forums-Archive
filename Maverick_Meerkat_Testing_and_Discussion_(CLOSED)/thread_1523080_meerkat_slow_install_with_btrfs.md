---
title: "meerkat slow install with btrfs"
date: 2010-07-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by gator on 2010-07-03
Ive created a usb install disk of meerkat alternate-i386. I decided to try it on my eeepc-901. On the first SSD i created a 300mb ext2 boot partition and the rest btrfs for root. The other ssd disk is ( 8GB ) btrfs mounted on /home. The install was taking much too long. I stopped the install after 2.5 hours having only reached 34%. The question i have concerns partitioning, do i need to do some kind of block align or something. Why is it so slow?. Lucid with ext4 only took a few minutes to install.

---

### Post by dino99 on 2010-07-03
[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

[http://www.mjmwired.net/kernel/Documentation/filesystems/btrfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/btrfs.txt)

---

### Post by psyke83 on 2010-07-03
> **gator said:**
> Ive created a usb install disk of meerkat alternate-i386. I decided to try it on my eeepc-901. On the first SSD i created a 300mb ext2 boot partition and the rest btrfs for root. The other ssd disk is ( 8GB ) btrfs mounted on /home. The install was taking much too long. I stopped the install after 2.5 hours having only reached 34%. The question i have concerns partitioning, do i need to do some kind of block align or something. Why is it so slow?. Lucid with ext4 only took a few minutes to install.

I recommend you search the Maverick subforum for existing threads on btrfs - others (including myself) have already reported that installation onto btrfs partitions is extremely slow.

---

### Post by xebian on 2010-07-03
I didn't notice anything slow when I installed in a VBox disk.  The only thing that slowed me down was the extra hoops bec I used the live CD.  This is 64-bit btw if it means anything at all.

---

### Post by gator on 2010-07-03
thank you pyske83, but where is this sub forum, i thought this was it? And does the system run good once installed?

---

### Post by psyke83 on 2010-07-03
> **gator said:**
> thank you pyske83, but where is this sub forum, i thought this was it? And does the system run good once installed?

Your thread is already in the proper section (though perhaps it was moved by a moderator?). This is the link: [http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

You can use the "search this forum" link from here, which is very useful when using the development release. If this is the first time you've discovered the development subforum, it's highly recommended that you read the stickies.

As for btrfs itself: I was receiving a lot of checksum warnings in the logs, and performance was simply inadequate for daily usage. I reformatted to ext4.

---

### Post by psyke83 on 2010-07-03
> **xebian said:**
> I didn't notice anything slow when I installed in a VBox disk.  The only thing that slowed me down was the extra hoops bec I used the live CD.  This is 64-bit btw if it means anything at all.

Convering a partition from ext4 to btrfs is quite fast, yes, but it tells you nothing of real btrfs performance.

The slowdown is most noticeable when unpacking and installing packages via the alternate installer directly to a btrfs filesystem. Your installation method bypassed this process entirely (by copying the live image to an ext4 partition, and then converting the ext4 filesystem to btrfs). Manual Installation took ~2 hours (or perhaps longer) on my system, compared to ~15 minutes when using ext4. I've also read some posts from Fedora users noting that yum/rpm installation takes longer via btrfs too.

---

### Post by gator on 2010-07-03
bug reported 

[https://bugs.launchpad.net/ubuntu/+bug/601299](https://bugs.launchpad.net/ubuntu/+bug/601299)

---

### Post by psyke83 on 2010-07-03
> **gator said:**
> bug reported 

[https://bugs.launchpad.net/ubuntu/+bug/601299](https://bugs.launchpad.net/ubuntu/+bug/601299)

Thanks, I added a comment.

---

### Post by xebian on 2010-07-03
> **psyke83 said:**
> Convering a partition from ext4 to btrfs is quite fast, yes, but it tells you nothing of real btrfs performance.

The slowdown is most noticeable when unpacking and installing packages via the alternate installer directly to a btrfs filesystem. Your installation method bypassed this process entirely (by copying the live image to an ext4 partition, and then converting the ext4 filesystem to btrfs). Manual Installation took ~2 hours (or perhaps longer) on my system, compared to ~15 minutes when using ext4. I've also read some posts from Fedora users noting that yum/rpm installation takes longer via btrfs too.

where did you get the idea that I converted an ext4 to btrfs?  This is a direct install to a btrfs / and ext4 /boot all done within the live CD installer.

---

### Post by psyke83 on 2010-07-04
> **xebian said:**
> where did you get the idea that I converted an ext4 to btrfs?  This is a direct install to a btrfs / and ext4 /boot all done within the live CD installer.

I see. I tried installing btrfs on the first day of the announcement on the ubuntu-devel list, and at the time, the daily-live installer did not support btrfs. I wasn't aware that it now works.

Anyway, installing from the livecd is still bypassing the process of unpacking each individual .deb package (instead, it's simply unpacking the single live image, and then performing some small miscellaneous tasks afterwards).

---

