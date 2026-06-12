---
title: "Heeelp, the dreaded hotel WiFi"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by CelestialMechanics on 2013-04-29
Hi
There seem to be many variations of this problem, but no of the previous posts I've found anywhere is helping me.
I'm in a best western with an HP laptop running 13.04, the wifi system tells me I'm connected to the hotel network but firefox (and Opera and Chrome portables) won't open any pages, so I can't log in to use there system.
The laptop seems to be picking up an ip address, and is telling me the gateway and the connection speed, but if I try and ping any address other than it's own (even the router) I get somethign to the effect "destination net prohibited". *I*'ve seen some posts where people have added googles DNS server in, but this makes no difference.
Can anyone help?
I'm a reasonable user (I'm here after all) and am fine with terminal input, but I don't really speak network.
Please forum, save me from this terrible, undermaintained hotel MS laptop, covered in stupid buttons and full of overdue updates!
Best
Robin

---

### Post by AlanR8 on 2013-04-29
Bummer ain't it!

This may be too simplistic but we need to start somewhere. I'm in an Ibis Hotel as we type and get the same if I try to log on to their hotel WiFi that's supplied by Orange. The connection, top right of the screen, will be active but the Web is not accessible. Also happens in Wetherspoons, (Cloud) my office secure WiFi, oh and the Holiday Inn just next door where I log on regularly because its free! (BT Openzone).

What the web browser is looking for is the network's homepage where you logon and in all probability have to exercise your credit card. What I do is open Chrome, allow it to error message me then press the Home button. That takes me to the correct "portal" page rather than my usual home page, google.co.uk.

Hope this helps a bit.

---

### Post by CelestialMechanics on 2013-04-30
Hi Alan
Thanks for your reply, but I'm afraid I've tried chrome and opera (by downloading them onto my phone and sliding them across the usb), but to no avail at all.
There seems to be something fundementally up, I'm beginning to suspect it's all down to the router, but I'm at a loss as to quite how this can be.  Maybe Ubuntu is seeing the config and refusing to have anything to do with such a dreadful set-up!

for background iwconfig does say:
Rx invalid nwid:0  rx invalid crypt:0 RX invalid frag:0
TX excessive retries:0 Invalid Misc:221 Missed beacon:

None of which sounds good!
Best
Robin

---

