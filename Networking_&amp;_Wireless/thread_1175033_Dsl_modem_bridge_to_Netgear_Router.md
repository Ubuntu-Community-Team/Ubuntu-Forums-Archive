---
title: "Dsl modem bridge to Netgear Router?"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by Gerard08 on 2009-05-31
I carefully followed the directions to change my Westell 6100 DSL modem to bridge mode as recommended to use with a Netgear wired router. I lost connectivity to the internet. I know I didn't complete this last step:> Enter ipconfig /release at the Command Prompt.

Can I do this in Console? What might have gone wrong in my settings?

I am using my router to print from a laptop running xp, and eventually set-up a Samba file share. This is proving to be difficult, possibly b/c of this problem: [http://ubuntuforums.org/showthread.php?t=825401&referrerid=571316]("http://ubuntuforums.org/showthread.php?t=825401&referrerid=571316")?

Here'e my ipconfig output
```
 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:9e:e8:d6  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe9e:e8d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43087892 (43.0 MB)  TX bytes:7688801 (7.6 MB)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36373 (36.3 KB)  TX bytes:36373 (36.3 KB)

pan0      Link encap:Ethernet  HWaddr fa:a1:49:62:82:6f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


``` I am a novice linux user with no experience with home networking. Thanks for your input. I am running 8.10 on a homebuilt desktop with an Asus mb.

---

