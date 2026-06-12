---
title: "WICD help"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2010-01-18
Hi, I tried looking in the WICD forums for the answer to my problems to no avail and they're not accepting new registrations so I'll ask here.

I installed WICD (and uninstalled network manager) on my netbook.  I am able to connect to my wireless router, I get a valid IP address, am able to connect to other computers in my LAN and to the router for adminnistrive purposes, but I CANNOT connect to the internet.  I'm using Karmic if that matters.

Also, WICD is showing 100% strength connection to the router no matter how far I move from it.  This is happeingin in 1.6.2.2 and 1.6.1

ANY help would be GREATLY appreciated!

---

### Post by wewantutopia on 2010-01-18
Any WICD experts out there?

I'm using an eeePC 1000H with a RaLink RT2860.  The driver in use is rt2860.

Thank you!!

---

### Post by wewantutopia on 2010-01-18
Ok, I got it fixed!!!!

Learned of /var/log/wicd/wicd.log Everything was working just fine except for this one line: [COLOR=Black]/etc/resolv.conf must be a symlink

after reading here:  [http://whatdoesthiserrormean.com/errors/2838](http://whatdoesthiserrormean.com/errors/2838)

and doing this:

[/COLOR]1. Back up your existing resolv.conf file (just in case): ‘sudo mv /etc/resolv.conf /etc/resolv.conf.backup’
2. Create a symlink to /etc/resolvconf/run/resolv.conf: ‘sudo ln -s /etc/resolvconf/run/resolv.conf /etc/resolv.conf

I disconnected from my router and reconnected and viola!

Hope this helps some one else. :)

---

