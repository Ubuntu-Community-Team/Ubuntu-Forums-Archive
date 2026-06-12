---
title: "NAS not showing up under Linux"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by MadsRH on 2012-08-07
Hi

I've have a D-link 320 NAS setup up as a network drive under Windows. My Mac automatically found and mounted the drive in Finder. But under Linux I can't see the drive!

Should I mount the drive? 
Do I need Samba?
Is there a terminal command for displaying if it is connected?

The linux box runs XBMC(buntu)

//MadsRH

---

### Post by MadsRH on 2012-08-08
Bump :(

Is there really no one that can help me?

---

### Post by steeldriver on 2012-08-08
if you are doing this via SAMBA / CIFS you can do

```
smbclient -L *server-name*
```or

```
smbclient -L *server-ip*
```on the client machine to see a list of samba shares from *server*. Or if it is NFS, then try

```
showmount -e *server-ip*
```

---

### Post by MadsRH on 2012-08-08
Exactly what I was looking for - I'll give it a try right away, thanks

---

### Post by MadsRH on 2012-08-08
I've tried to install samba and samba4 and smbtree - What a mess! Tried to remove/reinstall it again, but now I'm getting 

> Errors were encountered while processing:
  samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

With the showmount command I can see the drive now, but still can't access it :-(

---

### Post by steeldriver on 2012-08-08
Well if showmount is seeing the share(s) you should be able to mount them that way if you are stuck with samba (it's a bit more unixy anyway)

For any public shares it should be as simple as making a mount point and then mounting as server:/share e.g.

```
$ showmount -e 192.168.1.127
Export list for 192.168.1.127:
/c/home        *
/c/media       *
/c/public      *
/c/backup      *
/USB/USB_HDD_1 *
 $
$ sudo mkdir -p /mnt/nas-01/public
[sudo] password for steeldriver: 
$ sudo mount -t nfs 192.168.1.127:/public /mnt/nas-01/public
$

```

Hope this helps

---

