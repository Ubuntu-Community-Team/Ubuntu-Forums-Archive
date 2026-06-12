---
title: "Have internet but having problems connecting to other devices on home network"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by darkmakozu on 2009-09-29
Right, bear with me on this one, my problem has me absolutely stumped.

On my Ubuntu Jaunty installation which I've been using for quite a while know I have seem to have run into a small issue on my network. I cannot connect to other devices. My Computer doesn't appear on any other computer I have at my house: My Mac running OS X Tiger and another computer Running Ubuntu Jaunty. Also I can no longer use Mediatomb with my PS3.

I can still connect to the internet and I still have access to a few other features such as Bit torrent but recently I have not been able to connect to the other devices. I'm not sure when this trouble began but is it possible that there is something in Ubuntu blocking these services such as network sharing (NFS, SMB and Netatalk)  and mediatomb? I would give more information but frankly I am stumped as to how to diagnose my problem.

---

### Post by cariboo on 2009-09-29
IF you are using dhcp, there could be an ip address conflict.

---

### Post by darkmakozu on 2009-09-30
I'm not sure that's the case, I *should* be using a statically assigned IP that I set up back when I was using Hardy before upgrading up to Jaunty. If it helps I shall post the output of ifconfig

```
makozu@makozu-linuxcore:~$ ifconfig -a -v
eth0      Link encap:Ethernet  HWaddr 00:e0:29:29:b1:63  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe29:b163/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2709034 (2.7 MB)  TX bytes:683006 (683.0 KB)
          Interrupt:11 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6894 (6.8 KB)  TX bytes:6894 (6.8 KB)

pan0      Link encap:Ethernet  HWaddr a2:05:ec:b6:de:28  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I have Gnome, XCFE, KDE and openbox installed. Is it possible that one of them may have affected my network?

---

### Post by Iowan on 2009-09-30
Have you checked the addresses of the other (unreachable) devices? Can you **ping** them by name or address? Are machines connected via router or hub/switch?

---

### Post by silverwolf636 on 2009-09-30
I am also having the same problems here. I can ping my other computers that are also running Ubuntu hardy.

---

### Post by darkmakozu on 2009-10-01
Using the Gnome Networking tool I pinged My Playstation 3 successfully and I also decided ran a port scan upon my own computer. It revealed that the port used by Mediatomb was open, so the problem doesn't seem to be port based. I shall ping my other systems when I have access to them later.

---

