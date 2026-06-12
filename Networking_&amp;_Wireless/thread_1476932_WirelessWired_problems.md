---
title: "Wireless/Wired problems"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by rizon on 2010-05-06
Hello, I am fairly new to Ubuntu. I am using Ubuntu 9.04, and when I try to connect to a wireless network, it usually takes me several times of enabling networking/disabling networking (and wireless), before I can get any internet connection. It will say that I am connected, however when I try to go to any website, it will not work. Also, I will be connected to the Internet, but after a while it will say that I'm still connected, but I won't be able to get on the Internet. Does anyone know what this could be? Thank you very much.

---

### Post by Iowan on 2010-05-06
When it claims you're connected, try pinging the router, etc., by IP address. Another thing you can check is [MTU]("http://ubuntuforums.org/showthread.php?t=1376506").

---

### Post by rizon on 2010-05-08
Hello, I made a post earlier, but the thread I was told to go to didn't help me much. I will connect to this wireless network for a while, and then I will no longer be able to access the Internet. It will say that I am still connected and all of the lights are on on the router and modem, however, I cannot ping the router. I could be connected for only a few minutes or hours, and then I just will not be able to get on any page. I disconnected the cable from the router to connect it directly to my laptop, but my computer will try to connect on eth0 for a while, but won't be able and it will say disconnected. Any suggestions? I'm new to Ubuntu. Any help would be appreciated. Thanks.

---

### Post by Iowan on 2010-05-08
Threads merged.
You don't need to start a new thread for each post.:)
Use the "New Reply" button at the top/bottom left to add to the existing thread.
Does the machine still have an IP address  (**ifconfig -a** from a terminal)?

---

### Post by rizon on 2010-05-08
Sorry about that. I typed in the ifconfig -a, and it does have an IP address. However, it's working right now, able to connect to the internet. Do you want all of the information from that command posted? Here it is just in case.

cody@cody-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:aa:dd:a6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168284 (168.2 KB)  TX bytes:4572 (4.5 KB)
          Interrupt:247 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38978 (38.9 KB)  TX bytes:38978 (38.9 KB)

pan0      Link encap:Ethernet  HWaddr 2a:aa:d5:64:d0:42  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:e2:51:a8  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: 2002:4bb2:42b2:1234:216:eaff:fee2:51a8/64 Scope:Global
          inet6 addr: fe80::216:eaff:fee2:51a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:554691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:446657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573442367 (573.4 MB)  TX bytes:223751578 (223.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-E2-51-A8-31-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

