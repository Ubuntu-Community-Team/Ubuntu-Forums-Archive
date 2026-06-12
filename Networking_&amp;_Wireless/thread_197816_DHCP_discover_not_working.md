---
title: "DHCP discover not working"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by JKing on 2006-06-16
I'm using the native BCM43xx driver with a 4306 device (Linksys PCI WPC54G rv2 to be exact), and I can apparently get the interface configured properly (I grabbed the experimental firmware package and installed it; iwconfig seems to show that everything is fine once I set the access point to "any" (otherwise it reports it as "invalid")).  However, when I try and bring the interface up, DHCP discovery doesn't work, retrying several times without printing any errors until it finally gives up.

Would I have better luck with fw-cutter?  With an updated kernel (I'm using the stock one that came with U6.06)?  With ndiswrapper?  I elected to use the firmware package instead of fw-cutter because I have no wired network connection available to me and so can't use tools like apt-get and whatnot until I actually get this working.  This makes troubleshooting very slow and frustrating. :(

Any advice would be great appreciated.

---

### Post by jawrat on 2006-06-16
hi, i had the same problem with my 4306.  try two things.

1) set a static ip for the interface ... just set it once, make sure it works, and then run dhclient ethX (whatever your interface is).  that worked for me.

2) try rebooting your router.  for some reason, mine was caching the connection and wouldn't release it.  

keep tryin, you'll get it.

---

### Post by JKing on 2006-06-16
[QUOTE=jawrat]1) set a static ip for the interface ... just set it once, make sure it works, and then run dhclient ethX (whatever your interface is).  that worked for me.[/QUOTE]
How do I do this?

---

### Post by noname101 on 2006-06-16
Go to System | Administration | Networking then click your device and click Properties.

---

