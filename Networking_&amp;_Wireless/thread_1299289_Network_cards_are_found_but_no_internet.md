---
title: "Network cards are found but no internet"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by bud_man on 2009-10-23
I'm having some trouble with trying to get wireless internet in Ubuntu Studio 9.04. The weird thing though is that it knows the IP address and gateway and I'd open the terminal and put in 
> iwconfig 
or
> lshw
it displays information about that router but, when I open the applet properties, it says that wlan0 is disconnected. As of now I'm using Ubuntu 9.04 and every time I go back to Ubuntu Studio to try to fix the internet, it seems like I'm getting nowhere! I even tried reinstalling it and still no progress...help!
Thanks!

---

### Post by mojorising on 2009-10-23
Maybe try setting things up directly via wpa_supplicant.conf and see what happens.

Configuration is actually really simple. Use this page for guidance:

[http://linux.die.net/man/5/wpa_supplicant.conf](http://linux.die.net/man/5/wpa_supplicant.conf)

If that works, at least you're up and running while you try to work out what's up with network-manager or whatever the trouble really is.


Mike

---

### Post by bud_man on 2009-10-24
Alright, I'll try it out!

---

### Post by bud_man on 2009-10-25
I almost got it working but it didn't seem to work for whatever reason. Oh well. I found out that you can actually make Ubuntu into Ubuntu Studio simply by going to Synaptic and looking up "Ubuntu Studio" and mark the software for it and any other additional software you want.
Rock on!
:guitar:

---

