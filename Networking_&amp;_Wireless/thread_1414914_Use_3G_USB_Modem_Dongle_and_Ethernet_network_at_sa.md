---
title: "Use 3G USB Modem Dongle and Ethernet network at same time"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by unteer on 2010-02-24
Hey Folks,

I currently have a computer sitting underneath a router/switch on a Local Area Network that I want to connect to the Internet using a 3G USB dongle modem.  If I am connected to the ethernet and then enable the modem connection, only the ethernet LAN side works.  If I enable the modem and then enable a (disabled) ethernet connection, only the ethernet LAN side works.  If I keep the ethernet disabled and connect using the modem, I can get out onto the Internet, but obviously not the LAN.  I need to be able to do both.

I have a feeling it has something to do with my routing tables, but I couldn't find a simple answer of: send everything within this IP subnet to the ethernet, and send everything else to the modem.

Suggestions/help/walkthroughs?

Cheers!

---

### Post by alexfish on 2010-02-24
Hi

there is a thread here

[http://ubuntuforums.org/showthread.php?t=1384085&highlight=internet+share](http://ubuntuforums.org/showthread.php?t=1384085&highlight=internet+share)

---

### Post by unteer on 2010-02-24
That is great for sharing connections, but I did not want to share them, as that would enable other machines to acces the Internet, which in my situation, would not be a good thing.

However, following the steps in the other thread led me to realize that I must have changed some settings from before I left for a long holiday, which is why this all stopped working in the first place.

It turns out, that if configured correctly, Ubuntu can handle rewriting the routing tables correctly, especially if you enable your ppp0 connection before the eth0 connection.  My settings were not working because I had adjusted some settings to point all traffic at the routing box, which is just dumb.  I reverted everything to default settings, and now my normal, "connection dance," works again.  namely, I need to disable ethernet, connect ppp0, then re-enable ethernet and now my computer can talk out both sides of it's mouth, err, NICs.

---

