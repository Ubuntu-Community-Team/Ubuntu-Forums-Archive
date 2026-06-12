---
title: "AR5007 g-mode problem"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by K3N8 on 2008-12-04
Hi,

I can only configure my wireless Ath5k_pci card in mixed mode. When I try to set to g-mode through iwconfig I get the following message: ```
webmaster@laptop:~# iwconfig wlan0 modu 11g
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; Operation not supported.

```

Here is my iwconfig wlan0:```
wlan0     IEEE 802.11bg  ESSID:"[Not Important]"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: [Access Piont]   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:**password**   Security mode:open
          Power Management:off
          Link Quality=67/100  Signal level:-60 dBm  Noise level=-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Thanks

Alexander

---

