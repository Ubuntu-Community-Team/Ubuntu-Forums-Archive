---
title: "Synergy Problems"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by tommyss4l on 2011-05-23
I'm having some serious issues using Synergy between my desktop and my netbook. Both are running Ubuntu 11.04.

I installed quicksynergy from the software center and everything started ok. I wanted my desktop to be the server, I opened quick synergy and put in the IP address of my netbook, which I got from connection infromation>IP address, then hit execute and close. Next on the netbook, I opened quick synergy put in my desktop's IP address (acquired from the same location) in the "Server hostname/IP address:" box and my netbook's name in the "Screen name:" box. I hit execute and close.

Now when I move my cursor from the right side of my desktop's screen where it should move over to the netbook, the cursor jumps to the middle of the screen on the desktop and does nothing to the netbook. What have I done wrong here?

---

### Post by dilidon on 2011-07-24
> **tommyss4l said:**
> I'm having some serious issues using Synergy between my desktop and my netbook. Both are running Ubuntu 11.04.


Not sure if you found a solution already, it's been a while. But I was just struggling with the exact same situation, which I solved 10 minutes ago. Try this:
[https://help.ubuntu.com/community/SynergyHowto]("https://help.ubuntu.com/community/SynergyHowto")

It is the clearest of all instructions I was able to find during an hour of trying to make it work. (Also, my limited 30-minute effort 9 months ago failed). And now I got it to work in 2 minutes after a long process of reading manuals, forums and trying out solutions.
Like numerous users you can find on forums, I found quicksynergy not doing the trick at first. I figured out why, eventually - the problem lay in the semantics. The terms "share" and "use" simply mean nothing for the beginning user because, first, all manuals talk about "client" and "host" AND "server" (whereas the latter two mean the same thing in most cases, but it is not clear, **especially** for non-native English speakers). And second, it is by no means clear that one should **only** touch the "use" tab on the client side and the "share" tab on the server side (that little sentence already makes it easier to undertand). If you take the to points into consideration together, it simply does not add up. :) The standard logic of client-side and server-side stuff would make things much easier to understand. I would be happy to help someone sort it out if people agreed with me.
When I started up, I tried to fill out both tabs on both machines. To no avail. Then I read the man pages again and switched to manual configuration, and as that did also not work out, I gave the GUI another go, using the last manual I found. The last being the best. :guitar:

---

