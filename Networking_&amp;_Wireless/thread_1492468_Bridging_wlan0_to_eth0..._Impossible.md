---
title: "Bridging wlan0 to eth0... Impossible?"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by Chuck- on 2010-05-24
New user to the Ubuntu world, and I figured I would jump in head first with a fresh OS install. So..., In windows its simply My Computer/Network Connections/ highlight wireless and wired connections/ click bridge connection. I am on about almost 72 hours (im not <snip>ing you I was up till 4 this morning) trying to figure out this problem. Ive been to thread after thread, but they all seem pretty complicated as far as writing scripts and such, and as far as plugging commands into the Terminal, nothing so far has worked at all. My main goal here is, I am running a desktop with Vista 64bit with a Cisco wireless router 3 rooms  away, and i am connecting wirelessly with my Toshiba Satellite wirelessly/Cat5 to Xbox. Alls I want to do is bridge the connection. Heres my ifconfg -a

chuck@chucks-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:33:cb:a5:81  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8560 (8.5 KB)  TX bytes:8560 (8.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:02:af:0e  
          inet addr:193.169.1.101  Bcast:193.169.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe02:af0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56053919 (56.0 MB)  TX bytes:4307242 (4.3 MB)

---

### Post by Chuck- on 2010-05-25
O, if it matters. Im running Ubuntu 10.4

---

### Post by Chuck- on 2010-05-26
bump

---

### Post by Chuck- on 2010-05-26
bump

---

### Post by Iowan on 2010-05-26
Does this [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page provide any useful information? [Here]("http://www.linuxquestions.org/questions/debian-26/howto-bridge-wireless-and-wired-network-interfaces-369455/") is another article to review.

---

### Post by Chuck- on 2010-05-27
That link did help, Thanks! BUUT, even though the bridge is connected between eth0 and wlan0 my Xbox still cannot connect to Xbox live. Is there something special I need to do if im bridging to an Xbox instead of a computer?

---

### Post by Chuck- on 2010-05-27
Ok so the ICS page helped me bridge the connections, BUT thats it as far as the XBOX comes along I used this ([http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN](http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN)) page to get me connected to the "Network" between my laptop and my Xbox. I still cannot connect to Xbox LIVE yet because of DNS problems.

---

### Post by Chuck- on 2010-05-27
Ok heres my remediation: I went into my linksys router and opened ports 88 and 3074. and the Protocol type was BOTH. Then my "DNS" problem was that firestarter (the firewall) was blocking XBOX from connecting to its servers, so my quick remediation was to just uninstall firestarter completely and I got connected!!! to Xbox online the only problem is that it gave me a warning that my connection type is a moderate NAT, so anyone that knows how to make that better, it would be greatly appreciated.

---

### Post by Chuck- on 2010-05-28
Heres exactly how I did it pretty much, I made a thread:

[http://ubuntuforums.org/showthread.php?t=1495152](http://ubuntuforums.org/showthread.php?t=1495152)

---

