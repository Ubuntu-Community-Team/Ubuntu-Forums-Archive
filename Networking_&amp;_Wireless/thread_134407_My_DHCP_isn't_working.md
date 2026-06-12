---
title: "My DHCP isn't working"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by VirusScanner on 2006-02-21
I posted here a couple weeks ago about trying to get my wireless card working (netgear MA111), which I did to an extent with ndiswrapper or prism2_usb, honestly I have no idea which, but somehow the system recognizes it now.

It is supposed to receive an IP address via DHCP from my DSL modem, which hasn't been working. dhclient gives me lots of "no lease found" or something like that, and the IP address remains 0.0.0.0.

So my question is; has someone found this problem before and found a way to fix it?

---

### Post by newuser111 on 2006-02-21
"sudo ifdown wlan0" then "sudo ifup wlan0"

---

### Post by atomicmoose on 2006-02-22
Had a similar problem here: [http://ubuntuforums.org/showthread.php?t=133055](http://ubuntuforums.org/showthread.php?t=133055)

Take a look.

---

### Post by VirusScanner on 2006-02-26
Thank you everyone. I have it working now, with the prism2_usb driver. Since windows stopped recognizing the ext3 partition I had for programming, I think I'll stop regognizing windows ;)

---

