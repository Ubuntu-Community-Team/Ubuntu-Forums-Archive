---
title: "BCM4328 Wireless Works, But Can Not Scan"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by Krazy-Killa on 2010-09-23
Ok I got my BCM4328 Wireless-N card to work using the proprietary STA drivers, but I can't use the 'iwlist scan' command.

```
Owner@Krazy-Laptop:~$ sudo iwlist wlan0 scan
wlan0     Failed to read scan data : Invalid argument
```
But running 'sudo iwconfig' gives me this.
```
Owner@Krazy-Laptop:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Luna"  
          Mode:Managed  Frequency:5.58 GHz  Access Point: C0:3F:0E:06:A6:30   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-43 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:16  Rx invalid frag:0
          Tx excessive retries:79  Invalid misc:0   Missed beacon:0
```
I'm not sure what's wrong, but I did recently install 'bcm43-fwcutter', even though apparently the card was running fine without that installed, or at least there was no chance after that package was installed.  I even went as far as to do a clean re-install, and still I cannot do a scan.

---

