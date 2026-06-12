---
title: "I GOT SAMBA WORKING!!! Um, now what?"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by Donny Bahama on 2010-03-03
OK... I've heard so much about how hard it is to get Samba working. Following [this nice procedure]("http://howtoforge.com/ubuntu-home-fileserver-p3"), I didn't have much trouble, but now that it's working, and I can access the share from a Windows machine, I find that I now have the following questions...

1. Windows accesses this share very nicely. I have full permissions as a guest user (which is just how I want it.) But from an Ubuntu machine, when I go to Places > Network and navigate through to the server, clicking on the shared folder returns an "Unable to Mount" error. How do I access a Samba share from a Linux client?
2. The procedure that I used mounted the drive as one big share... access the share, then open a directory (backup, music, pictures, movies, etc.) But that's not really how I want it. I'd rather have multiple shares - one for each of those top level directories. How do I go about this?
3. Right now, I've mounted one big NTFS partition, but I'd much rather use LVM and be able to easily grow/shrink (for example) my music partition as necessary. But when setting up Samba shares, how do you reference the individual logical volumes? (All I can see is the disk identifier for the physical partition where the logical volume group resides.)

Thanks for reading!

---

### Post by johnson.d on 2010-03-03
> 1. Windows accesses this share very nicely. I have full permissions as a guest user (which is just how I want it.) But from an Ubuntu machine, when I go to Places > Network and navigate through to the server, clicking on the shared folder returns an "Unable to Mount" error. How do I access a Samba share from a Linux client?

You can access the samba share by mounting it in a directory this can be done by using the following command:

$ sudo mount -t cifs //<ip-address>/<share-name>/ /<mount-point>/ -o user=<user-id>


> 2. The procedure that I used mounted the drive as one big share... access the share, then open a directory (backup, music, pictures, movies, etc.) But that's not really how I want it. I'd rather have multiple shares - one for each of those top level directories. How do I go about this?

You can have multiple shares by adding separate entries for each of the folders you need to share.The entry looks like this: 

[<Share-name>]
path = /<path of the share>
browseable = yes
read only = no


> 3. Right now, I've mounted one big NTFS partition, but I'd much rather use LVM and be able to easily grow/shrink (for example) my music partition as necessary. But when setting up Samba shares, how do you reference the individual logical volumes? (All I can see is the disk identifier for the physical partition where the logical volume group resides.)

For creating LVM partitions you can look into the following link:

[http://manpages.ubuntu.com/manpages/karmic/man8/lvm.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/lvm.8.html)

After creating the LVM partition, you can mount it by using the following command:

$ mount -t <file-system> /dev/<Volume-group-name>/<Logical-volume-name> /<mount-point>

Now you can create a share entry of the mount-point in the smb.conf file.

---

### Post by Donny Bahama on 2010-03-03
Thank you, Johnson, for the thorough response! I'll try to absorb all this and post follow-up questions as I encounter them.

---

