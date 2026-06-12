---
title: "copy from network stalls"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by nixIT on 2010-05-05
Hello all,

I was previously running Ubuntu 9.04, with no problems, however since installing 10.04 this past weekend, I noticed a problem today.

We have a NetApp FAS250 at work, formatted as CIFS filesystem so our windows users can access it.  With 9.04 I had no problem ready and writing to the shares.

Today, I tried to copy some files from one folder to another and the "File Operation"  dialog came up with 0 bytes of 2.8MB -- 0 seconds left (0 bytes/sec).  However, no files are being copied.

I closed the dialog and tried again, same thing.

After a reboot I tried to copy files off the share to my hard, same thing, the dialog would just sit there.

After another reboot, I tried to copy files from my hard drive to my hard drive (different folder), that works fine, and copying from my hard drive to the network works fine.  Just not from the network.  Any idea?

here are the 2 mappings in my FSTAB:

```

//192.168.0.16/homedrive /mnt/hdrive cifs credentials=/home/nixit/.creds,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0
//192.168.0.16/c$ /mnt/fas250 cifs credentials=/home/nixit/.creds,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0

```

I did a system update today, and many things updated.  Any idea what can be wrong?

--nixIT

---

### Post by nixIT on 2010-05-06
anyone?  Is anyone else having these issues?

--nixIT

---

### Post by nixIT on 2010-05-06
Update,

I connected to one of our windows servers and was able to copy files to and from the server with no problem.  Any idea what could be causing the problem with the netapp FAS250?

--nixIT

---

### Post by nixIT on 2010-05-06
when I connect to the drive, by opening Nautilus, and in the address bar, I type:

```

smb://192.168.0.16/homedrive

```

enter in my login creditions, everything works like it should, however, when I mount the share via fstab:

```

//192.168.0.16/homedrive /mnt/hdrive cifs credentials=/home/nixit/.creds,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0

```

I can't seem to copy files from the share.  I'm not sure how the two are different when the drives are mounted.  

Can anyone help out?

--nixIT.

---

### Post by nixIT on 2010-05-12
I am still having this issue, nothing I try seems to work.

Any info on why a smb://<network IP>/<network share> works when the FSTAB entry does not?

any help is greatly appreciated.  

--nixIT

---

### Post by nixIT on 2010-05-14
Ugg, no luck on this issue.

I'm giving up on it, spent 3+ solid days searching and trying numerous things all ending with the same results, not working.  :(

--nixIT

---

