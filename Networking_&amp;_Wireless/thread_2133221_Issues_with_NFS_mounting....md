---
title: "Issues with NFS mounting..."
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by sjaglin on 2013-04-07
Hi,

I have a NAS with a NFS shared folder on my network. Usually I set up my machines by installig nfs-common and adding the following to fstab:

```
# Mount of Brehat
192.168.1.50:/share/Archives  /home/stephane/Brehat   nfs rsize=8192,wsize=8192,timeo=14,intr

```

I did that on my new machine (lenovo thinkpad), it worked for a couple of days and now the system refuses to mount my NFS folder:


```
stephane@stephane-ThinkPad-T410:~$ sudo mount 192.168.1.50:/share/Archives /home/stephane/Brehat 
mount.nfs: requested NFS version or transport protocol is not supported
stephane@stephane-ThinkPad-T410:~$
```

I didn't install anything new or did anything different on that new machine, it is a straight forward install of Ubuntu 12.04 LTS. My other machines (an Asus eee and an Asrock ION) both run Ubuntu and I set them up this way and mount my NFS folder with no issues.

Can anyone help me with that?

Cheers,

Stef:confused:

---

### Post by MakOwner on 2013-04-11
Do you have the NFS client installed?

```

dpkg -l | grep nfs
ii  libnfsidmap2                    0.25-1ubuntu2                NFS idmapping library
ii  nfs-common                      1:1.2.5-3ubuntu3.1           NFS support files common to client and server

```

It may not look exactly like that but you shoudl at least see nfs-common if you want to mount NFS export from another source.

---

### Post by sjaglin on 2013-04-12
Hi,
yes it's sorted, in fact it was a problem with my NAS, a reboot and tada! the nfs mount came back, 

Thanks anyway!

---

