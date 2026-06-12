---
title: "slow wireless card"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by kenhen93 on 2009-12-08
Hey all,

I have got wireless N speeds with this card (linksys wmp300n) on Windows XP but not with ubuntu. I am connecting to a WRT310n with DD-WRT installed. I have other Wireless N cards that can connect to this router with N speeds.

**/etc/network/interface**
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid <blah>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <blah>

[B]iwconfig
[/B]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:"blah"  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1E:E5:38:37:C9   
          Bit Rate=14 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-51 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:26  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



I followed this write up to set this up because while this card was running fine using NetworkManager Applet 0.7.0.100 I could not configure it for AES - WPA2.

[http://ubuntuforums.org/showthread.php?t=202834&highlight=wmp300n](http://ubuntuforums.org/showthread.php?t=202834&highlight=wmp300n)


Are there any other setting you would recommend trying to get N speeds?

How can the network manager GUI to work with my current setup?

Thanks for any help.

---

### Post by kenhen93 on 2009-12-11
Can anyone offer any help please?

---

