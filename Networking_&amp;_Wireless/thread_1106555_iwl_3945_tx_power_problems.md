---
title: "iwl 3945 tx power problems"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by sk8sn0surf on 2009-03-25
Hi, I'm using the latest iwl3945 drivers and I can't seem to set the tx power on my wireless card.

```
root@chris-laptop:~# iwconfig wlan0 txpower 20dBm
root@chris-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:F2:14:71   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=67/100  Signal level:-66 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


The tx power doesnt seem to change. Has anyone had success setting the tx power with the intel pro set wireless 3945. If so what drivers were you using? Please suggest a new driver to try or a workaround to this problem.

Thank You.

---

### Post by sk8sn0surf on 2009-03-25
bump. anyone?

---

