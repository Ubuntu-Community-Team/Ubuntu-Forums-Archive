---
title: "TP-Link Wireless Adapter (USB) on 11.04 - not connecting to network"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by neogarfield on 2011-05-19
Hello all,

i just installed Ubuntu 11.04 64bit on my desktop. i have a TP Link TL-WN321G (Ver 4.0) wireless usb adapter to connect to my wireless network (i used to use it with Windows XP). As expected (i'd read up a bit before installing Ubuntu), the adapter was autodetected - i could see my wireless network listed in the networks list dropdown, and lsusb showed it too.

lsusb identifies "Bus 002 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter"

But i cannot connect to the network. When i select my network, it keeps trying to connect, but never succeeds in connecting.

i tried going through the forums for possible solutions, but most of them deal with how to get it working when the adapter is not detected, or when networks are not shown. Or they are for older Ubuntu versions.

i use the same wireless network on my laptop (Ubuntu 9.04), and it has a WPA & WPA2 Personal security, with a password, which i've configured in the desktop as well.

Any help is greatly appreciated! i'm not an advanced linux user, and do not know to use the terminal well, so please elaborate responses to beginner levels :) Thank you!

---

### Post by neogarfield on 2011-05-19
My apologies! i've solved the issue myself. i found the solution which finally worked on this German website. For anyone facing the same problem, check out
[http://forum.ubuntuusers.de/topic/inbetriebnahme-tp-link-tl-wn321g-wlan-stick/#post-2804142](http://forum.ubuntuusers.de/topic/inbetriebnahme-tp-link-tl-wn321g-wlan-stick/#post-2804142)

Or the translated to English version-
[http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Finbetriebnahme-tp-link-tl-wn321g-wlan-stick%2F%23post-2804142](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Finbetriebnahme-tp-link-tl-wn321g-wlan-stick%2F%23post-2804142)

(please refer back to the original German version for the content given in code - Google Translate messes it up a little)

Cheers and thanks!:popcorn:

---

