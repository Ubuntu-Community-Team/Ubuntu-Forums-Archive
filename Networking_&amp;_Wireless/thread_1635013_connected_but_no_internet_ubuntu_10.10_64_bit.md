---
title: "connected but no internet ubuntu 10.10 64 bit"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by moukie997 on 2010-12-01
Hi I have lynksys wrt54g-tm modem and lyksys usb.  I can connect via etho and usb but no internet.  any ideas?  This is my first time trying ubuntu.  I use static Ip but none of the numbers I selected are shown here.  (I see 101, but all the numbers I selected in my setup are greater than that)

```
eth0      Link encap:Ethernet  HWaddr 00:30:67:0b:fe:51   
           inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
           inet6 addr: fe80::230:67ff:fe0b:fe51/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:74 errors:0 dropped:0 overruns:0 frame:0
           TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:9759 (9.7 KB)  TX bytes:46847 (46.8 KB)
           Interrupt:42 Base address:0x6000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:708 errors:0 dropped:0 overruns:0 frame:0
           TX packets:708 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0  
           RX bytes:68481 (68.4 KB)  TX bytes:68481 (68.4 KB)
 

 wlan0     Link encap:Ethernet  HWaddr 00:21:29:ea:cd:48   
           inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
           inet6 addr: fe80::221:29ff:feea:cd48/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:977 errors:0 dropped:0 overruns:0 frame:0
           TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:105356 (105.3 KB)  TX bytes:8103 (8.1 KB)
```

---

### Post by lrgmmc on 2010-12-01
how exactly did you setup static ip's? did you also set up the dns values as well?

---

### Post by moukie997 on 2010-12-01
thanks for the reply.  I set up the dns routes through my linksys administrator settings (192.168.0.1 in case I am not clear.. im a newbie to terminology)  .  I set up 3 dns numbers greater than 100.  I see the last 3 digits listed above as .101, that is not a number that I entered as a dns. 

I also tried setting dhcp manually and automatically from within various locations, unselected the ipv4 and 6 as being mandatory conditions, ran some script that I saw online regarding rcv keyrings.

---

### Post by gordintoronto on 2010-12-01
A lot easier to take defaults than force something when you don't know the terminology. If you're going to set DNS servers manually, you should use actual DNS servers, such as 8.8.8.8 and 8.8.4.4

---

### Post by moukie997 on 2010-12-01
> **gordintoronto said:**
> A lot easier to take defaults than force something when you don't know the terminology. If you're going to set DNS servers manually, you should use actual DNS servers, such as 8.8.8.8 and 8.8.4.4


I followed a port forwarding guide for my modem  that was simple enough so that I could use bitcomet and world of warcraft.  I will default to simplify but these settings work for my win 7.

---

### Post by lrgmmc on 2010-12-02
i would go with defaults such as gordintoronto said. you can tell your linksys to lease ip address forever. that will help in giving each of your computers the same ip each time. then setup port forwarding to those ips.

---

### Post by moukie997 on 2010-12-03
I am now on the internet and very pleased.  It seems as though i needed to reset my linksys modem using the button in the rear of the modem.  I had been trying to reset my modem by unplugging for 10 seconds but for some reason that didn't work.  After this all i needed to do was hit the button on the front of my modem to send out a signal for easy wireless set up and it was easy from there.

---

