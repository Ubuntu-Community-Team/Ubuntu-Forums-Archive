---
title: "wpa_supplicant help"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by chaospilot on 2011-09-03
I originally posted this in the general help area because i didnt see this forum, so im moving my question here. Sorry for the double post, ill delete my first one. 

 im trying to set up my laptop to connect to my router. Im having some issues that i cant seem to find answers to. Ill start from the beginning.

my iwconfig is : 

> :
lo no wireless extensions
eth0 no wireless extensions
wlan0 IEEE 802.11agb ESSID off/any
Mode: Managed access point : Not-Associated Tx-Power=15 dBm
Retry long limit:7 RTS thrff Fragment thrff
power managementff

So i set up my wpa_supplicant conf file in my /home/lo-fi/wpa.conf and it looks like this :

> :
ap_scan=1
network={
SSID="cindy1"
scan_ssid=1
proto=WPA RSN
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
#psk="mywepkey"
psk=a huge set of letters and numbers

so then i run the command
> :
sudo wpa_supplicant -Dwext -wlan0 -c/home/lo-fi/wpa.conf -dd

and my output is this (sorry i dont know where it starts exactly as it moves too fast, and im manually typing this out because i cant copy and paste, using a different computer) : 
> :
Selecting BBS from priority group 0
try to find WPA-enabled AP
0: long hex string ssid="cindy1" wpa_ie_len=0 rsn_ie_len=0 caps=0x11
skip - no WPA/RSN IE
no suitible network found

there is alot more, but im hoping this is what is needed to be seen. 

So i guess its saying that my router isnt using WPA, but i have a WEP key, which im using on my windows machine. And when i use windows to i can see that it says there is no security type, but i still have a WEP key that i used to connect. 

well i supposed this is a decent place to start. I have changed my wpa.conf to 
> :
ap_scan=2
network={
SSID="cindy1"
scan_ssid=1
proto=WPA RSN
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
#psk="mywepkey"
psk=a huge set of letters and numbers

and i get a smiliar result, mainly being as an error
> :
no keys configured - skip key clearing


well im sure i havent provided enough info, as i had to cherry pick with my extremely limited knowledge what to post. If anyone has any ideas i'd be very glad to hear them.

---

