---
title: "Wired network problem"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by kiritisai on 2013-03-12
I've installed ubuntu 12.04 but and everything went on fine. But my wired connection is not functioning properly, where as it is working fine in windows. So, are there any drivers that I shld install? My wireless is working absolutely fine.

---

### Post by chili555 on 2013-03-12
We won't know until you tell us, from the terminal:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by kiritisai on 2013-03-12
I got the following as the output ...  03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)

---

### Post by chili555 on 2013-03-12
Your device uses the relatively new driver *alx*. You could install 12.10, update the kernel to 3.5.0-24 and have it perfectly. Or, if you love pain, do this: [http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx](http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx) See post #4. I'd substitute this package: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2)

---

### Post by kiritisai on 2013-03-13
hey.. thank you very much chili55 .. U are awesome man. I was really facing a lot of trouble without this wired network connection. By the way, You are from?? I'm from India. :)

---

### Post by chili555 on 2013-03-13
> **kiritisai said:**
> hey.. thank you very much chili55 .. U are awesome man. I was really facing a lot of trouble without this wired network connection. By the way, You are from?? I'm from India. :)Glad it's working! For my location, see *Location* above. I have a few good friends in India.

---

