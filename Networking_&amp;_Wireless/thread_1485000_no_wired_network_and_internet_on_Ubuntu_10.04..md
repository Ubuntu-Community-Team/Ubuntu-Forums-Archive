---
title: "no wired network and internet on Ubuntu 10.04."
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by Normunds Slisans on 2010-05-16
Hi,
2 days ago I installed a fresh Ubuntu 10.04 system. After first boot no wired network was found and no access to internet. However, in network connections there is eth0 present. All settings are as should be - IPv4 is in automatic mode and IPv6 - Ignore. I tested internet from another machine with Windows on it and internet connections is ok. I checked etc/network/interfaces and there is as follows:
auto lo
iface lo inet loopback

Please help to solve this issue. Thank you for your assistance.

---

### Post by dineshs on 2010-05-16
please post the output of
```
ifconfig -a
```

---

### Post by Normunds Slisans on 2010-05-16
Tried ifconfig -a
Here is the result:
eth0 
Link encap: Ethernet HWaddr 40:61:86:01:72:5a
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes;0 (0.0 B)
Interrupt:27 Base address:0x2000

lo
Link encap: Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:366 errors:0 dropped:0 overruns:0 frame:0
TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:27852 (27.8 KB) TX bytes:27852 (27.8 KB)

---

### Post by dineshs on 2010-05-16
You can try configuring IP manually in NM.

---

### Post by Normunds Slisans on 2010-05-16
It would be worth to try but  am not sure what to type in DNS Servers and search domains under IPv4.:)

---

### Post by dineshs on 2010-05-16
You can use 4.2.2.1 as DNS,search domain -nil

---

### Post by Normunds Slisans on 2010-05-16
Thanks. Is there any other information to be added?

---

### Post by Normunds Slisans on 2010-05-16
Dineshs, thank you. I tried but it still does not work. If you have any other ideas let me know.

---

### Post by dineshs on 2010-05-17
After configuring NM manually can you ping default gateway?
also pl post result of
```
lshw -c network
```

---

### Post by Normunds Slisans on 2010-05-17
Not sure how to manually configure network. What information do I have to enter? I have never experienced this problem before. In Karmic Koala all was ok - installed it on several machines and it worked without a problem. 
I start to think maybe there is a driver issue???

---

### Post by Normunds Slisans on 2010-05-19
After unsuccessful attempts to fix the network connection I decided to switch back to Karmic Koala. I did a clean install and it works fine. :guitar:

---

### Post by zryder94 on 2010-05-19
I am having a very similar problem..
10.04, and my ifconfig -a is:

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:e1:f1:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:384909 (384.9 KB)  TX bytes:0 (0.0 B)
          Interrupt:34 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9881 (9.8 KB)  TX bytes:9881 (9.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:5c:b7:5c  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe5c:b75c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:786516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1125670377 (1.1 GB)  TX bytes:41737558 (41.7 MB)
          Interrupt:16 


Thanks for the help guys.

---

### Post by larytet on 2010-05-29
In my case DNS was missing. I had static IP configured before upgrade from 9.04 to 10.04.
Ifconfig and route did not report any immediately obvious problems - ifconfig showed IP address set.

Ping to 208.67.222.222  or 208.67.220.220 (OpenDNS) worked
```

ping 208.67.222.222
ping 208.67.222.222

```


I added above IPs to the file /etc/resolv.conf and got Internet working

```

namespace 208.67.222.222
namespace 208.67.222.222

```

---

### Post by vitothegreat on 2010-07-23
I'm having a quite similar problem, though my wired and wireless connections were both fine since the initial installation. 
Recently after rebooting my laptop it began to fail. I can see a Network Manager tray icon with a red exclamation mark (wired is set to automatically connect and wireless is always turned off). However I can still connect to wireless, but wired is grayed out and not functioning.
I also have a Win7 installation dual-booted on the same hdd and all connections work just fine, it also works in Puppy booted from a USB flash drive and it even works in other Linux distros on VirtualBox.

EDIT:
After a lot of fiddling with the settings and testing I found out that my wired network isn't working at all, I can only connect to wireless. So apparently the problem is my modem or ISP.

EDIT2:
I found out that wired connection worked fine on another computer, so clearly the problem was NIC of my laptop. Though the solution looks quite strange but it worked, so if you're having problems with your laptop NIC try this:
-unplug AC;
-remove battery;
-press and hold power button for 15s;
-put the battery back in;
-plug into AC;
-restart.

I found it somewhere on the Internet and the guy explained that the trick is draining flea power. Hope it helps someone.

---

### Post by Bile on 2010-07-29
Hi, 

Just tried the "unplug-battery-and-hold-powerbutton" trick and indeed, **it works!!!**

Still a mystery why I didn't have to do that to get it to work in Win 7.. :s

---

### Post by Bile on 2010-07-29
Hi, 

Just tried the "unplug-battery-and-hold-powerbutton" trick and indeed, **it works!!!**

Still a mystery why I didn't have to do that to get it to work in Win 7.. :s
> 
-unplug AC;
-remove battery;
-press and hold power button for 15s;
-put the battery back in;
-plug into AC;
-restart.

---

### Post by endofline on 2010-07-29
hi , i'm wonder if this can work on 10.10 also, as my wifi signal always give ridicolous sign (full wave) but cant get connected even nearby point which can normally connect via Windows.

thx in advance

---

### Post by vitothegreat on 2010-07-29
> **endofline said:**
> hi , i'm wonder if this can work on 10.10 also, as my wifi signal always give ridicolous sign (full wave) but cant get connected even nearby point which can normally connect via Windows.

thx in advance
The trick I mentioned before will work on any machine as it is hardware related, not software (you drain flea power from your motherboard).
However, your problem is more likely to be related with drivers, Linux have always had hard times with wireless... In addition, don't forget 10.10 is still in alpha phase, so it explains quite a lot :)

---

### Post by mohammedsaqib_2006 on 2011-07-06
Same problem
Pls help
[http://ubuntuforums.org/showthread.php?t=1794578](http://ubuntuforums.org/showthread.php?t=1794578)

---

