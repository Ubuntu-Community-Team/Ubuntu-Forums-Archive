---
title: "BCM4306 can see AP, but cannot connect"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by jjoseph8008 on 2009-11-14
I have the below wireless card on my hp zd8000 laptop with ubuntu 8.04 and have problems getting it to connect to my linksys wireless-g router. Please help.

0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

The wired network connection works fine. Below is some information, but I should admit that I am not very familiar with ubuntu. The wireless is configured for "mixed, channel 6, wpa2 personal aes"

I am able to see my wireless AP from the laptop, but it does not get an IP

Output from iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"truwe"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:7E:4F:B4:BC   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=85/100  Signal level=-44 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Below is from /etc/network/interfaces

iface wlan0 inet dhcp

wireless-channel 6
wireless-mode managed
wpa-psk b06efae2680c04af4a7f721ed39242d8f3102668e1c3b8881d0a89dba465sad85
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid trume

Please advise.

---

