---
title: "trying to get Ubuntu Lucid to be wifi AP"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by hrickh on 2011-09-03
I've been at this for a couple days now, and feel like I'm going in circles. I need a third perspective to get this working.

Here's the scenario:

I have an Android tablet that I would like to pair to my laptop for internet access. The laptop has two wireless cards, one going out to the internet and the second card not in use.

Android (1.6) has made this particularly difficult because it doesn't allow ad-hoc networks. So I've tried all sorts of different combinations of dsnmasq-base/hostapd, dhcp3-server, whatever I've been able to read up on.

I even found a nifty little utility written in Groovy/Java here: [http://blog.mycila.com/2010/09/turn-your-wifi-card-in-access-point-to.html?showComment=1315061384118#c7725074442825642120](http://blog.mycila.com/2010/09/turn-your-wifi-card-in-access-point-to.html?showComment=1315061384118#c7725074442825642120) that looks like it should be something really simple, but for whatever reason, I'm not getting IP addresses served.

My two wifi interfaces are; Alfa Network USB AWUS036H (works great, BTW) and the second card is an Atheros5K card, which I'd like to use as the secondary I/F to serve out IP addresses. I have a suspicion that the Atheros card doesn't support master mode, although the docs tell me it does.

Has anyone out there gotten something like this to work?

Thanks in advance.

R.
==

---

### Post by hrickh on 2011-09-04
Okie Dokes...

Got it working!

I found a really simple, easy to follow guide here: [http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/](http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/)

I ran into a problem with WPA authentication, though. While it would authenticate, it wouldn't stay authenticated for very long. So I ended up with an open AP. Not a huge problem, since this particular setup is in the middle of the woods with no one around for a mile or so.

Anyway, hope this guide on Vivek's blog helps others as it did me.

R.
==

---

### Post by northd_tech on 2011-09-04
I don't think my Broadcom STA driver will even go in master (or monitor) mode.  Anyway, I just wanted to add the Ubuntu Wireless Access Point documentation page for other readers if they might find it helpful:

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

Glad you got it figured out though.

---

### Post by hrickh on 2011-09-05
> **northd_tech said:**
> I don't think my Broadcom STA driver will even go in master (or monitor) mode.  Anyway, I just wanted to add the Ubuntu Wireless Access Point documentation page for other readers if they might find it helpful:

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

Glad you got it figured out though.
Yeah, I'd seen this documentation - one of the first places I looked. For me, it was needlessly complex.

The doc that got me up and running (linked in my second reply) was easy to follow. That may be, of course, due to the previous headaches trying to follow the labyrinth of docs available out there without success, and by then I was already familiar with most of the bits needed.

R.
==

---

