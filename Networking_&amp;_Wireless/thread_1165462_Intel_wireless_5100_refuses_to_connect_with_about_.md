---
title: "Intel wireless 5100 refuses to connect with about 55% power"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by Wintershade on 2009-05-20
Hi everyone. Just today I've bought a new notebook computer, Acer Aspire 7730G, with an Intel 5100 wireless card.
When I'm close to the router, it connects perfectly. However, if I make a few steps away (the NetworkManager applet still detects over 55% transmit power), I cannot connect anymore. I don't lose my connection if I had one - but if I disconnect, and try reconnecting, it doesn't work.

Since I'm not really experienced in this field, I'd like any pointer anybody could give me. Where should I start? Which log or output should I post that could make it easier for someone to help me?

Many thanks in advance :)
ps. I'm running Ubuntu Jaunty (32-bit ATM), just installed and updated to the latest versions.

---

### Post by pootle42 on 2009-05-22
I have this same problem on an aspire 6930G, I've reverted to a piece of wire for now, while I sort out the sound and graphics issues......

I came to the conclusion its the drivers.  It works if I'm on top of the wireless hub, but goes haywire when I move away.  Periodically it sees it then drops out again.  

I would get bits of web pages, and reprompts for WPA authentication.

Even close to the hub, ping response times to my router would be all over the place - up to 1 second or timing out

Suspect it'll need a new version of the drivers to behave - I'm already using much later versions of both video and audio drivers than those built into Jaunty.

---

