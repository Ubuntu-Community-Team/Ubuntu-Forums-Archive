---
title: "Karmic unable to obtain ip address"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by spsmith78 on 2009-12-24
I am using Ubuntu 9.10 and I get this weird message when I first try to connect to my wireless internet for the first time. It tries to connect then WICD comes up with a message that states unable to obtain IP address. I have to unplug the router, wait 30 seconds, plug it back in and everything is fine.  Once I do that the connection is strong and very fast. Is this just something I am going to have to live with or what could be the issue? I have another laptop that uses Windows 7 that never has an issue connecting. Anyone have any thoughts?

---

### Post by Iowan on 2009-12-24
Just theorizing (sounds better than "taking wild guess")...
Wonder if it isn't registering as "disconnected" - or if it's trying to get the same address (which is registered as "in use")? If the Windows box can disconnect and reconnect, I wonder why Ubuntu can't.
Do you have a way to connect to the router to check lease tables, etc., to see what's different between the two?

---

### Post by spsmith78 on 2009-12-24
> **Iowan said:**
> Just theorizing (sounds better than &quot;taking wild guess&quot;)...
Wonder if it isn't registering as &quot;disconnected&quot;? If the Windows box can disconnect and reconnect, I wonder why Ubuntu can't.
Do you have a way to connect to the router to check lease tables, etc., to see what's different between the two?

 I could probably do it but wouldn't have the first clue as to how to do it.  Another weird issue I ran into, if I have the desktop computer running then the wireless connections on the laptops drop every 5 or 10 minutes. As soon as I turn that desktop off everything is fine, almost like the desktop takes bandwidth away from the wireless laptops. I spoke with Linksys about this and they were no help, said if the problem persists I need to buy another router. This is the second Linksys router I have had in 2 years, if I buy another router it will NOT be a Linksys.

---

### Post by adam814 on 2009-12-24
I've also had poor luck with Linksys equipment ever since the Cisco merger.

Wicd tends to be a little less stable than NetworkManager and it seems to depend on the NIC involved.  That having been said I use it on my laptop as I also run fluxbox in addition to GNOME and it works fine with my wireless card (iwlagn driver).

---

