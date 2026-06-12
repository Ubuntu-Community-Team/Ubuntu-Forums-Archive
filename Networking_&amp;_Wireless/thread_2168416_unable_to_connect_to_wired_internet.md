---
title: "unable to connect to wired internet"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by captaincactuz on 2013-08-17
Hello, I just built a new computer and installed ubuntu 12.04 . everything seems to be working fine but I am unable to connect to the internet (wired). Any advice?

THankss

---

### Post by mikewhatever on 2013-08-17
I'd advise elaborating quite a bit on why you are "unable to connect to the internet". At least tell us why not, ...not to mention the relevant hardware specs.

---

### Post by captaincactuz on 2013-08-17
This is my motherboard : [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130686](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130686)

I have the ethernet cable plugged in and yet no connections appear.
manny@manny-MS-7751:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19392 (19.3 KB)  TX bytes:19392 (19.3 KB)

---

### Post by mikewhatever on 2013-08-23
It says the LAN chipset is "Killer E2205", so you might want to google that.
Here is a similar thread [http://ubuntuforums.org/showthread.php?t=2003542](http://ubuntuforums.org/showthread.php?t=2003542).

---

