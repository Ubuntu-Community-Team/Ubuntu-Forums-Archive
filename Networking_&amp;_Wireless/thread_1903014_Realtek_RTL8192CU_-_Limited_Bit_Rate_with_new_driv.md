---
title: "Realtek RTL8192CU - Limited Bit Rate with new driver"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by gdselzer on 2012-01-01
On 11.10 32-bit, the newest RTL8192cu drivers (3.3.0 and 3.3.1) will easily install and connect me to the network.  However, I am only connecting at 72Mb/s as reported by iwconfig and Network Manager. 

```
gdselzer@givo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"chopax"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: C0:C1:C0:1B:43:CA   
          [COLOR="Red"]**Bit Rate:72 Mb/s**[/COLOR]   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-52 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Trying to increase the bit rate with iwconfig doesn't have any effect.

```
sudo iwconfig wlan1 rate 150M
```

v2.0 of the driver is a pain in the @$$ to compile and has other issues, however, it will give me 144 or 150 Mb/s rates.

Has anyone run across this?  More importantly, anyone know how to fix it in the v3 of the driver?

---

### Post by Huzudra on 2012-05-31
Same problem still exists on 12.04 with the inbuilt driver.

Suggestions? I'd like to be able to run at full 'N' speed.

---

