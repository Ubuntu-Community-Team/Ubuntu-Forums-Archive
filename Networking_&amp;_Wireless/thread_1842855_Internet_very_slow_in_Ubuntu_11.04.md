---
title: "Internet very slow in Ubuntu 11.04"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by cha0s619 on 2011-09-12
Hi
 

 My rig
 

 Mobo: Gigabyte GA-M61SME-S2
 RAM: 1gb Kingston KVR 667Mhz D2N5
 Internet: 20Mbps connected via 100Mbps wired LAN (using onboard LAN)
 CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
 OS: Ubuntu 11.04 32bit


Output of "uname -a":


                                  ```
ubuntu@ubuntu-desktop:~$ uname -a
Linux ubuntu-desktop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux
```
 


                                  So I installed this system on the 6th of September and the internet was working as it should. Gradually it became slower and slower until yesterday when the speed is like dial-up and many pages just time out. It's the same when downloading via the software center, torrents or whatever. I know it's not an ISP issue because my roommates are getting the full 20Mbps while I'm getting 20kbps.
 

 I'm sure it's not an issue with my on-board lan because I tried a usb wireless adapter and it's still slow. But it works fine on my roommates pc who is running win7. The problem is also affecting all browsers,  I tried 4.
 

 I went digging around (on the excruciatingly slow connection) and turns out many people are having similar issues with Natty Narwhal. I tried turning off ipv6 as suggested here: [COLOR=#000080]_[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)_[/COLOR] ; but to no avail. I even tried changing TCP packet sizes as suggested elsewhere (can't remember the link) which resulted in a barely noticeable improvement but no where near what my connection should be. I've also tried changing DNS settings and still nothing. Please help!




                                  Here is the output of 'ifconfig':


                           ```


ubuntu@ubuntu-desktop:~$ ifconfig
 

 eth0      Link encap:Ethernet  HWaddr 00:1a:4d:7b:68:b0   
 

           inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
 

           inet6 addr: fe80::21a:4dff:fe7b:68b0/64 Scope:Link
 

           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
 

           RX packets:20055 errors:8143 dropped:0 overruns:0 frame:8124
 

           TX packets:22141 errors:0 dropped:0 overruns:0 carrier:0
 

           collisions:0 txqueuelen:1000  
 

           RX bytes:13477069 (13.4 MB)  TX bytes:3333947 (3.3 MB)
 

           Interrupt:41 Base address:0xe000  
 

 

 

 lo        Link encap:Local Loopback   
 

           inet addr:127.0.0.1  Mask:255.0.0.0
 

           inet6 addr: ::1/128 Scope:Host
 

           UP LOOPBACK RUNNING  MTU:16436  Metric:1
 

           RX packets:501 errors:0 dropped:0 overruns:0 frame:0
 

           TX packets:501 errors:0 dropped:0 overruns:0 carrier:0
 

           collisions:0 txqueuelen:0  
 

           RX bytes:15001 (15.0 KB)  TX bytes:15001 (15.0 KB)
 

 

 

 ubuntu@ubuntu-desktop:~$ ifconfig
 

 eth0      Link encap:Ethernet  HWaddr 00:1a:4d:7b:68:b0   
 

           inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
 

           inet6 addr: fe80::21a:4dff:fe7b:68b0/64 Scope:Link
 

           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
 

           RX packets:20109 errors:8156 dropped:0 overruns:0 frame:8137
 

           TX packets:22183 errors:0 dropped:0 overruns:0 carrier:0
 

           collisions:0 txqueuelen:1000  
 

           RX bytes:13507379 (13.5 MB)  TX bytes:3341185 (3.3 MB)
 

           Interrupt:41 Base address:0xe000  
 

 

 

 lo        Link encap:Local Loopback   
 

           inet addr:127.0.0.1  Mask:255.0.0.0
 

           inet6 addr: ::1/128 Scope:Host
 

           UP LOOPBACK RUNNING  MTU:16436  Metric:1
 

           RX packets:502 errors:0 dropped:0 overruns:0 frame:0
 

           TX packets:502 errors:0 dropped:0 overruns:0 carrier:0
 

           collisions:0 txqueuelen:0  
 

           RX bytes:15030 (15.0 KB)  TX bytes:15030 (15.0 KB)

```                                 I did it twice and noticed that the errors in RX packets is increasing. Not sure what that means though.

---

### Post by cap10Ibraim on 2011-09-12
do you have more than one kernel ?

---

### Post by cha0s619 on 2011-09-12
I think so, I'm not sure. I haven't installed an extra one. When I search for "linux-image" in synaptic the following packages are installed:

Package | Installed version | Description

linux-generic-image | 2.6.38.11.26 | Generic Linux kernel image

linux-image-2.6.38-8-generic | 2.6.38-8.42 | Linux kernel image for version 2.6.38 on x86/x86_64

linux-image-2.6.38-11-generic | 2.6.38-11.48 | Linux kernel image for version 2.6.38 on x86/x86_64

for all 3 the installed version is the latest.

---

### Post by praseodym on 2011-09-12
Check the mtu-value of your ISP and replace "Automatic" in the NM with the number, see Rx-package errors

---

### Post by cap10Ibraim on 2011-09-12
when grub loads if you have more than one kernel try starting a different one and test you issue

---

### Post by cha0s619 on 2011-09-12
> **praseodym said:**
> Check the mtu-value of your ISP and replace "Automatic" in the NM with the number, see Rx-package errors

Can you provide more details, sorry I'm still noobish to linux

> **cap10Ibraim said:**
> when grub loads if you have more than one  kernel try starting a different one and test you issue

I'm not getting a grub menu, after POST ubuntu just loads.

Thanks for the responses.

---

### Post by nm_geo on 2011-09-12
> **cha0s619 said:**
> Can you provide more details, sorry I'm still noobish to linux



I'm not getting a grub menu, after POST ubuntu just loads.

Thanks for the responses.

Hold down SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.

---

### Post by benthenk on 2011-09-13
my laptop have same proble with u. my spec is core i7 mem 4gb, hd 750gb. today i instal ubuntu because i'm boring with windows. but after i istall ubuntu 11.04 than i go browsing somtime's i get server error. i don't usually get this problem in win 7. my some one can help us please. and i run many aplication is more slow than win 7 why? thank you for answer please?

---

### Post by cha0s619 on 2011-09-14
I tried pressing shift and it says for a moment that grub is loading but then it just boots up as usual without giving me the grub menu. I'm guessing that grub sees only one kernel and loads it automatically without showing the menu?

---

### Post by praseodym on 2011-09-14
Try to press SHIFT repeatedly.

---

### Post by cha0s619 on 2011-09-14
> **praseodym said:**
> Try to press SHIFT repeatedly.

Yeah repeatedly pressing loaded Grub. Also, loading a different kernel certainly helped. I was getting 6-7Mbps for my 20Mbps on a speedtest, not that much relative to the total but alot better than the 50kbps I was getting earlier. Dunno how long this will last because past solutions didn't last a s well. Anyway, I've had it with Natty Narwhal (I've been getting stability issues with Adobe Flash as well when viewing certain video sites) and I'm getting Lucid Lynx 10.04. Hope the install goes without a hitch.

Thanks for the help

---

### Post by cap10Ibraim on 2011-09-14
is this your download speed or your browsing speed ?

---

### Post by cha0s619 on 2011-09-15
Download speed, according to my ISPs Speedtest web app.

---

