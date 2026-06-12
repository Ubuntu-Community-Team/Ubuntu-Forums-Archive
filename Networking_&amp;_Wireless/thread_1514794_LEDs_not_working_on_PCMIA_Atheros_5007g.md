---
title: "LEDs not working on PCMIA Atheros 5007g"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by bobnutfield on 2010-06-21
Hello Everyone, 

This one is not really a big deal.  More of an irritant than anything else.
I use a PCMIA wireless card in one of my laptops running Lucid, and it works well.  However, the LED lights on the card (power and traffic) do not work and never have with Ubuntu.  They do, however, work with other distros (Fedora, Knoppix, etc.)  I had this trouble with my Acer Aspire One which also uses an Atheros chip and installing the wireless backports fixed it there, but has had no effect on this laptop.

I am just curious if anyone knows what I can do to start investigating this.  I saw nothing in the wireless config files of the other distros that would suggest why it works there and not in Ubuntu.

lshw yields this:

```
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-23-generic **[COLOR="Red"]firmware=N/A[/COLOR]** ip=192.168.1.37 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:68000000-6800ffff
```

I am guessing that the lack of firmware is the answer, but where does one get firmware if it is not included in the module?     

Any thoughts appreciated.

---

