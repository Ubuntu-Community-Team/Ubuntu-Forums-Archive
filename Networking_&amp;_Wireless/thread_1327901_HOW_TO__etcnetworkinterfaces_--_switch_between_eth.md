---
title: "HOW TO:  /etc/network/interfaces -- switch between eth0 and wlan0"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by SierraDump on 2009-11-15
I am setting up a media pc - its a tiny little desktop. And will take it many places.  Some with Ethernet and other places with NO ethernet but WiFi instead.  I only have a minimal install of ubuntu jaunty so no GUI (gnome/kde).  I will need to set this all up via command line.

The PC has both a Ethernet AND WiFi card.  

A.)  How do I setup the wireless card to automatically turn on and join a network? What if i have 2 ssids and I want it to pick between the two? I set it up and seems to be working by adding the WiFi section to my /etc/network/interfaces file but don't know how to have it pick which of 2 ssid is stronger and automatically switch to that one.  

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


### I added this section###
# The wireless network interface
auto wlan0
iface wlan0 inet dhcp
wireless_mode Managed
wireless_essid wifissid
wireless_key 1234567890 # is this how you add a wep key? its ASCII i think?
wireless_rate 54G
wireless_channel auto


```



B.) 

I am trying to figure out how I can setup the networking so that it uses ethernet(eth0) ONLY if a ethernet cable is plugged in.  And if NO ethernet cable is plugged in; then it will use WiFi(wlan0). 

IN OTHER WORDS, I WANT ETHERNET TO TAKE PRIORITY... So if WiFi is available, but there is a ethernet cable plugged in - I don't want the WiFi interface to come up.  (because obviously if no ethernet cable is plugged in, it won't get an IP)

Do I set this up in /etc/network/interfaces???

---

