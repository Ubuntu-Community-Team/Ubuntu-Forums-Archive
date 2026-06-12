---
title: "ubuntu 9.10 smbmount not showing anything"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by EvansFive on 2009-11-09
I just have successfully completed an upgrade from 9.04 to 9.10, had just a few little hassles!

One thing I can't get working is mount a samba share.

I have a shared USB disk ETCSharedMusic attached to an Apple Time Capsule.

Under 9.04 I executed the following command:

smbmount //10.1.1.3/etcsharedmusic /home/peterevans/ETCSharedMusic -o credentials=/home/peterevans/Scripts/smblogin.txt

If would mount fine and I could navigate the various folders etc.

NOW....

Under 9.10 when I execute the above command, if I try to view folders on the share there is nothing to be found (the mount completes).

BUT...

If I use "connect to server" from the gui I can see the folders fine.

Does anyone have a workaround this problem please?

---

### Post by EvansFive on 2009-11-09
anybody help me please?

---

### Post by dmizer on 2009-11-10
Try this:
```
smbmount //10.1.1.3/etcsharedmusic /home/peterevans/ETCSharedMusic -o noserverino,credentials=/home/peterevans/Scripts/smblogin.txt
```

---

### Post by EvansFive on 2009-11-10
Thanks for your help, that worked perfectly!

---

### Post by lmarsh on 2010-02-14
> **dmizer said:**
> Try this:
```
smbmount //10.1.1.3/etcsharedmusic /home/peterevans/ETCSharedMusic -o noserverino,credentials=/home/peterevans/Scripts/smblogin.txt
```
Thank you dmizer. This problem also occurred for me after upgrade to 9.10.

In fact, the solution for me just required  -o noserverino

lmarsh

---

