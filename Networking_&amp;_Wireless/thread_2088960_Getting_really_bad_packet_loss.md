---
title: "Getting really bad packet loss"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by faux_real on 2012-11-27
I can't get anywhere with this. Every few minutes I start dropping packets and lose my connection for 2-3 minutes. It doesn't seem to be a hardware issue as everything works fine when I run Windows. Wifi signal strength is fine. Nothing showing up in log files. 

ping google.com
```

. . .
64 bytes from ord08s06-in-f2.1e100.net (74.125.225.34): icmp_req=32 ttl=51 time=55.1 ms
64 bytes from ord08s06-in-f2.1e100.net (74.125.225.34): **icmp_req=33** ttl=51 time=55.3 ms
64 bytes from ord08s06-in-f2.1e100.net (74.125.225.34): **icmp_req=64** ttl=51 time=55.5 ms
64 bytes from ord08s06-in-f2.1e100.net (74.125.225.34): icmp_req=65 ttl=51 time=56.1 ms
64 bytes from ord08s06-in-f2.1e100.net (74.125.225.34): icmp_req=66 ttl=51 time=56.4 ms
64 bytes from ord08s06-in-f2.1e100.net (74.125.225.34): icmp_req=67 ttl=51 time=54.6 ms
64 bytes from ord08s06-in-f2.1e100.net (74.125.225.34): icmp_req=68 ttl=51 time=56.3 ms
64 bytes from ord08s06-in-f2.1e100.net (74.125.225.34): icmp_req=69 ttl=51 time=55.0 ms
^C
--- google.com ping statistics ---
69 packets transmitted, 39 received, **43% packet loss**, time 68291ms
rtt min/avg/max/mdev = 53.959/56.213/75.533/3.494 ms

```ifconfig wlan2

```
wlan2     Link encap:Ethernet  HWaddr [removed]  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10297 errors:0 **dropped:32310** overruns:0 frame:0
          TX packets:9977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8797397 (8.7 MB)  TX bytes:1726471 (1.7 MB)
```Please help.

---

### Post by StinkySQL on 2012-11-27
Just some thoughts ...
Are they both using inet 4 or is Windows running ipv6?
Is the radio being set up the same in both OS systems? The default gain in Ubuntu may be lower perhaps - something along those lines. 

SS

---

### Post by faux_real on 2012-11-27
> **StinkySQL said:**
> Just some thoughts ...
Are they both using inet 4 or is Windows running ipv6?
Is the radio being set up the same in both OS systems? The default gain in Ubuntu may be lower perhaps - something along those lines. 

SS

They're both using v4. I disabled v6 on the linux side because I read that it could cause stability problems with rtl81xx drivers but it didn't seem to make any difference.

I don't think small differences in gain would be an issue as I'm sitting pretty close to the router and through the periods of packet loss, iwScanner shows no problems with signal strength or noise.

---

### Post by varunendra on 2012-11-29
Hi faux_real, Welcome to the forums! :)

I looked at the netinfo file you attached and the first and a 'Strong' suggestion is to upgrade your OS to 12.04, as Natty (11.04) is no more supported. It has reached its EOL (end of life) and so you won't get updates for it. Details : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

We may try to do the troubleshooting in the current setup and I'll gladly help. But honestly, I don't think an outdated version is worth putting too much effort in it. But still if you have some good enough reason to stick with it, please let me know and we may try a few things.

However, if you concur with me and prefer to upgrade, I'd suggest to download the 12.04 iso via torrent which can be downloaded from here - [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

How to Burn ISO : [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Your current version is 32 bit. If your system supports 64 bit and doing a clean installation is not a problem for you, I'd suggest to download and install 64 bit. However, if you wish to 'upgrade' (if possible), you would need 32 bit and you may try the 'Upgrade' options if the cd offers you that.

But I am not sure if 11.04 can be directly upgraded to 12.04 (skipping 11.10). Besides, OS upgrades are often prone to bugs and errors. Therefore, I'd recommend to backup all your data on an external drive or a different partition, then do a 'clean' install of 12.04.

Please let me know what you prefer and if you need any help to make your decision.

Regards,
Varun

---

