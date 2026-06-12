---
title: "Setting up WiFi Radar for WPA"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by tirofiban on 2006-06-19
Hello,

I did some searches and I didn't find anything on this topic.

I would like to try WiFi Radar instead of Network Manager on Dapper. It's probaby a dumb question, but how do I set Wifi Radar up for WPA?

Under the WiFi profile, it say Use WPA Driver. 

What driver is it refering to? 

Also I'm using NDISWRAPPER.

Thanks,
Marc

---

### Post by jarocooke on 2006-07-29
I would like to know what that option is about as well.

Did you find anything out about it?

---

### Post by wislon on 2006-07-30
I came across an answer to this accidentally, in another link which I've lost :(. The example was actually of a wifi radar configuration file. In the 'driver' part, it had next to it 'wext' (the generic wireless extensions driver). 

Personally I haven't been able to get wifi radar to work with WPA, even trying with 'wext' and 'ndiswrapper' as my driver settings. 

Using wifi radar, it associates with the access point, at which point my laptop locks up so hard I have to pull the battery out in order to get it reset. It's a real PITA.

At the moment, I actually run wpa_supplicant from a script to get it all to work, but it's still flaky, and requires a wlan0 reinitialisation from the control panel under 'System' to get it working again.

Anyway, HTH :)

---

### Post by wislon on 2006-07-31
[Update]
I found a way to finally get wifi-radar working without crashing and locking up. I set the WPA driver to be 'ndiswrapper' (no quotes), and removed the 'auto wlan0' line from my '/etc/network/interfaces' file. I have a static IP address set for my wlan0 interface, so I left that stuff alone. It now appears rock solid. I have tried using 'wext' in the box as well, and it also seems to work.

My network connectivity indicator initially comes up and tells me I don't have a wireless network adaptor, but as soon as I run the wifi-radar, and connect to my access point, I suddenly do. So much smoke and mirrors in this linux thing!

I do NOT start wpa_supplicant at all now, wifi-radar seems to take care of everything.

Also (I don't have my laptop here, it's at work, so I can't confirm right now), but I seem to remember setting my WPA settings in the wifi-radar config file (I think it's under '/etc/wifi-radar.conf.'? However this was done a while ago, when it was still crashing. I doubt it's collecting my shared key and stuff from wpa_supplicant configuration.

I also don't have anything running pre- or post-wifi-radar connection (down near the bottom).

Hope this helps someone too! :)

---

### Post by awaldram on 2006-07-31
you need wpa_supplicant working your wpa_supplicant.conf should look somthing like

cat /etc/wpa_supplicant/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=admin
network={
ssid="Pegasus"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
group=TKIP
psk="mysecretkey(not any more)"
}


then just need you network id and wext in the wifi-radar gui.

hint ---- wifi-radar -d 

will connect to the first available network in your wifi-radar setup

---

