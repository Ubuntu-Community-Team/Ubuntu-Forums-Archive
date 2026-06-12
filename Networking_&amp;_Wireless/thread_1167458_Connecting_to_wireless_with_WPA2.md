---
title: "Connecting to wireless with WPA2"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by squirrelplayingtag on 2009-05-22
I'm trying to set up mythbuntu to connect automatically to my schools wireless network. The only way to do this is to use the "secure" one which uses WPA2-Enterprise. I can enter the correct values when I choose edit connection with the network manager but when I click to connect it bring up the message box saying authentication is required by the wireless network but only has options for WEP.

I tried manually installing wpa_supplicant and I used the same file I use on my laptop to connect which has no problems. Then I ran
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -D wext -i wlan0 -c /etc/wpa_supplicant.conf -dd 
```

But then I get:
```

00:1c:57:42:4a:62 ssid='umd-secure' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 skip - non-WPA network not allowed
```

which is the correct ssid, and is a WPA network.


The network adapter is a microsoft broadband networking wireless usb adapter model mn-510(Prism II based).

---

