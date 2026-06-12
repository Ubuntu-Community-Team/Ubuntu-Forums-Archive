---
title: "Connecting to Unsecured Wireless Needs Authentication Details??"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by Crii on 2013-01-24
I'm attempting to connect to an unsecured wireless service in my apartment building. This is easy enough in a GUI environment with a browser, if you're not logged in, a window pops up in your browser asking for your credentials (username, password) which submits that via php post/get off to their magical servers somewhere and you are granted access.

I'm stuck trying to connect to this service with ""Command Line Ubuntu Sever"".

I took the time to figure out the URL+PHP submitted to authenticate, which thanks to some university papers wasn't overly difficuly. So submitting the following url, with my details does actually grant access.

[http://internetService/login?username=MyName&password=MyPass](http://internetService/login?username=MyName&password=MyPass) 


How the heck do I use this in conjunction with Ubuntu server to login to this service manually or even better automatically.

I've already set the wireless interface wlan0 in /etc/network/interface, so i'm connected to the AP, just have no idea where to go from here.


Interfaces
----------
# The wireless card.
auto wlan1 <--------- yeah i use wlan1 and not wlan0 :)
iface wlan1 inet dhcp
wireless-essid   ImJustNotTelling
wireless-mode    managed

EDIT: Whilst being connected to the AP, I was messing around and just used 'wget [http://internetService/login?username=MyName&password=MyPass](http://internetService/login?username=MyName&password=MyPass)' and that got me connected, but i'm sure that's a horrible way to do this...

---

### Post by Cheesemill on 2013-01-24
> **Crii said:**
> EDIT: Whilst being connected to the AP, I was messing around and just used 'wget [http://internetService/login?username=MyName&password=MyPass](http://internetService/login?username=MyName&password=MyPass)' and that got me connected, but i'm sure that's a horrible way to do this...
I was going to suggest this as a solution when I started reading through your post, I don't see anything horrible about it.

---

