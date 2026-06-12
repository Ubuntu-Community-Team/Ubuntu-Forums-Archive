---
title: "DUP! when pinging default gateway. No internets for me."
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by woohhaa on 2011-01-30
I had a router crap out yesterday. I'd been testing out a new one for the last few days and just reconfigured it to be the main. Took the old one down and everything in my house (Windows 7 PC, XP Files server, Ubuntu PC , windows 7 laptop, android tablet, ps3, etc) seems to be working fine whether it be hard wired or wifi. All except my ubuntu 10.04 laptop. It worked fine before the swap so I can't figure out what's going on.  

I'm able to connect to the new SSID without issue but I can't resolve any external names and when I try to ping the default gate way every other packet has (DUP!) behind it. If I'm hardwired I don't get the dup! when pinging the default gateway but I still can't resolve any external names. 

Any ideas as to what is going on would be much appreciated? I have provided the results of an ifconfig and the results of a ping to the default gateway below.


cooley@Quigon:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.98 ms
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.04 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=3.50 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=5.72 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=8.09 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=11.1 ms (DUP!)
^C
--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, +3 duplicates, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 2.983/5.750/11.155/3.020 ms


cooley@Quigon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:11:55:78  
          inet6 addr: fe80::212:3fff:fe11:5578/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39001 (39.0 KB)  TX bytes:17555 (17.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75090 (75.0 KB)  TX bytes:75090 (75.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:0b:73:b2  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe0b:73b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2128976 (2.1 MB)  TX bytes:304500 (304.5 KB)

---

### Post by woohhaa on 2011-02-01
I can get out sporadically and I've come to find out my android tablet is doing the same thing. Everything else seems to be functioning fine. I'm really not sure what is going on here. Any help would be much appreciated.

---

### Post by mips on 2011-02-01
You are getting duplicate replies.

1. Double check you don't have 192.168.1.1 configured on any other devices except the new router.
2. Switch all network devices off and back on again as there 'might' forwarding issues related to latent addresses.

---

### Post by woohhaa on 2011-02-01
I am certain there is only 1 device with 192.168.1.1 but I will give turn it all off this afternoon and see what shakes out.

---

### Post by mips on 2011-02-01
> **woohhaa said:**
> I am certain there is only 1 device with 192.168.1.1...

You can check with **arp -a**

---

### Post by woohhaa on 2011-02-01
I ran an arp -a this afternoon afterwards I shut everything down except the router and cable modem. I then brought the ubuntu laptop back up and ran arp -a again. I got the below results both times and I still couldn't get out to the internet while all the other devices were down. 

Its worth mentioning I had no problems on the wireless network at work so I'm guessing this is a router related problem. It just kills me that everything except my ubuntu laptop and android tablet works just fine. ](*,)


cooley@Quigon:~$ arp -a
? (192.168.1.1) at 00:13:10:b1:c8:1a [ether] on wlan0

---

### Post by mips on 2011-02-02
> **woohhaa said:**
> I ran an arp -a this afternoon afterwards I shut everything down **except the router and cable modem**.

Now those were the two that were more important to shut down....

Also supply the IP info for the network devices.

---

### Post by woohhaa on 2011-02-02
I have cycled the power to the cable modem and router numerous times since this ordeal started but I'll try again this morning. 

For right now almost everything is dhcp. These are the addresses that show up in the dhcp table of the router. That list accounts for all our network devices. 

file server	192.168.1.11 	
Windows 7 PC    192.168.1.12 Static
Ubuntu Laptop	192.168.1.15 	
Android Tablet  192.168.1.16 		
Ubuntu Desktop	192.168.1.17 	
DTV Box	        192.168.1.18 	
Win 7 Laptop	192.168.1.19

Edit: Added static address, and edited for clarification.

---

### Post by woohhaa on 2011-02-02
Alright I cycled the modem and routers power. Reconnected the laptop to the SSID and ran the arp -a see results below. 


cooley@Quigon:~$ arp -a
? (192.168.1.1) at 00:13:10:b1:c8:1a [ether] on wlan0
holocron.local (192.168.1.11) at 00:24:1d:c4:1b:96 [ether] on wlan0

---

### Post by mips on 2011-02-02
That looks fine.

---

### Post by woohhaa on 2011-02-02
It's so bizzare because I can hit the web interface of the router from the ubuntu laptop.

---

### Post by woohhaa on 2011-02-02
Alright I finally got it. I reset my ssid to have no security and I was able to get out. I then enabled WPA/WPA2 Personal and set the encryption algorithan to tkip. I reconnected to the new SSID and was able to get out. When I was having issues I was using TKIP+AES. Thanks for the help ):P

---

