---
title: "wifi problems, can't activate my wlan"
date: 2005-01-18
forum: Networking &amp; Wireless
---

### Post by nico on 2005-01-18
I installed ndiswrapper without any problems:

```
Jan 18 20:28:19 localhost kernel: ndiswrapper: using irq 5
Jan 18 20:28:20 localhost kernel: wlan0: ndiswrapper ethernet device 00:0b:7d:0f:46:f0 using driver bcmwl5.sys
Jan 18 20:28:20 localhost kernel: ndiswrapper device wlan0 supports WPA with AES/CCMP and TKIP ciphers
Jan 18 20:28:20 localhost kernel: ndiswrapper: driver bcmwl5.sys (Broadcom,06/25/2004, 3.40.73.0) added

```

I can scan for access points:
```

root@ubuntu:/var/log # iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:30:BD:F8:80:E2
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462GHz (channel 11)
                    Quality:0/100  Signal level:-84 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1Mb/s
                    Bit Rate:2Mb/s
                    Bit Rate:5.5Mb/s
                    Bit Rate:11Mb/s
                    Bit Rate:18Mb/s
                    Bit Rate:24Mb/s
                    Bit Rate:36Mb/s
                    Bit Rate:54Mb/s
                    Bit Rate:6Mb/s
                    Bit Rate:9Mb/s
                    Bit Rate:12Mb/s
                    Bit Rate:48Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:80:C8:2A:8D:F2
                    ESSID:"NYB"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462GHz (channel 11)
                    Quality:0/100  Signal level:-35 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1Mb/s
                    Bit Rate:2Mb/s
                    Bit Rate:5.5Mb/s
                    Bit Rate:11Mb/s
                    Bit Rate:22Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

The second one is mine, the first one is my neighbours :) I disabled WEP for now as I thought that could be my problem. So everything appears to be fine but when I want to enable the wlan0 in network-tools in Gnome, the checkbox unchecks itself after 2 seconds without any message after checking it. There isn't anything logged except the following (in Windows this card works fine).

```
Jan 18 21:07:33 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jan 18 21:07:41 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Jan 18 21:08:02 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jan 18 21:08:14 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jan 18 21:08:27 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan 18 21:08:34 localhost dhclient: No DHCPOFFERS received.
Jan 18 21:08:34 localhost dhclient: No working leases in persistent database - sleeping.
```

I also get the following but don't know if it has anything todo with my wlan0:

```
Jan 18 21:04:44 localhost dhclient: sit0: unknown hardware address type 776
Jan 18 21:04:45 localhost dhclient: sit0: unknown hardware address type 776
```

My router doesn't log anything. Trying to set the connection settings with iwconfig doesn't work either. I just don't get any errors but nothing changes. How can I debug this more??

---

### Post by Alexander Kirillov on 2005-01-20
The message "No DHCPOFFERS received" is the culprit (as you probably understand) - it means your machine was unable to get DHCP address. I had similar problems when connection quality is poor - say, when I am far from the router. 

My guess is that your machine is trying to get DHCP from your neighbor's  router first, and it fails because of poor link quality. Did you   try setting ESSID to force it connecting to your own router only?

---

### Post by nico on 2005-01-20
Hm for some reason I didn't get an email for your reply.
Yes I have tried setting everything manually, but that doesn't work. Link quality from my neighbour is actually also excellent, and my own router stands besides my laptop so that can't be it.

---

