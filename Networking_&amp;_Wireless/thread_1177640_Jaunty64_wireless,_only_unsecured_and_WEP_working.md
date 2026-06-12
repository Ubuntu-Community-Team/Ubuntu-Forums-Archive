---
title: "Jaunty64 wireless, only unsecured and WEP working"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by Evil Dax on 2009-06-03
Well, having Ubuntu64 since it came out (fresh install).
There were some 'minor' issues with WLAN, which I thought would be fixed pretty soon.

However, Wireless is still hopeless.

Machine: Acer Aspire Notebook with Intel WifiLink 5100
Original OS: WinVista32 sp1 (wireless works on WEP,WPA and WPA2)
New OS: Ubuntu Jaunty64 (up-to-date)

What I tried so far:
[LIST]
[*]'latest' driver from IntelLinuxWireless
[*]WICD instead of Networkmanager
[*]updated WPA_Supplicant
[*]ndiswrapper (it does not seem to like the Windriver for Intel)
[*]manually building compat-wireless (arghh... the horror)
[*]manually added all info from the HOWTO-Wireless Security
[*]and a lot more, which I cannot remember so soon...
[/LIST]

Here's what my wpa_supplicant log says:

```

CTRL-EVENT-SCAN-RESULTS 
Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxxxxxxx' freq=2452 MHz)
Associated with xx:xx:xx:xx:xx:xx
WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS

```

Anyone got a fix that works? Using only WEP is not an option here...

[edit] It seems either a problem of the 64bit Jaunty, or the iwlagn (intel) driver, as my fileserver running Jaunty32 with RT2600 connects just fine to WPA2

---

### Post by Crafty Kisses on 2009-06-03
Just out of curiousity what's the output of the following? That might give me some more information.
```
iwconfig
```

---

### Post by Evil Dax on 2009-06-03
Logged in using WEP,
iwconfig puts out:

```

wlan0     IEEE 802.11abgn  ESSID:"xxxxxxx"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:xxxxx [3]   Security mode:open
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Trying to login using WPA2:
```

wlan0     IEEE 802.11abgn  ESSID:"xxxxxxxxx"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:xxxxxxxxxxxxxxxx [2]   Security mode:open
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

where all the 'xx' are obviously blocked for privacy.

---

### Post by PostWax on 2009-06-04
I too have had all kinds of issues with my wireless.  No real luck other than rebooting several times until it connects.

Several weeks back I came across some information regarding the CCMP option in the wireless network configuration.  In Terminal gconf-editor, do not use sudo.  System, networking, connections, 802-11 wireless.  They said to remove the CCMP if it exist here.  I tried this with 8.10 and it help a bit but I do not have that option showing up in 9.04.

The above is not much help, but at least you are not the only one with problems.  Based on the wireless issues in this form I am going to bet someone is working on the issue.

Thanks

---

### Post by Evil Dax on 2009-06-04
Unfortunately, with Gconf-editor, under System, there's no Networking folder available.
I've only got dns_sd, gstreamer, http-proxy, proxy, smb and storage located under System.
(and not even hidden somewhere else in the menu..)

---

### Post by Evil Dax on 2009-06-07
Finally, it works!
Intel has new code:
[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz")

put it in /lib/firmware

and update modules this way:
```

sudo modprobe -r iwlagn
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

```

Now it connects to WPA2 :D

---

