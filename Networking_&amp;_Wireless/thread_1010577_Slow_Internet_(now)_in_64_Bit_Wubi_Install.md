---
title: "Slow Internet (now) in 64 Bit Wubi Install"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by mickbw on 2008-12-13
Hi,

I did a fresh install of Windows Vista and then did a new wubi install of 8.10 on my Dell Inspiron 1501 laptop using the restricted Broadcom wireless driver.  I did the 64 bit install of Ubuntu 8.10 and at first could browse through Firefox at a fast rate (if a little slower than on Windows.)

I had some trouble setting up a kvpnc connection to a Cisco vpn (which I understand may be related to the 64 bit version of Ubuntu.  As part of my troubleshooting I changed my dns settings from OpenDNS to the Comcast DNS settings.

Since that point browsing has slowed down to a crawl.  I tinstalled the 3.1 beta and Epiphany but the results did not change.  I also switched the Router Settings back to the OpenDNS, resetting the router and cable modem but this also did not work. 

Any suggestions on how to proceed or should I bite the bullet and reinstall.

---

### Post by mickbw on 2008-12-14
It would appear I might have found a solution by manually clearing the DNS cache:

First of all: install ncsd
```
 sudo aptitude install nscd
```

After ncsd is installed:
```
 sudo /etc/init.d/nscd restart
```

AND
```
sudo /etc/init.d/networking restart
```

I then logged out & back in.  
Woot!!!!  Faster Firefox

---

### Post by superprash2003 on 2008-12-14
how about setting opendns servers in ubuntu itself..

---

