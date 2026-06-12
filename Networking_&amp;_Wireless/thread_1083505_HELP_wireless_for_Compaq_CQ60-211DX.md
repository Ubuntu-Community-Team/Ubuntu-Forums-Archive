---
title: "HELP: wireless for Compaq CQ60-211DX"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by [.root/fail] on 2009-03-01
I have tried quite a bit and I still cannot get any luck on getting my wireless to work. I am REALLY hoping to get wireless before the 6th of March, I will be going on vacation then, and it's important to me I can be wireless at that point.
     When I go to System>Administration>Hardware Drivers I 

     Specifications: Compaq CQ60-211DX
                     64-bit architecture processor
                     Ubuntu 8.10 (64-bit)
                     [http://h10025.www1.hp.com/ewfrf/wc/s...roduct=3866423](http://h10025.www1.hp.com/ewfrf/wc/s...roduct=3866423)

     The ethernet works fine. (though, I reinstalled because somehow, I must have installed something that conflicted with it). I believe I've given all the info I can, any further information can be found in the following link:          

[http://ubuntuforums.org/showpost.php?p=6795069&postcount=27](http://ubuntuforums.org/showpost.php?p=6795069&postcount=27)

When I run iwconfig I get the following:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

Also, the following image may help. So, it says I have the driver and it's activated, but not in use, of course. But..., when I go to the Wireless tab in Network Connections, it's blank. And when I am unplugged... either it doesn't work or I have no idea what to do to get it started. I'm weighing towards it's not working.

[http://i60.photobucket.com/albums/h39/Kyo-ninja/FGSFDS1.jpg](http://i60.photobucket.com/albums/h39/Kyo-ninja/FGSFDS1.jpg)

---

### Post by [.root/fail] on 2009-03-10
Here is what I get from ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1f:16:50:ce:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:46518765 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Charles Ingalls on 2009-03-18
I have the exact same problem. It's really annoying.
I had no problem finding a solution on my other computer, but on my Eee PC1000H it's impossible to find any wireless network in the network manager.


Anyone?

---

### Post by wangsuda on 2009-03-18
If you're using a Ralink wireless LAN card, then I can help. Otherwise, I am sorry.

---

### Post by [.root/fail] on 2009-03-19
It's an Atheros AR5007 802.11 b/g WiFi Adapter.

---

### Post by ugm6hr on 2009-03-19
Sorry it has taken 3 weeks to get an answer.

[http://ubuntuforums.org/showthread.php?p=6895635#post6895635](http://ubuntuforums.org/showthread.php?p=6895635#post6895635)

---

### Post by [.root/fail] on 2009-03-26
> **ugm6hr said:**
> Sorry it has taken 3 weeks to get an answer.

[http://ubuntuforums.org/showthread.php?p=6895635#post6895635](http://ubuntuforums.org/showthread.php?p=6895635#post6895635)

That worked perfectly. I have the wireless working. Thankyou so much!

---

