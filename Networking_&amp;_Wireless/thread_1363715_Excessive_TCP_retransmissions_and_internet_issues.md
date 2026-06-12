---
title: "Excessive TCP retransmissions and internet issues"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by chorca on 2009-12-24
Been having issues with the internet since my upgrade to Karmic. I'm using an Atheros-based wireless card, however the issues happens on both wifi and to a lesser extent on wired network.

Basically, at random times, I'll be unable to access a site. This won't necessary be all of a site, but it will be the main page normally. I'll type in a location and hit enter, and it will go as far as "Waiting for xxxxx" or "Transferring data from xxxxx", then wait there for long periods of time until a timeout happens or the page eventually loads.

This will happen and stay happening for on average, about five minutes, at which point it will begin loading properly again. It only happens on this laptop, and only since I've installed Karmic. The same sites load normally on other computers on the same router while this one has issues. I decided to use WireShark to pull some info on what's going on while it's waiting. I found (as you can see from the image) that after the initial "HTTP POST" goes out, there are retransmissions all the way out to 21 minutes (if i'm reading correctly, the timestamps are seconds since beginning of capture). Finally the page loads, but other than that, there's no data transfer, just constant retransmissions. Reloading the page or trying to go to the URL again does not change at all, it just keeps retransmitting again and again.

I'm not sure what's going on here, if it's having problems with the wireless driver or something else.

Anyone else having similar problems?

This is on a Dell Latitude D510, Karmic with latest updates, Netgear Atheros based wifi card.

---

### Post by chorca on 2009-12-24
Did another test as it stopped working again. Plugged in Ethernet, and was still unable to contact Google properly. There are no retransmissions, it just sits there and waits for more data to come in. It waited over 6 minutes with no sign of timeouts.

This is what Wireshark saw in the TCP stream containing my search query to Google. At this point there has still been no change in the browser ("Waiting for www.google.com"). It's frustrating at a minimum, because the site will stop working and come back at random. I've upgraded my router's firmware, but because this is a random occurrence it's hard to define a test to make it happen, other than browsing for an hour or so and see if this occurs.

Any help would be much appreciated.


EDIT 1: If it is in a "broken" state (one of the times where a page will not continue to load) resetting my router and having the laptop request a new IP does not resolve the issue. It will still wait for long periods.

---

### Post by focwiz on 2009-12-24
Sounds a lot like what was happening to me...see the following post...
[http://ubuntuforums.org/showthread.php?t=1361797]("http://ubuntuforums.org/showthread.php?t=1361797")

---

### Post by chorca on 2009-12-24
I've now reset my router, cablemodem, and laptop. I'm still getting excessive retransmissions and pages load for over 10 minutes. I've also changed my router's DNS servers to OpenDNS and verified they're operational. I've pulled down new IPs from the ISP and the router, with no change.

I should also note that I even went so far as to reinstall Ubuntu. Right from the start, this problem exists.

I'm not sure where to look from here. I have Wireshark logs of the local machine, but I don't know where else to start looking. I have Tomato on the router, not sure if it's able to get raw packet logs, i could look into that.

---

