---
title: "cannot write to my ipod anymore"
date: 2009-05-21
forum: Multimedia Software
---

### Post by flevosap on 2009-05-21
hello,
since one day i have this strange problem.
In kubuntu when i mount my ipod with the dolphin file manager i can only mount it without write access.
Also it is not mounted in /media anymore but in a dir called "/tmp/ipodLY0QpW".

When i try to unmount it with dolphin i get this message saying: "org.freedesktop.Hal.Device.Volume.NotMountedByHal: Device to unmount is not in /media/.hal-mtab so it is not mounted by HAL"
But i can unmount the ipod at the command line with "sudo eject /dev/sdc2"

I really don't know where to start so maybe someone knows how to solve this problem

eelco

---

### Post by Paul41 on 2009-05-21
Have you tried mounting it yourself to see if that works?

```
sudo mount /dev/sdc2 /media
```

---

### Post by flevosap on 2009-05-21
thanks for your reply,
Yes i did, but i still don't have write permissions.

---

