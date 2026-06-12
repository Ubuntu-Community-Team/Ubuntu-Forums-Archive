---
title: "Installing Netgear WG311v2 Adapter"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by juroen on 2009-03-03
Hello guys

I recently installed a Netgear WG311v2 into my "Ubuntu" System. Also im already trying to get it to work for a few weeks now :(. But its still not working.

So my question is: how can install the Netgear WG311v2 driver for my linux machine. I never did this before so a little tutorial with commands would be nice.

Thanks :D

Juroen

Sorry for my bad english

---

### Post by N04h on 2009-03-03
Can you run the ifconfig and iwconfig commands from the command line and copy and paste what you get back into here.  Put it inside the code tag to make it easier to read.

---

### Post by juroen on 2009-03-04
> **N04h said:**
> Can you run the ifconfig and iwconfig commands from the command line and copy and paste what you get back into here.  Put it inside the code tag to make it easier to read.


ok thanks for your reply will post it when im back home tonight :)

---

### Post by Lgodio on 2009-03-04
How do you use iwconfig output to get it to work ?

---

### Post by juroen on 2009-03-04
IWCONFIG:

```
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11b+/g+  Nickname:"acx v0.3.36" 
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated    
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3   
          Retry min limit:7   RTS thr:off    
          Power Management:off 
          Link Quality=47/100  Signal level=26/100  Noise level=0/100 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions. 

```

IFCONFIG:

```
eth0      Link encap:Ethernet  HWaddr 00:11:2f:f0:f8:e2   
          inet6 addr: fe80::211:2fff:fef0:f8e2/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:1073 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1050 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:1094607 (1.0 MB)  TX bytes:183887 (183.8 KB) 
          Interrupt:23 Base address:0xa000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B) 
 
wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:48:1d:ec   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18  
```

INTERFACES:

```
auto wlan0 
iface wlan0 inet dhcp
```

---

### Post by N04h on 2009-03-05
is wlan0 your internal wifi card on your computer?

---

### Post by N04h on 2009-03-05
It is confirmed that wlan0 is your adapter.

What have you tried to do to get it to work.  Have you tried using the command line or the GUI?

This may be useful: [http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html]("http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html")

---

### Post by juroen on 2009-03-06
i only tryed the CLI
dont know how to install the GUI (which program it is for wireless network)

Trying your link now

Thanks

---

### Post by N04h on 2009-03-06
What command are you using at the GUI?  Maybe that's the problem?

---

### Post by juroen on 2009-03-07
im not using an GUI for the network adapter. (dont know which program i need)

---

