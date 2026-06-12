---
title: "Maverick has Problems with UMTS after longer idle time"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by night-wing on 2011-02-15
Hello.

I use a thinkpad x60 with a UMTS - Karte Option Globetrotter GT II Max Qualcom 3G CDMA, PCMCIA for my internet connection via umts.
In ubuntu 8.10 this worked perfectly. In 10.10 I have the problem, that I can't re-establish a connection after the computer wasn't used for some ("idle") time. The problem also exists, when I use an umts usb - stick instead. Does somebody have any hints for me?

The computer goes not in standby or suspend. It's simply idle for some time. When I remove the card and re-insert it, it works again after some minutes.

Regards
nightwing

---

### Post by night-wing on 2011-02-17
*bump*

---

### Post by hermes85pl on 2011-02-28
I believe I have similar problem with my built-in ethernet. Just updated network-manager and pm-utils. Hope those will help.

---

### Post by alexfish on 2011-02-28
> **night-wing said:**
> Hello.

I use a thinkpad x60 with a UMTS - Karte Option Globetrotter GT II Max Qualcom 3G CDMA, PCMCIA for my internet connection via umts.
In ubuntu 8.10 this worked perfectly. In 10.10 I have the problem, that I can't re-establish a connection after the computer wasn't used for some ("idle") time. The problem also exists, when I use an umts usb - stick instead. Does somebody have any hints for me?

The computer goes not in standby or suspend. It's simply idle for some time. When I remove the card and re-insert it, it works again after some minutes.

Regards
nightwing

Try

```
sudo killall modem-manager
```wait for the device to settle
see what happens

if problem persistent, log bugs to (modem-manager)

alexfish

---

