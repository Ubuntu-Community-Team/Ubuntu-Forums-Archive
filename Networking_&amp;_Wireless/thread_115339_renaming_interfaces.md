---
title: "renaming interfaces"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by wpollans on 2006-01-10
As a result of a response I got in a different thread, "very slow network configuration", I realize that for some reason my network interfaces seem to be named incorrectly.  I'm running on a Dell 700m laptop - My wireless interface is called 'eth0' rather than 'wlan0' and my ethernet interface is called 'eth1' rather than 'eth0'.  My Breezy install is about a month old.

My iftab is:

     eth0 mac xx:xx:xx:xx:xx:xx
     eth1 mac yy:yy:yy:yy:yy:yy

Is it sufficient to change the names in /etc/iftab?
If so, what do I enter for wlan0?
If not, how do I do this?

I want to do this without hosing my current installation of everything else  :-)

By the way, the wireless seems to work OK the way it is.  My initial problem was (and still is) that it takes 30-40 seconds to configure the interfaces.
Thanks

---

### Post by wpollans on 2006-01-10
OK, apparently editing iftab is all that's required (also edited interfaces file) - did it, rebooted, and it works with new interface names.  Sorry for the spam - should have tried it before I asked for help :(

---

