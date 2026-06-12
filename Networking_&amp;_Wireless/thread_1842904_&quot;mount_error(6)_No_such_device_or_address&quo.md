---
title: "&quot;mount error(6): No such device or address&quot; when mount a Samba server in LAN"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by sliter on 2011-09-12
**Command i use:**
/# mount -t cifs 192.168.31.66:/mnt/samba /mnt -o username=root,password=password

**The result:**
mount error(6): No such device or address

**My smb.conf:**
[global]
        security = user
[samba]
        path = /mnt/samba
        read only = yes
        guest ok = yes
        create mask = 0755
        browseable = yes

I've googled for hours but no solution yet. Anyone have encounter the same problem?:confused:

Thanks in advance

---

### Post by 2F4U on 2011-09-12
I think you need to place "//" in front of the IP address.

---

### Post by Morbius1 on 2011-09-12
Replace:
> cifs 192.168.31.66:/mnt/samba /mntWith this:
> cifs //192.168.31.66/samba /mnt

Note: /mnt/samba on the server is the correct path to the target folder being shared but that's not the way you specify it on the client. On the client it's specified by share name.

---

### Post by sliter on 2011-09-13
Thanks Morbius1,

That's solved my problem~~~;)



> **Morbius1 said:**
> Replace:
With this:


Note: /mnt/samba on the server is the correct path to the target folder being shared but that's not the way you specify it on the client. On the client it's specified by share name.

---

### Post by infomaster on 2013-03-09
Thanks

---

### Post by QIII on 2013-03-09
This is a very old thread.

If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

Thanks.

*Thread** closed.***

---

