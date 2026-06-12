---
title: "Can't get BELKIN f5d9050 wireless to connect"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by davoutuk on 2009-09-03
I trying to activate a Belkin f5d9050 USB wireless device on my Ubuntu server r9 installation.

I've followed the instructions as laid out in [Manual Network Configuration without the need for Network Manager]("http://ubuntuforums.org/showthread.php?p=3501096") but I can't get this to work.

So far I have...
* installed wpasupplicant
* created the 'wpa_supplicant.conf' file with the WPA(1) content

Following the 'connect via command instructions' when I enter...

```
   
    sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

```

... then the process just hangs.

This last command spits out the following info before it hangs...
```
   
   WPA: key negotiation completed...
   CTRL-EVENT-CONNECTED - connection to .... completed

```

Any ideas?

If I key CTRL-C the command line returns.

---

### Post by davoutuk on 2009-09-03
I found another [article]("http://ubuntuforums.org/showthread.php?t=318539") that explains how to configure the interfaces file and this proved to be more successful. Eventually I got the wireless link working using the following interfaces file content..
```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> [IMPORTANT: See "WPA-PSK key generation"] 

```

---

