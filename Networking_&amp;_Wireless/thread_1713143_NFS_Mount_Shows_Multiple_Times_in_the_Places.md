---
title: "NFS Mount Shows Multiple Times in the Places"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by peshko-lnx on 2011-03-23
I have the follwoing fenomenan. In my /etc/fstab I have an entry to automatically mount my NAS. Here is my entry:

192.168.1.10:/mnt/array1/My_NAS    /media/My\040NAS    nfs    _netdev,
auto,rw,hard,users,intr    0    0

When my laptop boots it successfully mounts the NFS NAS and I get an icon "My NAS" on my dekstop that points to the NAS. If I double click on the icon it opens my file browser and I can browse thru my NAS fodlers.

What I see on the left hand side of the file browser is that I have to entries for My NAS. One of it has a button to shows that it is mounted and the other does not.

If I go to Places I also see 2 entries for "My NAS". One of it takes me to browsing the NAS and if I click on the other it says "Unable to mount ... busy or already mounted". Which makes sense.

If I unmount everything and mount everything back, it seems to be ok.

The question is why do I have 2 (two) entries for the same thing?

---

### Post by NertSkull on 2011-03-23
I'm not super familiar with NFS, but I use it.  I don't know what nfs netdev is, I just have mine as nfs

i.e.

```
192.168.1.10:/mnt/array1/My_NAS /media/My\040NAS nfs rw,hard,intr 0 0
```

And I've never had it mount things twice.  That may not help you at all, but I know that works for me at least.

---

### Post by peshko-lnx on 2011-03-24
> **NertSkull said:**
> I'm not super familiar with NFS, but I use it.  I don't know what nfs netdev is, I just have mine as nfs

i.e.

```
192.168.1.10:/mnt/array1/My_NAS /media/My\040NAS nfs rw,hard,intr 0 0
```And I've never had it mount things twice.  That may not help you at all, but I know that works for me at least.

_netdev would basically wait for a network connection before it attempts to mount the NFS.

I just mounted again and same thing. If I click on Places I have My NAS two times...

---

### Post by peshko-lnx on 2011-03-25
Just tested this on a new 10.10 instalaltion with the same problem.

---

### Post by peshko-lnx on 2011-03-25
Anyone?

---

