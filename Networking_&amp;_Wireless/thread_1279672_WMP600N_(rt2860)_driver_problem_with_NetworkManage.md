---
title: "WMP600N (rt2860) driver problem with NetworkManager"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by TheBigT on 2009-10-01
Hi everyone,

I'm trying to get a Linksys WMP600N wifi-n card (rt2680 chipset) working under Jaunty.
The card works with the stock driver, but the n connectivity is fubar. I've seen some posts indicating that the fresh RaLink drivers perform better, so I tried to build them from source.

I followed the steps that are outlined here: [http://forums.remote-exploit.org/backtrack-4-bugs-fixes/23611-ralink-rt2860-doesnt-work-eeepc-1000h-wpa2-ccmp.html](http://forums.remote-exploit.org/backtrack-4-bugs-fixes/23611-ralink-rt2860-doesnt-work-eeepc-1000h-wpa2-ccmp.html) using the latest 2.2.0.0 driver tar.gz from RaLink.

The driver I built seems to work, I can do an insmod and iwconfig lists the card, but NetworkManager refuses to support it, with the following messages in daemon.log:

Oct  1 10:15:41 xxx nm-system-settings:    SCPlugin-Ifupdown: device 
added (udi: /org/freedesktop/Hal/devices/net_pci_1814_601, iface: ra0): not well known
Oct  1 10:15:41 xxx NetworkManager: <WARN>  wireless_get_range(): (ra0): couldn't get driver range information (100). 
Oct  1 10:15:41 xxx NetworkManager: <WARN>  constructor(): (ra0): Device unsupported, ignoring. 

Why is the device unsupported with the new driver, but not with the old one? What should I do to try to resolve this problem?

Thanks in advance for any tips!

---

### Post by Fzappa70 on 2009-10-03
I can connect  with 802.11n (no security) using the ralink linux driver compiled from source on Jaunty.

ra0       Ralink STA  ESSID:"MySSID"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=5.805 GHz  Access Point: 00:23:69:E5:20:99   
        [COLOR=Red]**  Bit Rate=270 Mb/s   **[/COLOR]
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-52 dBm  Noise level:-56 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The unsuccessful part is that I cannot get it to work with WPA1/2 using either DHCP or static addressing. The WPA supplicant reports that is succeeds with the 802.1x 4 way handshake and the group handshake. In the case of DHCP it ends up with a timeout and with static address I can't ping the router.

---

### Post by arepaking on 2010-09-27
I am having this problem to. I can connect to a "G" network with no issues but when it comes to a "N" network it just won't connect.

Any ideas?

---

