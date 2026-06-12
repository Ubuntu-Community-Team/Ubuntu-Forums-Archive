---
title: "Wireless not always connecting"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by KBoisits on 2013-03-23
When I boot the machine sometimes the wireless will connect and sometimes it will not. I have looked at the syslog file and it seems that when it does NOT boot it has this:
[INDENT]Mar 23 20:30:20 zotac-desktop wpa_supplicant[746]: WPA: Key negotiation completed with <Removed> [PTK=CCMP GTK=CCMP][/INDENT]
[INDENT]Mar 23 20:30:20 zotac-desktop wpa_supplicant[746]: CTRL-EVENT-CONNECTED - Connection to <Removed> completed (auth) [id=0 id_str=][/INDENT]
[INDENT]Mar 23 20:30:21 zotac-desktop wpa_supplicant[746]: WPA: Key negotiation completed with <Removed> [PTK=CCMP GTK=CCMP][/INDENT]

Notice there are two "WPA: Key negotiation completed" messages. When it does work and connects on boot there is only one. Does this have something to do with the dual band router or is this not related at all?

The machine is a [FONT=arial]Zotac[/FONT][FONT=arial] IONITX-T-U Desktop Motherboard and the router is Asus RT-N66U.
[/FONT]
I removed network manager and in the interface file for my wireless connection I have this:
auto wlan0
iface wlan0 inet static
#iface wlan0 inet dhcp
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
wpa-driver wext
wpa-ssid <Removed>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <Removed>


When it doesn't connect I have to reboot it a few times until it will get a connection. Any help or direction would be great as this is been annoying me for a while now.

Thanks,
  Kevin

---

