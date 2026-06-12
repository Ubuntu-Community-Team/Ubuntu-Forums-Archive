---
title: "wpa2-aes???"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by emmiesix on 2010-05-16
Does anyone have a way to use this type of encryption?  I have read many posts but have not gotten a solution yet.  

I am trying to get this to work at a friend's house.  I know the SSID and the super-long ascii code (with symbols?).

gnome nm and wicd have been useless.

I have been connecting to my school's wpa2 using wpa_supplicant + dhclient directly, so I tried adding it in there:

network={
ssid="name"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk="horribly long thing"
}

What happens is a string of connects and then immediate disconnects when runnign wpa_supplicant.  It says "CTRL-EVENT-DISCONNECTED - disconnect event - remove keys" then starts all over.  Can't get a stable connection but I must be close???

---

### Post by DouglasAWh on 2010-05-20
I'd like to know this too...

---

