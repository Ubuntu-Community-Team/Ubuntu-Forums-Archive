---
title: "Random WiFi Drop outs in Ubuntu"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by GlennLChugg on 2011-10-09
If your wireless network keep dropping out while your in Uubntu (Working fine for Other OS's or PC/Devices)...

I have found a solution:

By using Network Manager in Ubuntu to set the MTU to 1500 (Instead of Auto) and by setting IP v6 to Ignore (Disabled), I have found my connection to be very stable again. Before I would get random drop outs (Once every 10 minutes usually), especially while my network was under high load.

Hope you can share this tip and help someone save many hours hunting for a solution (Like I had to).

Step 1:
[IMG]http://img42.imageshack.us/img42/3441/30492591.png[/IMG]

Step 2:
[IMG]http://img253.imageshack.us/img253/2880/60540183.png[/IMG]

Step 3:
[IMG]http://img267.imageshack.us/img267/6228/66339401.png[/IMG]

Step 4:
[IMG]http://img192.imageshack.us/img192/3764/96083116.png[/IMG]

---

### Post by GlennLChugg on 2011-10-11
To elaborate on the quality, I've had 3 Drop outs in the last 2 days, these were cause by running torrents whilst a lan user was streaming a movie off my PC (via Plex). I am using the N network and it's sufficient to say that 3 dropouts in the mentioned situation is a lot more tolerable than 6+ dropouts an hour.

Of cause the most stable connection will be wired, unless you get one of the certified WiFi adapters.

Netgear WNDA3100 v1 is not one of them.

---

### Post by dinutu on 2012-05-31
Thanks, hope it helps.

---

