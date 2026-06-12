---
title: "Netgear Adapter ~ Slow &amp; Disconnects (After 5 Minutes)"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by Bozomo on 2010-11-30
Hello, I am fairly new to Ubuntu - just installed yesterday - and I love it so far except my wireless turns on for about 5 minutes, then disconnects.

In order to get internet back I have to either restart or uncheck "Enable Networking" and then recheck it.

I will try to provide as much information, but like I said I am new to Ubuntu and there is some things that are completely different from what I'm used to on Windows:

**Wireless Adapter: **Netgear RangeMax Next Wireless PCI Adapter WN311B
[B]
Additional Driver its Using:[/B] Broadcom STA wireless driver

**Router:** Netgear RangeMax
[B]
Information From "sudo iwconfig":[/B]
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:"Bergman"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:2A:E3:62:7F   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=3/5  Signal level=-69 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:25  Invalid misc:0   Missed beacon:0
```Thank you so much for you help! I can't go back to Windows! Lol.

---

### Post by grahammechanical on 2010-11-30
I am comparing your iwconfig listing with mine. You have something listed that I do not have.

I see in my list Link quality and Signal level, but you have in addition - Noise level=-95dBm.

Could this be the cause of your problem? 

Regards

---

### Post by Bozomo on 2010-11-30
I found out that my router log has tons of statements saying that my ip is (DoS) attacking and it disconnects me

Trying to find a solution.

---

