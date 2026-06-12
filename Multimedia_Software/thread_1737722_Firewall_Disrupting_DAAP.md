---
title: "Firewall Disrupting DAAP?"
date: 2011-04-23
forum: Multimedia Software
---

### Post by lookup on 2011-04-23
Hi all,

I set up Ubuntu 10.4 on an old Dell (now referred to as UbuntuDell) and loaded it with music.  Practically out of the box, Rhythmbox's DAAP-powered library sharing worked swimmingly over a local area network when UbuntuDell was hardwired (no wireless PCI card) into the router and the client computers were running iTunes.  Perfect.

I've taken UbuntuDell to a cafe and plugged it into his router - I changed nothing else.  Now, the library is hidden - UbuntuDell's library doesn't show up in Shared Libraries in iTunes or Rhythmbox clients.  (Oddly, I can still connect to UbuntuDell with remote desktop.)  (Yes, I have the music licensed.)

All I can guess is that the router's firewall is blocking DAAP, but I don't know how to figure this out.  I've fiddled with Ubuntu's network settings and all, and can't find any reason it shouldn't work.  I should also say I'm not very Linux-literate (Linurate?) - so please be gentle.

So how do I figure out if this is indeed the problem, and then how do I work around this?  The whole point of this endeavor is to make it as automatic as possible for client computers - they log into the cafe's WiFi, and there's UbuntuDell's library right in their iTunes shared libraries.  For various reasons, I'd REALLY like to avoid disrupting the cafe's WiFi service in doing this; I saw something about "telling the router to forward to port 3689" but I don't know how to do this, if this is the right fix to pursue, and I'm not comfortable fiddling with the router itself without guidance.

After lots of searching, I'm still stumped, so thanks SO much for any advice.

---

### Post by lookup on 2011-04-23
Forgot to mention - Rhythmbox is also the boxed version with Ubuntu 10.4 - version 0.12.8

Also should be mentioned that Rhythmbox on UbuntuDell doesn't find any shared libraries on the cafe's WiFi network, either (even while shared libraries are definitely present), whereas in initial test at my place, it did.  Supports the firewall theory?

---

### Post by lookup on 2011-04-24
A more pointed question:  Is mt-daapd the same system that Rhythmbox (or other DAAP programs) sets up when you enable DAAP sharing?

More specifically to this case, is it worth configuring mt-daapd on a computer that is having trouble sharing over the network via Rhythmbox?  Is there any hope that mt-daapd will circumnavigate a router's firewall where Rhythmbox didn't, or is it easier to configure mt-daapd to do so?  (I'm still not 100% that's the issue here but it's still my best guess...)

Thanks very much

---

