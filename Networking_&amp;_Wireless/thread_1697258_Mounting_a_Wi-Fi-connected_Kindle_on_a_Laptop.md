---
title: "Mounting a Wi-Fi-connected Kindle on a Laptop"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by jackn on 2011-02-28
My Kindle is connected to the net by Wi-fi.
Yet, I can't see it on my laptop's filesystem.

When the Kindle is USB-connected, it appears under /media, of course.

When the Kindle is connected by wi-fi, I can browse the net and use the device directly, but I can't manage it from the laptop. This is not very convenient.
I'd like to be able to manage downloading and files off of the laptop.
What can I do?

I guess it is actually connected to the router (part and parcel of my ISP box), and that's why I can't see it on the laptop.
Is that so? 
If so, can something still be done to allow me to handle the Kindle from the laptop when it is connected by Wi-Fi?

Thanks,
Jackn

---

### Post by jackn on 2011-03-01
I've made some progress, I think.

Following a [post]("http://ubuntuforums.org/showthread.php?t=1577362") in these forums with slight modifications, I included Kindle in /etc/fstab as follows:
```
#Kindle3 Device 
UUID=4B62-8102 /media/Kindle vfat noauto,users,rw,umask=007,uid=1000,gid=1000,noexec  0 0
```

When the Kindle is USB-connected to the laptop, it is /dev/dsb1. 
blkid gives:
```
x@x:~$ sudo blkid /dev/sdb1
/dev/sdb1: LABEL="Kindle" UUID="4B62-8102" TYPE="vfat" 
```

When it is wi-fi connected (to the router, I guess), whether 'mount' receives the device name or its UUID, the laptop doesn't see Kindle:
```
x@x:~$ sudo mount -t vfat -U 4B62-8102 /media/Kindle/
mount: no such partition found
x@x:~$ sudo mount -t vfat /dev/sdb1 /media/Kindle/
mount: special device /dev/sdb1 does not exist

```

The Kindle is definitely connected by wi-fi, as indicated by its wi-fi icon and by connectivity.

Is there anything I can do?
Thanks.
Jackn

---

