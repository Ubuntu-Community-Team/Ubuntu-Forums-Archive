---
title: "btrfs - useable?"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Gorlist on 2011-04-24
Hi, wanted to reinstall natty, just wondering what the state of btrfs is, and whether its usable? Allot of searching on the web suggest its still lacking however most of the posts were October time last year and partly testing on 10.10.

Regards!

---

### Post by dino99 on 2011-04-24
[http://ircanswers.com/ubuntu1/563247/can-natty-btrfs-without-workarounds](http://ircanswers.com/ubuntu1/563247/can-natty-btrfs-without-workarounds)

---

### Post by gnomeuser on 2011-04-24
I am using btrfs on my netbook, it is a straight forward install and in use the only things you will notice is a sparse error on boot which is harmless and apt-get due to it's heavy use of fsync() is rather slow. 

It works rather well overall, I am very happy with btrfs at this stage.

---

### Post by RJ12 on 2011-04-24
Is there a reason to use btrfs over ext4? I've only heard of it a few times...

---

### Post by gnomeuser on 2011-04-24
> **RJ12 said:**
> Is there a reason to use btrfs over ext4? I've only heard of it a few times...

It is the filesystem of the future. Already today on btrfs you can use the snapshot feature to save the state of the machine prior to an upgrade, making it possible to rollback in case something broke (requires installation of an additional package but otherwise just works today).

---

### Post by RJ12 on 2011-04-24
> **gnomeuser said:**
> It is the filesystem of the future. Already today on btrfs you can use the snapshot feature to save the state of the machine prior to an upgrade, making it possible to rollback in case something broke (requires installation of an additional package but otherwise just works today).

Sounds cool!

---

### Post by SushiR on 2011-04-26
Just out of curiosity I performed another Natty install. This time I wiped the two partitions of my former main system (Linux Mint Julia - which I only used twice since I installed Natty alpha1 as a test system), and installed the latest daily with both "/" and "home" as btrfs. It worked like a charm, so I decided to step a bit further and also converted my ext4 data partition (around 200 GB). In fact it was easier than I thought (and some instructions described it).

I just ran "btrfs-convert /dev/sda7", which took a while, but not as long as I thought. Then I mounted it, adjusted the fstab, rebooted - and after I saw it all was working as expected, I deleted the snapshot image and...that's it. I was a little bit confused about the "subvolume" thing in fstab, but I figured out I don't need that for the converted partition.

I may fool around with compression, balancing and defragmentation later, but so far I'm very satisfied with how easy this was. I'm waiting to have the already mentioned boot error fixed, which only fault is to extend boot time (it even boots without hitting a button!), but else I haven't encountered any problems yet.

But I must admit - although my netbook is my main device for daily stuff - there is no sensible data involved, and that's the primary reason to dare such thing. For personal fun I strongly recommend at least a little testing of btrfs.

The last thing I have to say: Ubuntu Natty is literally FLYING on my netbook (Samsung N150, 2 GB of RAM), something I've never seen with any Ubuntu release before. And no, I don't think it's because of btrfs, because with ext4 it's almost the same experience...

---

### Post by donniezazen on 2011-04-26
It didn't work for me. I used / and /home as btrfs and installation failed to install bootloader. Did you guys use regular installation method (manual partition) or had to use some tweak.

---

### Post by SushiR on 2011-04-27
> **soham_1207 said:**
> It didn't work for me. I used / and /home as btrfs and installation failed to install bootloader. Did you guys use regular installation method (manual partition) or had to use some tweak.

I also used / and /home as btrfs and installed Grub in the MBR. Worked just fine without any tweaks.

---

### Post by sdowney717 on 2011-04-27
this still true saying grub wont run ?

> Fresh Install on 11.04-beta1 Natty

As of 11.04-beta1, it is possible to use only btrfs file systems with the **caveat that grub _MUST_NOT_ be installed to the boot sector of the btrfs volume** containing /boot. See also Ubuntu Grub2 Bug 757446 and Ubuntu Grub2 Bug 759772. You must install it to either the parent (sda rather than sda1; MBR/Reserved Sectors) _OR_ use a dedicated /boot partition as shown in the following example (in Fresh Install on 10.10 Maverick).

Fresh Install on 10.10 Maverick

Obtain the latest install cd from [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

Do a regular installation except use manual partitioning to create:

    a ext2 or ext3 partition of about 250MB for /boot
    a btrfs partition for /
    a linux swap partition large enough to allow for suspending to RAM (amount of ram plus 100MB is a good size) If you don't need suspend support then not more than 2GB is sufficent. 

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

---

### Post by donniezazen on 2011-04-27
Root btrfs installation worked flawlessly on Lenovo Ideapad s10e but failed to install bootloader (i had to restart to get rid of bootloader installer screen) on Dell Inspiron E1505.

I do get sparse error at boot in my netboot which seems to be innocuous.

---

### Post by donniezazen on 2011-04-27
I tried to install btrfs on my Dell Inspiron E1505 as root but it failed. I get an following error.
>  Executing grub-install /dev/sda failed.
This is a fatal error
Installation aborts and it takes me to Ubuntu Live. I try to install grub but it is not installed. After sudo apt-get install grub it takes me to grub prompt and i get error 15.

I tried other method from another thread which also fails.

> 
sudo mkdir /media/sda5
sudo mount /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda

Initially i got error cfg file too large and when i tried later i got "The file /media/sda5/boot/grub/stage1 not read correctly".

When you guys tried to install what option did you choose at bootloader installation screen and did your installation completed without error. Is there a thread with instruction on how to install grub in this perticular case?

Thanks.

---

