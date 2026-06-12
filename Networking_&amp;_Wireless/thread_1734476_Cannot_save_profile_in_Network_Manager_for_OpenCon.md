---
title: "Cannot save profile in Network Manager for OpenConnect"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by ybbon66 on 2011-04-20
I am running 64-bit 10.10, installed OpenConnect v2.22-1 and that works fine, I can connect to my corporate VPN no problem, which is more than can be said for the Cisco AnyConnect which behaves badly in oh so many ways.

Anyway, OpenConnect installed and working fine. I want to use Network Manager to create a VPN connection but although it can see OpenConnect as a VPN connection, if I try to create a new VPN profile the apply button remains greyed out so I can't save it. 

I'm using Gnome not KDE. It's not a big deal as I just created a desktop launcher instead but it would be quite nice to have the NM working too. Anyone seen this at all?

---

### Post by dwmw2 on 2012-05-21
A year later, I've *just* seen your question. If you'd posted it to the openconnect mailing list as described at [http://www.infradead.org/openconnect/mail.html](http://www.infradead.org/openconnect/mail.html) you'd have got a much quicker answer. Are you still having this problem?

If the Apply button remains greyed out, that implies that you haven't given it all the information it needs to be a valid connection. Which is odd, since it doesn't really need much; mostly just the hostname of the server. If you still have a problem, please send mail to the mailing list, or just to me if you prefer, showing exactly what you have entered into the configuration when it didn't let you hit 'apply'. Usually when something does that, it's useful to just try entering *dummy* information into various fields, until the 'apply' button lights up. Then you know what it thinks it's missing, and can try to find a more sensible entry for that field...

---

