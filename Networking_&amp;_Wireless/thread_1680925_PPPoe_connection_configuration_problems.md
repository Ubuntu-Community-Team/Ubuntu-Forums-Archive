---
title: "PPPoe connection configuration problems"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by Vorac on 2011-02-03
Hi!
I am having trouble with a newly installed Ubuntu 10.10 Maverick. And I am new to Linux.

The story:
I installed Ubuntu 10.10 64-bit on a 80 GB HDD partitioned as follows: 16GB swap, 16MB boot, 35GB System(ext4) 30GB (ntfs) - for future windows installation. Typing sudo pppoeconf I managed to connect ot the interent. The connection failed several days later, with the Network connections icon disappearing from the taskbar(upper right corner of the screan). I booted from the USB stick - the network connections manager reported "Wired conenction disconencted". I could not connect to the internet thereafter.

Here are some of the things I have tried:

```
vorac@Strahil:~$ sudo pppoe -I eth0
[sudo] password for vorac: 
pppoe: Timeout waiting for PADO packets

		  &#9474; I found 1 ethernet device:							   
		  &#9474; eth0													  
		  &#9474;														   
		  &#9474; Are all your ethernet interfaces listed above?			
		  &#9474; (If No, modconf will be started so you can load the card  
		  &#9474; drivers manually).									   
		  &#9474;														
		  &#9474; Or press ESC to abort here.							  
		  &#9474;														 
		  &#9474;														  
		  &#9474;			   <Yes>				  

 Sorry, I scanned 1 interface, but the Access			 
		  &#9474; Concentrator of your provider did not respond. Please	 
		  &#9474; check your network and modem cables. Another reason for   
		  &#9474; the scan failure may also be another running pppoe	   
		  &#9474; process which controls the modem.

vorac@Strahil:~$ sudo ifup -a -v
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant


&#65279;vorac@Strahil:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

vorac@Strahil:~$ ping -c 5 209.85.227.103
connect: Network is unreachable


ubuntu@ubuntu:~$ sudo ifconfig 
eth0	  Link encap:Ethernet  HWaddr 00:25:22:3a:b8:d8  
		  inet6 addr: fe80::225:22ff:fe3a:b8d8/64 Scope:Link 
		  UP BROADCAST MULTICAST  MTU:1500  Metric:1 
		  RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
		  TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
		  collisions:0 txqueuelen:1000 
		  RX bytes:0 (0.0 B)  TX bytes:852 (852.0 B) 
		  Interrupt:43 Base address:0x8000 

lo		Link encap:Local Loopback  
		  inet addr:127.0.0.1  Mask:255.0.0.0 
		  inet6 addr: ::1/128 Scope:Host 
		  UP LOOPBACK RUNNING  MTU:16436  Metric:1 
		  RX packets:56 errors:0 dropped:0 overruns:0 frame:0 
		  TX packets:56 errors:0 dropped:0 overruns:0 carrier:0 
		  collisions:0 txqueuelen:0 
		  RX bytes:4032 (4.0 KB)  TX bytes:4032 (4.0 KB) 

ubuntu@ubuntu:~$ ping -c 5 209.85.227.103 
connect: Network is unreachable 

When running from the USB-stick Ubunto shows an icon Wired Connection: Disconnected – you are now offline.
```

The internet fee is payed, so I assume the problem is not by the ISP. Please give me some advice.

PS: The system behaves in the same way even with the HDD disconnected.

---

### Post by dineshs on 2011-02-04
Why dont you try the DSL tab in Network manager ?
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by Vorac on 2011-02-05
Thank you for your answer, **dineshs**. After trying to fix the problem for a week, today I come home, power the computer on, and google opens up (I am writing from the machine now). I guess the problem was not at my home - should the problem return, however, I will try your advice.

Wellcome to me on Ubuntu :)

---

