---
title: "No Roaming in Intrepid"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by degroof on 2009-01-24
Posting this here in case others are having similar issues...

I've got an Acer 5920 laptop with 3945ABG wifi. After upgrading from Hardy to Intrepid, the NetworkManager applet stopped showing me any valid wireless connections. I was still connecting to my home wifi network without any problems, so I didn't think much of it. 

Today, I took my laptop to another location and, no matter what I tried, I was unable to connect to their wifi network. When I got home, my laptop immediately connected to my home network. 

Just for kicks, I attached a D-Link adapter to a usb port. The NetworkManager applet immediately recognized it and listed my network along with two others in the neighborhood. The built-in wifi adapter showed up as "device is unmanaged" and doesn't list any networks.

I eventually tracked the problem down to /etc/network/interfaces which contained these lines:

```
iface wlan0 inet dhcp
wireless-essid sd
auto wlan0
```

Since "sd" is the name I use for my home wifi network, I realized that somewhere along the way my built-in wifi was hard-coded to my location (I don't remember doing that). I commented out these 3 lines and restarted my laptop. Now both the built-in and usb adapters were listing the neighborhood networks.

---

