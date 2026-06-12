---
title: "Wireless card not scanning"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by ForMar on 2009-02-23
I am using 8.04 on a ppc, but for some reason my card will not scan for anything I think that it might be "unactive" for one reason on another.

I have already done what FAQ suggest about the firmware
```
sudo aptitude install bcm43xx-fwcutter
```

but still nothing, my iwconfig is as follo
```
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci displays as follows:


```
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

Thanks for any help

___________________________SOLUTION!_________________
It seems that you have to run one last command that they dont tell you in the wiki...god knows why


```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

---

### Post by pdtpatrick on 2009-02-23
what do you get when you scan?

sudo iwlist wlan0 scanning

---

### Post by ForMar on 2009-02-23
Thanks for responding,

> **pdtpatrick said:**
> what do you get when you scan?

sudo iwlist wlan0 scanning



```
wlan0 Interface doesn't support scanning : Network is down
```

I should also note that I have tried several different wireless network managers none work

---

