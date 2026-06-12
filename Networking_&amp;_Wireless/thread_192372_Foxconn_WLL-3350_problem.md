---
title: "Foxconn WLL-3350 problem"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by AlexBryan on 2006-06-08
Hi, I've just installed Ubuntu for the first time and I'm loving it so far, but I'm having some problems getting my wireless adapter to work. I have a Foxconn WLL-3350 PCI card which I gather is supported by default in Ubuntu:
[http://linux-wless.passys.nl/query_part.php?brandname=Foxconn](http://linux-wless.passys.nl/query_part.php?brandname=Foxconn)

I'm only used to setting up wireless networks in windows XP. I guess ESSID is the same as SSID in windows and I've added that and I entered the wep key. It says the wireless adapter ra0 is active, but firefox won't connect to any webpages. I've tried both DCHP and a static IP address using 192.168.0.1 as the default gateway. I don't what else to do. 

I'm a novice linux user so if the answer is technical could you explain it slowly. Thanks!

---

### Post by mindwarp on 2006-06-09
It would help the troubleshooting process if you could take screenshots of your network config windows, and also post the output of 
```

sudo iwconfig ra0 all

```

---

### Post by emilde on 2006-07-01
I'm having the same problem with the same hardware

Netwok settings indicates ra0 is active and I can see all of the local wireless routers listed on the ESSID dropdown, but Network Manager only sees the wired network.

$ sudo iwconfig ra0 all

ra0       RT2500 Wireless  ESSID:"homeip"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:#########   Security mode:open
          Link Quality=84/100  Signal level=-58 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by emilde on 2006-08-21
Finally found this article that helped me fix my problems with this card:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

Hope it helps someone else

---

