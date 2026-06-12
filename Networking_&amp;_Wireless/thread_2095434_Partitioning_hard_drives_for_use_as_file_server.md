---
title: "Partitioning hard drives for use as file server"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by triglyph on 2012-12-16
I have Ubuntu 12.04 set up as a file server for a network that includes Mac and Windows 8 computers. I have settled on NTFS, which works fine with the Mac Lion (I can read and write files) and works sometimes on Windows (one out of 4 of them works, the others don't).

A couple of problems:

1. Everytime I format/partition a drive, it says "The partition is misaligned by xxx bytes [varies]. This may result in poor performance. Repartitioning is suggested."  I repartition and the same happens.

2. Should I format as Master Boot Record, GUID, Don't Partition or Apple Partition Map?

3. Should I partition or leave the drive as "Free"

4. Windows can read one of the hard drives, but not others. As of now, I have not figured out what is different about the one that does work.

5. Any ideas on why Windows 8 can access some of the partitions but not others? Windows tells me I don't have permission but won't let change partitions.

Any suggestions?

---

### Post by triglyph on 2012-12-16
I tried ext4 formatting for the Linux drives and it seems to work. I didn't try this before because everything I had read on the net said that ext4 wouldn't work with Mac or Windows. I'm surprised to find that you shouldn't believe everything you read on the internet. After all that's how World War I got started.

Any hidden traps I should look for as I continue to experiment with ext4 as the format for my Linux server?  I still have one hard drive that won't allow access on Windows (although it works fine on the Mac). I'm reviewing to see what setting is wrong for that.

One problem I'm still having is that when I restart the Linux server, the drives do not appear on the other computers on the local net until they are opened on the desktop of the Linux computer. Any way to shortcut this?

---

### Post by ahallubuntu on 2012-12-16
> **triglyph said:**
> I tried ext4 formatting for the Linux drives and it seems to work. I didn't try this before because everything I had read on the net said that ext4 wouldn't work with Mac or Windows.

That is correct - they can't read ext4.  But they aren't seeing ext4 over the network - they are seeing a Windows share.  The connected clients don't care what format the drive itself is in, as long as the server can understand it.

> **triglyph said:**
> One problem I'm still having is that when I restart the Linux server, the drives do not appear on the other computers on the local net until they are opened on the desktop of the Linux computer. Any way to shortcut this?

You can add them to your /etc/fstab file to mount them automatically at startup.  Careful, though: if these are external drives and they aren't plugged in upon boot, you WON'T be able to boot - you'll get an error.  If these are internal drives, no problem, you can assume they'll always be plugged in.

To test your fstab file after you edit it, on the Ubuntu server type:

```
sudo mount -a
```

If that returns without error (without doing anything), then your fstab file has no errors.  Again - if one of the mounted devices is an external drive, it WON'T BOOT if you put one of those drive's partitions in your fstab file unless it is plugged in.

Do some googling on instructions for editing an fstab file if you don't know how to do it.

---

