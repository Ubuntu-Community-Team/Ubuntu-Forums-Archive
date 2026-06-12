---
title: "wired connection problems"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by mik765 on 2009-03-31
Hello everyone,

I just installed Ubuntu 8.10 desktop Edition and am having problems connecting to my DSL connection. It connects for about 2 seconds and then disconnects, and keeps going through the same cycle.I am using Westell 327w modem/router and it works fine with windows. any help will be greatly appreciated.

---

### Post by freonchill on 2009-03-31
do you have the modem in PPPoE or bridge mode?

if pppoe then it should be straight ethernet
if bridge, then you need to do the pppoe connection

---

### Post by superprash2003 on 2009-04-01
how do you say that it connects and disconnects.. does ubuntu give any message? post output of** ifconfig** from the terminal

---

### Post by mik765 on 2009-04-02
I get a constant message on the top bar stating, here is the message i get. "connection established, you are now connected to auto Eth0" right after it establishes connection it immediately disconnects and i get the message "disconnected, the network connection has been disconnected" and then it keeps repeating the same process. here are the results of ifconfig:

---

### Post by mik765 on 2009-04-02
eth0      Link encap:Ethernet  HWaddr 

          inet6 addr: xxx::xxx:xxx:xxx:xxx/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets 100 errors:0 dropped:0 overruns:0 frame:0

          TX packets:182 errors:1 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:13872 13.8 KB  TX bytes:29392 (29.3 KB)

          Interrupt:22 Base address:0x8000 

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: :1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:314 errors:0 dropped:0 overruns:0 frame:0

          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:20560 (20.5 KB)  TX bytes:20560 (20.5 KB)

---

### Post by mik765 on 2009-04-02
Do I have to manually set up the PPPoE?

---

### Post by superprash2003 on 2009-04-03
check your LAN cable.. does the modem keep rebooting every few seconds?? observe the power light , does it blink?

---

### Post by mik765 on 2009-04-05
I have checked and ruled out the modem as the problem because I have another pc connected to the same modem and it does not have any problems, however I did have similar problems with windows xp running on the same computer and I was able to fix that by changing the Duplex/Speed settings for the NIC. how do i change those same settings in Ubuntu 8.10?

---

