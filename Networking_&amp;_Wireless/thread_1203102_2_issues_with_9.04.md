---
title: "2 issues with 9.04"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by icubyx on 2009-07-02
Hi,
I have recently installed 9.04 and have the following issues:
1. I can connect fine to WLAN, but compared to Windows, the download speeds crawl. In windows I always get at least 25kbps, but here, the maximum I manage to get is 6kbps. Is it only me or others too face the same problem?

2. For Wired Internet, I use PPPoE from windows and it works fine. But I can't even connect to the LAN from ubuntu. I have tried everything suggested on different places, but there really doesn't seem to be final solution. Somebody suggested it is a kernel bug and kernel updates can solve this. Is it so?

These 2 things stop me from really enjoying using ubuntu...:(

Thanks in advance.

icubyx

---

### Post by superprash2003 on 2009-07-03
post output of ifconfig from the terminal.. is this normal http website downloads or torrent downloads?

---

### Post by icubyx on 2009-07-05
Hi, 
I just shifted to Linux Mint and get the wireless speeds all right. 
About the wired networking, I can now connect to the network, but pppoe doesn't work. I managed to get it working only once last night, and when I replicated the steps, I cannot connect through pppoe today. 
This is the kind of internet connection I have: my provider has an ethernet cable connected at my home, which I plug directly into the computer ethernet port. When I use the wireless router between the comp and the cable, I can connect well. ipconfig output follows in a minute

---

### Post by icubyx on 2009-07-05
eth0      Link encap:Ethernet  HWaddr 00:22:3f:2b:e7:63  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4208 (4.2 KB)  TX bytes:4208 (4.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:d6:7e:a5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fed6:7ea5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41707 (41.7 KB)  TX bytes:29183 (29.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-D6-7E-A5-65-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2009-07-06
which interface connects your wired connection? eth0?

---

### Post by icubyx on 2009-07-11
hi!
Superprash - I use eth0. thanks for taking interest in the problem. 

Solved the problem. I'll need to check if it works after restart too. Here is what I did:
0. Change the MAC address by adding the following (if you need to spoof it) in rc.local like this:
ifconfig eth0 down
ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx
ifconfig eth0 down

1. Install wicd - this replaces the default network manager

2. Set the wired connection to DHCP (even if the windows counterpart is set for static IP in my case)

3. Some bug - probably in Linux Mint I use or Ubuntu does not create the pppoe.conf in /etc/ppp/ Get a sample pppoe.conf from [http://db.glug-bom.org/wiki/index.php/Sample_pppoe.conf_file](http://db.glug-bom.org/wiki/index.php/Sample_pppoe.conf_file). I needed to open the ppp folder as Superuser to be able to copy to it. 

4. Edit the file and change the service provider name in it if you need to use one. Keep the ACNAME as it is if you don't need to provide it. 

5. Run sudo pppoeconf

6. Sudo start-pppoe

7. ping yahoo.com or google.com to make sure you're connected.

You're set. I am currently posting through the same connection...

---

