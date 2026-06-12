---
title: "sshfs stalls my nautilus"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by modjoa on 2010-11-07
Hello guys,
Currently I am using Ubuntu 10.10 on my laptop and use to following command to mount the HDD from my home PC:

```
sshfs myhomeuser@my.home.ip:/ ~/Desktop/home_PC
```

and I unmount the drive by:
```
fusermount -u ~/Desktop/home_PC
```

It works fine without any problems, BUT if I disconnect the network cable or go out of the Wi-Fi range, my Ubuntu(more specifically nautilus) hangs up, because the drive from sshfs is not accessible.
If I try to umounted at that moment it gives me this message:

```
umount: /home/ulaptop/Desktop/home_PC: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```
If I plug the network cable again, everything continues working normally.

It seems that there is a problem with fuse or something else goes wrong or I am missing some fundamentals about drive mount operations...

Any ideas? :confused:

---

### Post by TSJason on 2010-11-08
Hello,

Unplugging the network cable is akin to yanking out a harddrive while the machine is running with respect to mounted partitions.

Try using a "lazy" umount. For instance:


```
umount -l ~/Desktop/home_PC

```

It still might take a moment for the system to recover but I think it should work.

---

### Post by modjoa on 2010-11-08
Thanks for the solution, but it doesn't make any difference. :/

1. Still, If I am browsing this folder and the network connection is disrupted, the Nautilius continues to stall. The nautilius is recovered, only when the connection is recovered. 

2. The "System Monitor" in my Gnome Panel does not work any more (as it happens before). It does not matter whether I am browsing the folder or not;

Is there another way than sshfs to attach a network drive through ssh whitout causing me any troblems?

---

