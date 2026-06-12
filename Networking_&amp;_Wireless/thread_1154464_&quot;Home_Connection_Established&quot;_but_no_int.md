---
title: "&quot;Home: Connection Established&quot; but no internet and can't ping router"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by anthropodeus on 2009-05-09
I am having a strange problem with my wireless (DHCP). i'm running ubuntu 9.04 and have a wireless-n atheros card.

when i boot my computer, it connects automatically to my home's WEP (128-bit encryption) wireless network.  however, when i open firefox, after a long delay i get the "This page cannot be displayed" page.  also, when i go to System->Administration->Network Tools, and ping my router (192.168.1.1) or my wireless print server (192.168.1.10), i get no response. pinging and internet work fine if i am wired to the print server.

there are two additional problems that i dont really need fixed right now, but perhaps they are related to the first issue so i'll mention them:

2. when i start my computer, it only detects wireless networks 50% of the time. if i start my computer and no networks are detected, the next time the computer boots networks WILL be detected. rebooting a second time will again result in no networks being detected.

3.  in the case that i boot and wireless networks are detected and i am therefore automatically "connected" to my home network, right-clicking on the network icon on the panel and de-enabling my wireless will make me unable to reconnect to my home network after i re-enable the wireless.  i just keep getting a box that asks me for the WEP key, which it's already got. rebooting twice will fix this issue (since rebooting once will cause no networks to be detected.)


like i said before, i dont care about the second two problems as long as i am able to solve the first problem and therefore can get connected to the internet.

i'm unsure of what i should post to diagnose this. here's my output from iwconfig:
```

anthropodeus@anthropodeus-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Hudson"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:BF:41:FF   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=51/100  Signal level:-88 dBm  Noise level=-121 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

also, right-clicking on the network icon on the panel and selecting "Connection Information" when connected to the network gives this information:

<Connection Information>
Interface: 802.11 WiFi (wlan0)
Hardware Address: 00:15:AF:DD:94:D5
Driver: ath9k
Speed: 1Mb/s
Security: WEP

IP Address: 192.168.1.4
Broadcast Address: 192.168.1.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.1.1
Primary DNS: 192.168.1.1
</Connection Information>

---

