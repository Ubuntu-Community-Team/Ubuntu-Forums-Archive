---
title: "Error connecting to wireless via command line"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by Alexander D. Gray on 2011-04-06
Hello everyone,

I've been familiarizing myself with the command line and am attempting to connect to a wireless network but am getting stuck at the point wherein I need to put in a password.

When I run iwconfig I see my card is wlan0

So I run

iwconfig wlan0 essid [Network Name]

Then I run

iwconfig wlan0 key s:[password]

Where [Network Name] is the name of my network and [password] is my password respectively (no brackets are used in the command).

When I run the second command I get:

Error for wireless request "Set encode" (8B2A)  :
     SET failed on device wlan0 ; Invalid Argument.

I definitely know my password as I can connect using a GUI. The encryption method for my network is WPA2.

Could someone tell me how I could connect to a WPA2 secured network via a command line, and/or where I went wrong with what I've been trying?

Thanks!

---

### Post by flash63 on 2011-04-07
Hello,
> The encryption method for my network is WPA2.
edit the configuration-file **/etc/network/interfaces**

```

auto lo
iface lo inet loopback

auto wlan0 
iface wlan0 inet dhcp
     wpa-driver wext
     wpa-ssid [COLOR="Red"]Your_SSID[/COLOR]
     wpa-ap-scan 1
     wpa-proto RSN
     wpa-pairwise CCMP
     wpa-group CCMP
     wpa-key-mgmt WPA-PSK
     wpa-psk "[COLOR="Red"]Your_WPA-Key_ASCII[/COLOR]"

```
This is one way. 

Second alternative way:
```
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]Your_SSID[/COLOR]
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0
```
```
sudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```
```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

network={
ssid="[COLOR="Red"]Your_SSID[/COLOR]"
scan_ssid=1
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk="[COLOR="Red"]Your_WPA-Key_ASCII[/COLOR]"
}
```
Restart the Configuration now:
```
sudo /etc/init.d/networking restart
```
Both methods use wpa_supplicant.

---

