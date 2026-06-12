---
title: "Complete cutout of networking using Verizon FIOS, only with Linux"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by Volmarias on 2011-11-26
I'm having significant problems with my Ubuntu partition at the moment. I haven't booted into it for at least 6 months, and decided to boot back into it for a variety of reasons.

Unfortunately, the network was going somewhat slowly. Running an internet speed test shows an average speed of about 5Mbps down, whereas on windows the speed is usually around 40Mbps down. Additionally, I had period where the network would just cut out entirely.

I assumed that the latter part was connected to me looking up a hostname during a google search, so I tried changing the DNS servers to 8.8.8.8 and 8.8.4.4 (Google). That helped get rid of Verizon's DNS Adverts, but didn't solve the underlying problem.

Pulling out wireshark, it turns out that my networking just flat out cuts out at certain points. I started pinging a website (thedailywtf.com), and wireshark shows the DNS resolving (looks about right), and a couple other bits happening as I send the ICMP query and get the response, but after a few seconds it just.... stops. Nothing happens. I see ICMP requests go out but absolutely no other networking, not even background networking such as the router asking for tree info.

I'm pretty stumped on what to do here. This doesn't happen WHATSOEVER while booted into windows. Additionally, I don't remember it happening the last time I used linux (6 odd months ago) with this desktop, and I had FIOS then with the same router.

It's possible that this is an issue with the router, but I don't even know where to begin here.

I've burnt a live CD of 10.04, on the off chance that this was related to 11, but it still occurs even for the 10.04 live CD.

I also found another thread that seems to describe this problem ( [http://ubuntuforums.org/showthread.php?t=1671214&highlight=fios](http://ubuntuforums.org/showthread.php?t=1671214&highlight=fios) ), but it seems to be closed. Changing the DNS servers fixed this for him, although I have no idea why, since his networking was also cutting out when he was just making connections to ips directly.

I'm hosting the wireshark capture at [http://volmari.as/temp/fioswtf.capture]("http://volmari.as/temp/fioswtf.capture"), in case anyone wants to take a look.

If it helps, the router is an actiontec mi424wr, effectively stock.

---

### Post by JesusFreke on 2011-11-26
Have you tried turning it off and on again?

---

### Post by Volmarias on 2011-12-26
For reference to anyone who stumbles over this thread, the same issue occurs when I use my Android device; it appears to be an issue with the ActionTec MI424wr router, not with the desktop.

---

