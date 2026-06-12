---
title: "ra0 and netspeed applet"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by tezer on 2009-10-21
Hello everyone

I just installed a D-Link DWA-140 USB Wi-Fi card, which works just fine. To my surprise I don't have an expected wlan0 connection, but ra0. What is ra0 and how does it differ from wlan0?
Everything is fine, but I found one bug. The netspeed applet works fine after boot. But once something happens to the ra0 connection, the applet fails to find it again and instead shows the eth0 connection that does not exist. In the Preferences the interface type selection is greyed and shows only eth0. I have to remove the applet from the panel and start it again so that it could pick up the right interface.
So what's happening?

By the way, my conky stopped working, whatever I do it doesn't start. Might it be a result of the wlan0 to ra0 migration?

Thanks in advance.

---

### Post by proxess on 2009-10-22
Maybe in your *Conky* you've got in the variables *wlan0*. Change it to *ra0*.

Or you could try and make a link of your */dev/ra0* (or wherever it's situated) as */dev/wlan0* (or wherever it's meant to be situated, definitely where *ra0* is).

---

### Post by tezer on 2009-10-22
conky is OK now. But what's wrong with the applet?
And what's the difference between the ra0 and wlan0?

---

