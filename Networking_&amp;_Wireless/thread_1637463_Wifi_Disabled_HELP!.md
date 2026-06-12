---
title: "Wifi Disabled HELP!"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by SightSmash on 2010-12-04
Hi! I'm a complete newbie to Ubuntu (or unix, for that matter) and am having trouble with my wifi. I have an HP Pavillion dv4000 laptop that was previously running XP, and I followed the troubleshooting guide and nothing works. I don't remember being given an option to enable the wifi antenna/card and I haven't been able to find anything that helps yet.

---

### Post by Trigger_21 on 2010-12-04
Hey 

can you run this command and confirm that your wifi card is detected by linux, please post output from command

"ifconfig"

---

### Post by karthick87 on 2010-12-04
Post the output of,

```
sudo iwlist scan
```
```
iwconfig
```

---

### Post by ajmjbrowning on 2010-12-12
also having wifi problems with hp pavilion DV6000 BCM 4311 802.11b/g
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:66:56:48  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe66:5648/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:568981 (568.9 KB)  TX bytes:109351 (109.3 KB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

