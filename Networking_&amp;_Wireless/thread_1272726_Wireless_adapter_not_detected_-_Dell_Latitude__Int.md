---
title: "Wireless adapter not detected - Dell Latitude / Intel 3945ABG"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by Hibbo on 2009-09-22
Hello hello,

I have a Dell Latitude D830 laptop, with the following WiFi interface built in
```
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
```

I am running Ubuntu 9.04 from a 250GB external HDD, and my wireless works fine.

However, I also have Ubuntu Studio (64bit) installed on another 250GB external HDD, and when I use this version I have no wireless.  Ifconfig doesn't even list it as present.

I have copied the entire /etc/network directory from the working install over to the ubuntu studio install, but it still doesn't work, in fact it has made thing worse as it doesn't even find the wired network adapter now.

The interfaces file contains
```
auto lo
iface lo inet loopback
```

This is sufficient on Ubuntu but not for Ubuntu Studio.

I am writing this from Ubuntu, as I only have wifi internet here......

(It's extra annoying as my package manager doesn't work on this install, so I have one install unupdatable, and another with no internet access, great! [http://ubuntuforums.org/showthread.php?t=1249538](http://ubuntuforums.org/showthread.php?t=1249538) 

Please help!

---

