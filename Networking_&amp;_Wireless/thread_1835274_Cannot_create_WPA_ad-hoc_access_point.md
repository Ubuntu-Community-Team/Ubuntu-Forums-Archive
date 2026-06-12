---
title: "Cannot create WPA ad-hoc access point"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by Jargon64 on 2011-08-29
Hey guys,

I've searched around and tinkered with the config files for a few hours with not much success. I'm trying to get my Acer Aspire Revo to share its wired Internet connection over its wireless card (an Atheros AR928X according to lspci). I'm running Lucid Lynx (10.04).

I haven't even got to the bridging yet as I cannot, for the life of me, get the wireless card to create a WPA ad-hoc access point. I've followed several different tutorials on how to get it to work with no luck. I've got to the point where I'm getting no errors, which has made things a little harder to troubleshoot. I'd prefer to get WPA2 working but any WPA would be acceptable right now. I'm certain the card supports both as a quick *iwlist wlan0 auth* yields the following:
```

wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP

```
I don't want to use the network managers to do this (not even sure it can) and have been trying to get it all configured with */etc/network/interfaces* and */etc/wpa_supplicant.conf*. My latest efforts have been restricted to */etc/network/interfaces* which now contains:
```

auto wlan0
iface wlan0 inet static
address 192.168.2.1
network 192.168.2.0
netmask 255.255.255.0
#gateway 192.168.2.1
broadcast 192.168.2.255
wireless-essid MySSID
wireless-mode ad-hoc
wireless-channel 6
wpa-driver wext
wpa-mode 1
#wpa-frequency 2412
#wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-ssid MySSID
wpa-psk <KEY>

```
As mentioned above, this yields no errors but after running a network restart I'm greeted with:
```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

```
If anyone can point me in the right direction, I'd be most grateful :) It seems to be that most of the WPA forum posts and tutorials out there seem to be a few years old now anyway, so I'm not even sure if I'm following the right information! D:

Cheers!
Jargon

---

### Post by praseodym on 2011-08-29
Hi,

your static IP-address is you router-IP?! Imho Ad-Hoc only works with WEP under Ubuntu so far.

---

### Post by Jargon64 on 2011-08-29
Nah, the router/gateway is 192.168.1.1. The 192.168.2.1 is for a new subnet that will be created for the purposes of sharing the wireless.

And are you sure WPA isn't supported? I've seen tutorials and other sites claiming it does... but then again I can't get it working xD

---

### Post by praseodym on 2011-08-29
You may have a look at the google-translation of the german wiki-site:

[http://translate.google.de/translate?js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FInternetverbindungsfreigabe](http://translate.google.de/translate?js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FInternetverbindungsfreigabe)

The red box!

---

### Post by Jargon64 on 2011-08-29
I'm not sure if that is confirming that it does or doesn't work... looks like it says the hardware and drivers have to support it in order for it to work and I'm fairly sure the Atheros card does support both WPA and WPA2. Unless I'm missing something?

---

### Post by praseodym on 2011-08-29
Maybe with a driver update from linux-wireless (compile?).

---

### Post by Jargon64 on 2011-08-29
Looks like I was looking in the wrong place.

I was browsing around that linux-wireless site and stumbled across [HostAP]("http://linuxwireless.org/en/users/Documentation/hostapd"), after a quick read and some frantic configuring, I now have a WPA2 access point hosted from my Revo and the bridge is up and running smoothly (providing Internet access to my gf's laptop).

Cheers for the help :)

---

