---
title: "Can't write to my NFS shared folder"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by TheMiz on 2010-02-24
[CENTER]Hi,
[/CENTER]
 I have a MacBook Pro.  I just got it to "mount" the recording/video folders using NFS to connect to my mythbox.

Here is my /etc/exports file:
```
/var/lib/mythtv 192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000)

```Here is my hosts.allow file:
```
portmap: 192.168.0.0/24
lockd: 192.168.0.0/24
rquotad: 192.168.0.0/24
mountd: 192.168.0.0/24
statd: 192.168.0.0/24

```Here is my hosts.deny file:
```
portmap : ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL
```I also made sure that under Settings -> Shared Folders, the "Read-only" box was unchecked.  I did all this and I still cannot get the MacBook to write to the mounted folders.

I would appreciate some help.  Thanks!

---

### Post by suseendran.rengabashyam on 2010-02-24
Hi,

Your settings looks fine.

Enter the folowing command in the terminal

```
sudo ls -ln /var/lib/ | grep mythtv
```

make a note of UID and GID.

If the UID and GID is not '1000', then you need to set the UID and GID to '1000' by entering

```
sudo chown -R 1000:1000 /var/lib/mythtv
```

Hope this helps.

---

### Post by TheMiz on 2010-02-24
Thanks Sus

After I posted, I figured it must be a permissions problem.  Thank you for helping me to fix it easily and painlessly.

---

