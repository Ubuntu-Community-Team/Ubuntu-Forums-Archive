---
title: "m202e mp3 player needs help working please"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by pneaveill on 2007-09-19
I have scanned several forums for this particular issue in hopes of finding something, but alas this is not to be.

Here is the scoop: My wife gave me an RCA m202e mp3 player for a late anniversary present and cannot figure out how to get it to install on dapper media machine. As can be seen below, can see it there in the posts, but cannot see it from the desktop or other areas (even from cold boot) -- unless I am looking at something wrong.

What I have learned is this if anyone can help from here.

lsusb
```

Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 005: **ID 069b:0731 Thomson, Inc. **
Bus 002 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 
```here is dmseg | grep sd
```

[17179671.248000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179736.280000] SCSI device sda: 124096 2048-byte hdwr sectors (254 MB)
[17179736.284000] sda: Write Protect is off
[17179736.288000] sda: Mode Sense: 3e 00 00 00
[17179736.288000] sda: assuming drive cache: write through
[17179736.300000] SCSI device sda: 124096 2048-byte hdwr sectors (254 MB)
[17179736.304000] sda: Write Protect is off
[17179736.304000] sda: Mode Sense: 3e 00 00 00
[17179736.304000] sda: assuming drive cache: write through
[17179736.308000]  sda: sda1
[17179736.320000] sd 1:0:0:0: Attached scsi removable disk sda
[17179736.340000] sd 1:0:0:1: Attached scsi removable disk sdb
[17179736.420000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179736.420000] sd 1:0:0:1: Attached scsi generic sg1 type 0
```

---

### Post by pneaveill on 2007-09-20
After a rough night's sleep, I went back through some posts from others. Here is where I am at currently -- all entries were made from root (if this helps anyone) :

```

sudo mkdir /media/M202E
sudo mount -t vfat /dev/sda1 /media/M202E

gedit /etc/fstab
```I was able to access the "free" test songs on there, but could not remove them or add my own. So I did both of the following separately (of course)

```

chmod 655 /media/M202E
chmod 777 /media/M202E

```

I can now see M202E icon on the desktop and can see it in "Places" but says this:

```

"/media/M2...eshot.mp3" cannot be deleted because you do not have permissions to modify its parent folder. 
```

Now to just get the old files off and the new ones on . . . 

Anyone have ideas on how to do this?

---

