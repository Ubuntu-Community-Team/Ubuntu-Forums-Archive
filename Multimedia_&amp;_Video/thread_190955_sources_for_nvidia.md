---
title: "sources for nvidia"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by davi on 2006-06-06
hi everyone!

i'm trying to install the binary driver from nvidia (the version that ubuntu comes with doesn't work very well with my card); but i need my kernels sources.

i try:
```
prieta@prieta:~$ sudo apt-get install linux-source-`uname -r` Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-source-2.6.12-10-386
prieta@prieta:~$

```

but no sources.  i tried looking online for them, but i can't seem to find them.

how can i get my sources so i can install the nvidia binary driver.

thank you

---

### Post by bikeboy on 2006-06-06
Not 100% sure on this but I think it's the "linux-headers" package you need. That's what I used when setting up vmware.

---

### Post by tseliot on 2006-06-07
Try my guide, please:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

