---
title: "wireless connection dropping, reboot req'd"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by dkruidhof on 2009-12-06
My wireless connection drops for some reason after a long but random time. It usually happens when I am away from my computer, but has happened once in the middle of my using it. When I check for wireless networks it can no longer find any. Only after rebooting am I able to reconnect.


Here's the debug log after it disconnected:
```
Dec  5 14:45:31 david-desktop kernel: [   37.520109] wlan0: authenticate with AP 00:0f:66:05:ce:b2
Dec  5 14:45:32 david-desktop kernel: [   37.720072] wlan0: authenticate with AP 00:0f:66:05:ce:b2
Dec  5 14:45:32 david-desktop kernel: [   37.721685] wlan0: authenticated
Dec  5 14:45:32 david-desktop kernel: [   37.721692] wlan0: associate with AP 00:0f:66:05:ce:b2
Dec  5 14:45:32 david-desktop kernel: [   37.723792] wlan0: RX AssocResp from 00:0f:66:05:ce:b2 (capab=0x411 status=0 aid=3)
Dec  5 14:45:32 david-desktop kernel: [   37.723800] wlan0: associated
Dec  5 14:45:42 david-desktop kernel: [   47.772040] wlan0: no IPv6 routers present
Dec  5 18:17:11 david-desktop kernel: [12737.331260] usb-storage: device found at 6
Dec  5 18:17:11 david-desktop kernel: [12737.331266] usb-storage: waiting for device to settle before scanning
Dec  5 18:17:16 david-desktop kernel: [12742.337040] usb-storage: device scan complete
Dec  5 18:17:16 david-desktop kernel: [12742.394004] sd 4:0:0:0: [sdc] Mode Sense: 37 00 00 08
Dec  5 22:47:16 david-desktop kernel: [28942.192806] wlan0: deauthenticated (Reason: 7)
Dec  5 22:47:17 david-desktop kernel: [28943.196096] wlan0: direct probe to AP 00:0f:66:05:ce:b2 try 1
Dec  5 22:47:17 david-desktop kernel: [28943.396111] wlan0: direct probe to AP 00:0f:66:05:ce:b2 try 2
Dec  5 22:47:17 david-desktop kernel: [28943.397994] wlan0 direct probe responded
Dec  5 22:47:17 david-desktop kernel: [28943.398001] wlan0: authenticate with AP 00:0f:66:05:ce:b2
Dec  5 22:47:17 david-desktop kernel: [28943.399688] wlan0: authenticated
Dec  5 22:47:17 david-desktop kernel: [28943.399694] wlan0: associate with AP 00:0f:66:05:ce:b2
Dec  5 22:47:17 david-desktop kernel: [28943.408142] wlan0: RX ReassocResp from 00:0f:66:05:ce:b2 (capab=0x411 status=0 aid=3)
Dec  5 22:47:17 david-desktop kernel: [28943.408156] wlan0: associated
Dec  5 22:48:14 david-desktop kernel: [29000.324108] wlan0: deauthenticated (Reason: 7)
Dec  5 22:48:15 david-desktop kernel: [29001.324789] wlan0: direct probe to AP 00:0f:66:05:ce:b2 try 1
Dec  5 22:48:15 david-desktop kernel: [29001.528070] wlan0: direct probe to AP 00:0f:66:05:ce:b2 try 2
Dec  5 22:48:16 david-desktop kernel: [29001.728154] wlan0: direct probe to AP 00:0f:66:05:ce:b2 try 3
Dec  5 22:48:16 david-desktop kernel: [29001.932099] wlan0: direct probe to AP 00:0f:66:05:ce:b2 timed out
```

And here is iwconfig connected...
```
david@david-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"JesusIsLord"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:66:05:CE:B2   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-desktop:~$
```

and disconnected:
```
david@david-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"JesusisLord"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-desktop:~$
```

The issue seems to be that the Access Point is "Not-Associated". Unfortunately, I don't know what that means or how to fix it. When I searched through the forums, I found similar situations from years past, but nothing helpful for fixing it. If you think I missed something, feel free to point me to it. Otherwise, any new thoughts would be greatly appreciated.

---

### Post by uncaspi on 2009-12-06
Hi.
There have been some problems here with the 9.10 and network key in wireless. Unsecure your router to see if its getting better. Possible bug in 9.10

---

### Post by dkruidhof on 2009-12-08
I'm not sure how that would help. Once it can no longer connect, it simply can't find any wireless networks at all. And, I'm in a dense apartment complex, so I really don't want to just open my wireless network to everyone here.

also, in case it helps anyone, here is the output of lspci:

```
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0d.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

---

### Post by LinuxFanBoi on 2009-12-08
> **dkruidhof said:**
> I'm not sure how that would help. Once it can no longer connect, it simply can't find any wireless networks at all. And, I'm in a dense apartment complex, so I really don't want to just open my wireless network to everyone here.

also, in case it helps anyone, here is the output of lspci:

```
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0d.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

I;ll PM you the e-mail address of the tech support rep at Realtek who had the driver for my Realtek 8192SE,  he was very fast and the driver solved the same problems for me that you are having, even though you have different hardware.  Perhaps they have a driver for you.  

PS all their drivers require that you have build essentials and kernel sources installed.  They also require that you build the driver from source to install it.  It's not very hard really, and if you need help,  let me know.

---

