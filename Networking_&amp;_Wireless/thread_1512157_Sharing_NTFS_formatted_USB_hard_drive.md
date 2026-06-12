---
title: "Sharing NTFS formatted USB hard drive"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by sevesteen on 2010-06-17
I'm trying to get my wife moved to Ubuntu.  Her box is currently dual boot XP/10.4, and she has a large USB hard drive, formatted NTFS about half full of data.  Under XP, this drive is shared, and available to our other computers, a laptop running 10.4, and two netbooks running Jolicloud.  


The current fstab entry for that drive is essentially:
#Entry for /dev/sdb1 :
UUID=123412341234	/media/bigdrive ntfs-3g	defaults     0 0

In a sudo'd Nautilus, media/bigdrive shows as shared, owned by root, with owner, group and others having folder access of create and delete files, and all 3 file access showing "--", not changeable via the GUI.  It does not show as shared in nautilus if not using sudo. I have also tried fstab with WIFE as the owner, create and delete for everyone, and was still not able to make it visible via network. 

I've installed the apache bits that personal file sharing requires, and tried sharing a folder owned by WIFE.   

I can ping in both directions, and connectivity to the internet works.  Clicking on "network" on my computer shows "WIFE's public files on wifecomputer", but clicking on that gives an error dialog,  unable to mount location  DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus).  I can read and write to the public folder on my laptop from Wife's computer. 

What's the easiest way (other than booting XP) that I can get this drive to be visible from the other Linux-based computers, while remaining available via USB if I boot into XP? I've read a bunch of threads on this, and not been able to sort the wheat from the chaff.

---

