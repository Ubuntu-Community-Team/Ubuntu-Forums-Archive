---
title: "TransmissionBT + TOR"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by sphm on 2009-08-04
Hi all,

I'm trying to configure transmission to connect to the tracker trough TOR, but when I set it up. Upload/Download goes to 0,0kb immediately. By the way, I set the proxy configs to 127.0.0.1:9050

Ubuntu Jaunty
Transmission 1.73 (PPA)
Tor 0.2.1.19 (from tor repos)
Privoxy 3.0.9 (from Jaunty repos)

---

### Post by Zak Frost on 2010-09-26
Well, I realize this was quite a long time ago, but I just used the 127.0.0.1:9050 settings with polipo and tor, and it seems to be working fine. [Here]("http://www.torproject.org/docs/tor-doc-unix.html.en#polipo") It says you can also use Privoxy, but they seem to prefer polipo for whatever reason. Perhaps using the Privoxy settings they have there will help.

Of course you've probably fixed this or given up by now, but for people who were googling for answers like I was, I will attempt to help.

---

