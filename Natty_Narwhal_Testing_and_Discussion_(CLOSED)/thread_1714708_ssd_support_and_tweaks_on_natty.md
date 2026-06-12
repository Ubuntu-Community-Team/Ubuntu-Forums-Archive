---
title: "ssd support and tweaks on natty"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ppjose on 2011-03-25
hello

I just bought a computer with a 60GB SSD and a corsair 1TB hard drive and 8GB RAM.

I want to install windows 7 and ubuntu on the SSD.

If I make the partitions with the installer Natty and formatting, will be aligned?

When I install windows and format the partition created with gparted loses the alignment ?

TRIM is enabled by default in the installation on ubuntu?

thank you very much

---

### Post by cariboo on 2011-03-25
I'd suggest you install Windows first, and only create a partition big enough for what you need, and leave the rest of the hard drive space blank. Then when you install ubuntu, you can tell it to use the empty space. You'll have to wait for someone else to chime about ssd's

---

### Post by andrewabc on 2011-03-25
I'd also like to know about SSD support. I've been asking since October 2009 about when/if it will auto proper align, and TRIM enabled by default.

---

### Post by cariboo on 2011-03-25
I don't have one, but from what I've seen in other sub-forums, most people just format the drive and use it.

---

### Post by recluce on 2011-03-25
I am not sure about natty (as it still doesn't install for me), but the most efficient way is probably to make the partition table and first partition  with parted (yes, from the shell) - after that, you should be good to go with any GUI tool (GParted, Natty Installer, Windows installer). You can google or use the forum search to find a lot of information on using parted to align a SSD. If you need further help, post your SSDs erase block size and I will try to help.

If you already installed something, "fdisk -lu" might tell you something. If your first partition start at block 63, you are NOT aligned. Otherwise, do the math (your logical block size, block number(s) your partition(s) start at) and see if every partition starts at a multiple of your SSDs erase block size.

The "secret" with SSDs is that you really want your partitions and block size to align with the SSDs erase block size. If you don't align, many write operations will actually need to read two physical blocks, modify the logical block that spans two physical blocks and erase/write the two physical blocks. Your SSDs performance will take a huge hit, less than half as fast on writes as advertised should be about right. Also, you will have additional wear by causing additional writes.

More on SSDs and alignment here:

[http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux](http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux) 


Also, you want to enable TRIM in your fstab entries. With trim, the kernel will "tell" the SSD which logical blocks are no longer in use, so the SSD can erase those blocks during idle times - writing to an empty block is much more efficient than overwriting a block that has data in it. With "normal" file system behaviour, the drive never knows that a block is no longer in use until it gets overwritten.

Here is a sample from my fstab:

```

# / on /dev/sda2 (SSD)
UUID=87f60bce-cc20-4631-986f-bb159c3ce34c /               ext4    errors=remount-ro,noatime,nodiratime,discard 0 1

```

"discard" enables trim
"noatime" and "nodiratime" disable access time stamps on files and directories - and thus reduce unnecessary writes to your SSD.

Note that trim is available only with 2.6.35 kernels and later (so NOT in "stock" Lucid) and I know that ext3 and ext4 support TRIM. reiserfs, ntfs-3g and many other filesystems do not support TRIM. I am not sure about ext2 and btrfs.

**BTW: even some mechanical hard drives now need alignment, namely "advanced format" drives that have physical 4kB sectors but emulate 512B sectors to the outside world (like the popular WD20-EARS or WD20-EALS drives, aka 2.0TB Caviar Green)**

---

### Post by MacUntu on 2011-03-26
Just install Windows 7 and then Ubuntu. For TRIM to work, you'll have to add the 'discard' mount option in '/etc/fstab' yourself ('noatime' will reduce writes, so add it too, but there's no need for 'nodiratime', which is automatically enabled when setting 'noatime').

---

### Post by glaze on 2011-03-26
> **recluce said:**
> 
"noatime" and "nodiratime" disable access time stamps on files and directories

You don't need "nodiratime" if you enable "noatime".

---

### Post by ppjose on 2011-03-26
hello (sorry for my bad English)

thanks for responding.

addition to the partition table, I read something about format partition to change the value of the stride and stripe, with SO installers do not need it?:

> Intel SSDs with an erase block size of 128 (or 512 KiB -- Intel isn't quite straightforward with this, see the comments section for a discussion on the subject - if anyone from Intel is reading this, help us out! ) that are not part of a software RAID:
-E stride=32,stripe-width=32

OCZ Vertex SSDs with an erase block size of 512 KiB that are not part of a software RAID:
-E stride=128,stripe-width=128

Normal hard drives that are not part of a software RAID
trust the defaults

Any software RAID:
-E stride=raid chunk size / file system block size,stripe-width=raid chunk size x number of data bearing disks

I will install Windows 7 first in a first partition, and then install ubuntu creating a partition with the remaining size of the ubuntu installer (natty)

at the end I do a fdisk-lu and post here the result.

Thanks

---

### Post by plun on 2011-03-26
> **MacUntu said:**
> Just install Windows 7 and then Ubuntu. For TRIM to work, you'll have to add the 'discard' mount option in '/etc/fstab' yourself ('noatime' will reduce writes, so add it too, but there's no need for 'nodiratime', which is automatically enabled when setting 'noatime').

Yep, I am using both discard and noatime in my fstab.

I followed this guide last year when I bought my Intel SSD

[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux)


To also move the Firefox cache to tmp is an extra bonus with SSD......;)

On the 3rd page:
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/3/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/3/)

**6. Move Firefox cache to a tmpfs**


Just great with an SSD-disk.....:D

(boot-time often below 10 seconds)

---

