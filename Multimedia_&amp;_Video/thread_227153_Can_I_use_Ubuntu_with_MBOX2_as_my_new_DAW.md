---
title: "Can I use Ubuntu with MBOX2 as my new DAW"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by atoni on 2006-08-01
Can I use my MBOX2 device with Ubuntu for example with Ardour?

---

### Post by drycellbattery on 2006-08-01
I'm not sure if that would work, it would be nice if it could. In the windows and mac world the best DAW for using Digidesign hardware is Motu Digital Performer. Cubase, Logic, etc are limited or don't support Digidesign hardware at all. I know that 3rd party hardware controllers can control Pro Tools to a certain degree by using HUI protocol. Perhaps if Ardour understands HUI it may work with a Mbox. I'm going to google this... brb.

---

### Post by drycellbattery on 2006-08-01
It seems that there is no ALSA support for Digidesign gear. The mbox and mbox2 use their own proprietary protocol and not a generic usb-audio one.

[http://ardour.org/node/192](http://ardour.org/node/192)
[http://www.ferventsoftware.com/index.php?option=com_content&task=view&id=27&Itemid=82](http://www.ferventsoftware.com/index.php?option=com_content&task=view&id=27&Itemid=82)
a small list of some supported hardware.

If you really want to use linux audio then I suggest getting another interface. Do you use a laptop? There are supported usb interfaces but firewire are a little trickier. There's a project called freebob, and I hope it makes it's way into the next Ubuntu release. Cardbus interfaces are supported too, and if you're able to shell out a lot of cash, give the RME Multiface 2 a look (you'll have to buy the cardbus in addition to the interface).

I'd hold on to the mbox2 as well as keeping your windows partition with Pro Tools LE. Having Pro Tools and knowledge of using it efficiently is important these days if you want to record other people's stuff or look for a studio job.

---

