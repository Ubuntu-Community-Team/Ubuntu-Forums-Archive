---
title: "FSC Amilo wifi problem"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by timmson on 2009-01-18
hello!
My wifi card worked fine until i have turned off it in bios. then i have turned it on, but network-manager show :"wirless network is not allow".
iwconfig wlan0:
```
wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
iwlist wlan0 scanning:
```

wlan0     No scan results

```

---

### Post by timmson on 2009-01-21
nobody knows?
/var/log/messages
```
Jan 21 19:42:24 timmson-pc kernel: [   41.573184] iwl3945 0000:02:00.0: PCI INT A disabled
```

---

### Post by timmson on 2009-01-21
bios default and all work)

---

