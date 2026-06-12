---
title: "Mount windows share."
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by CyberRascal on 2010-01-23
Hey,

I'm having trouble mounting a windows share. In windows I just click "Map network resource to disk" or something like that and write the address - \\server\share. No password or anything.

Using ubuntu, I tried adding this line to fstab:

//server/share           /mnt/win      smbfs   defaults        0       0

Is this correct? Since I don't need a password in windows, I shouldn't need user credentials here right? How would I go about finding the log about the mounting attempt?

Thanks.

---

### Post by CyberRascal on 2010-01-24
Since I'm on page 4 with no replies, I thought I would bump this.. Sorry.

---

### Post by umechanism on 2010-01-24
I dual boot Vista/Ubuntu 9.10 on the same machine.  I wanted to have access to the Windows side of the hard drive from Ubuntu so I mounted the Windows partition by entering this line of code in my /etc/fstab file:

```
/dev/sda3 /mnt/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Where "sda3" is my Windows partition.  I didn't make the string of code up myself...I dug around this forum until I found it so I can't explain to you what all these commands mean.  I can only attest that it works.

---

### Post by Iowan on 2010-01-24
> **CyberRascal said:**
> //server/share           /mnt/win      smbfs   defaults        0       0
CIFS has replaced SMB. [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for mounting CIFS shares.

---

