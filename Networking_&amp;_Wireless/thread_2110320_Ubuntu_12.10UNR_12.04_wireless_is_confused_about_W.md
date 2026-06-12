---
title: "Ubuntu 12.10/UNR 12.04 wireless is confused about WPA2"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by rae_bot on 2013-01-29
I have a recently-upgraded UNR (12.04) running on my netbook, and I just built a computer with Ubuntu 12.10. UNR had no wireless problems until I upgraded, and now the only way I can connect is by manually choosing the connection every time I turn on my netbook - because trying to connect to the network it detects, it won't let me hit "connect" unless I add another three characters to the password! Checking "automatically connect" on the new version of the connection didn't work to make it connect automatically, and editing the wireless security on the default connection didn't work, either.

So now I have this desktop running 12.10 and I'm running into basically the same issue as the netbook with 12.04, except I can't even manually connect to a new connection to the same network with the right security selected. It's WPA2 (which I verified with iwlist, and since iwlist knows it's WPA2, I really have no idea what's going on), but it will not let me hit "connect" without a thirteen-character password, which is very much wrong. When I try to make another connection with the right security selected, it tries for a while to connect and then asks me for the password in a pop-up box, and then tries for a while to connect and then asks me for the password in a pop-up box, et cetera, ad nauseam.

What in the world am I supposed to do? I have to assume the issue is in the OS and not the hardware, since the hardware is totally different on both boxes and the trouble only appeared on my netbook when I upgraded the OS.

---

