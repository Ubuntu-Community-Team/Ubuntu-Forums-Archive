---
title: "Can't share folder on a different hard drive than root"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by Aitaix on 2010-02-02
I'm having trouble sharing a folder on a different hard drive other than root. I can share a folder such as /home/username/music fine.

I have samba installed with visible shares and read/write access.
Ubuntu 9.10 32bit

Thanks

---

### Post by dmizer on 2010-02-02
> **Aitaix said:**
> I'm having trouble sharing a folder on a different hard drive other than root. I can share a folder such as /home/username/music fine.

I have samba installed with visible shares and read/write access.
Ubuntu 9.10 32bit

Thanks

Is there an entry for the drive in /etc/fstab? If not, you'll have to make one before you can share it with the proper permissions.

Take a look here if you're not sure how to accomplish that: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by Aitaix on 2010-02-03
The drive is already formatted and partitioned already to ntfs, so I skipped the first few paragraphs from the link you provided. 

From the paragraph where it says to mount the drive. It says to add in a line to edit fstab for an ext3 filesystem and another for a fat32 file system. My drive is ntfs..what do I add in then?


```

aitaix@Gokart:~$ sudo chown -R aitaix:aitaix /media/Media
chown: cannot access `/media/Media': No such file or directory

```



I tried also tried to manually mount the drive, this is what I got:
```

aitaix@Gokart:~$ sudo mount /dev/sdb1 /media/Media
fuse: failed to access mountpoint /media/Media: No such file or directory

```

What am I doing wrong here?

---

### Post by dmizer on 2010-02-03
Try this: [http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig](http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig)

---

