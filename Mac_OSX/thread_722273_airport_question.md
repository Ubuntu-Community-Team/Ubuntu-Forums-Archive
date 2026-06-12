---
title: "airport question"
date: 2008-03-12
forum: Mac OSX
---

### Post by BomarJr on 2008-03-12
i have a question about airport. i'd like to find out though my computer if someone is using my airport for internet. how can i do this?

---

### Post by scramasax on 2008-03-12
> **BomarJr said:**
> i have a question about airport. i'd like to find out though my computer if someone is using my airport for internet. how can i do this?

I haven't got that particular router, but if you surf to the router, as you would when configuring it, you should be able to see the connected devices.

But you should just set up WPA encryption for the wireless signal with a pre-shared key.  Then no-one can use your connection unless they have the key.


Hard to find much documentation on setting  the Airport up to use a pre-shared key.  But there's this:

[http://docs.info.apple.com/article.html?path=AirportWin/4.1/en/apw95.html](http://docs.info.apple.com/article.html?path=AirportWin/4.1/en/apw95.html)

There's also this:

[http://world.std.com/~reinhold/airport.html](http://world.std.com/~reinhold/airport.html)

Basically, no encryption means you're wide open.  And the older version WEP is totally broken, so that it is no barrier to anyone.  Use WPA.  Choose a good long key.  Anything up to 63 characters is usual.  I'd use *at least 12* and make 'em random.  Save the password in a textfile and you can move it to any machine you want to connect to your network on a USB thumbdrive.

---

### Post by cprofitt on 2008-03-13
Most routers allows for web administration... not sure about the AirPort. If the router is both wired and wireless it usually only allows administration via the wired ports. From reading it sounds like you must use the Airport Extreme Utility (supposed to be on the CD that came with the AP). This then allows you to set the level of security you want, add the password, etc. [http://www.apple.com/airportextreme/features/security.html](http://www.apple.com/airportextreme/features/security.html)

This link might help as well -- [http://www.vonwentzel.net/ABS/Configuration/OSXExtreme/](http://www.vonwentzel.net/ABS/Configuration/OSXExtreme/)

The AirportExtreme supports the following security measures:

Security:
Wi-Fi  protected   Access  (WPA/WPA2)
Wired  Equivalent   Privacy   (WEP)   64-   bit,   128-   bit   encryption  
MAC  Address  Filtering
NAT Firewall
Support  for   RADIUS  authentication
802.X,PEAP,LEAP,TTLS,FAST
Time-base  acces  control

WEP is near useless, but typically the easiest to setup. If you are in a low vulnerability area then you could go with this, but I prefer setting the minimum bar at WPA. Personally a combo of MAC Address Filtering and WPA should be good enough for most home users.

The first step is to change the default admin password - that is an absolute must.

---

