---
title: "Server's network connection seems to go to sleep"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by tyraen on 2009-09-03
Hi folks,

So I've had a machine running in the house for a little while, I think it started out with 8.04 on it but it's up to 9.04 now. All the while it's had an issue I haven't been able to track down. It seems like the network will go down on it, but as soon as I hit the keyboard to login it comes back up (I've even watched the network activity LEDs on the back, and they start blinking when I touch the keyboard). I've had a look in the past but can't really figure out what is causing it. Any ideas?

Thanks.

---

### Post by jonobr on 2009-09-03
I would recommend if you have a second machine that you send a continuous ping to the server and see if the interface becomes unavailable or doesnt respond.

You could also try a continous ping from that machine and see what happens with that also,

It may shed a bit more light...

It would be interesting to see if those pings keep the thing active.

Also is this DHCP or static IP address assignment?

---

### Post by tyraen on 2009-09-03
I set up a cron that is supposed to ping Google once every 5 minutes (now I haven't confirmed that it's actually doing anything, so I'll give that a shot). The IP is static also. Thanks for the suggestions!

---

