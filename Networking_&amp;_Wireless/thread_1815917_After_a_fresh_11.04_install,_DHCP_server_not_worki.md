---
title: "After a fresh 11.04 install, DHCP server not working..."
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by omelette on 2011-08-01
After a fresh install of Ubuntu 11.04 (from 10.04) and spending several hours trying to figure out why the ad-hoc connection between my two computers (Fedora14 <-> Ubuntu 11.04) no longer worked - it had worked fine for almost 2 years with 10.04 - I've finally concluded it was a DHCP problem. This realisation (which was slow in coming!) dawned on me when I reversed my setup and configured the Fedora box as the DHCP server and everything was suddenly working perfectly! A quick internet search threw up an installation file called "isc-dhcp-server" which other Ubuntu 11.04 - related forums are also complaining about.  My problem is that this file, although available in the repository, is not even installed!!!

It seems unlikely that the developers forgot to include DHCP support, so I hope someone can point me in the right direction.

---

### Post by omelette on 2011-08-01
I have just confirmed to myself at least, that this is the lamest Ubuntu release I have yet experienced - this being ISO number 4 from the Ubuntu stable!  After exhausting every other possibility I could think of, including reinstalling it all again, I have just reinstalled and am typing this in on the old Ubuntu 10.04 LTS, and found unsurprisingly, that the Wireless works perfectly from the get-go - just like the last few other releases did prior to the release of this turkey!

There is definitely a major Wireless bug in Ubuntu 11.04 which looks like it's in the DHCP server code, seeing as the DHCP client seems ok as I commented on in the above post.  That coupled with the many other DHCP comments regarding 11.04 that I've come across would tend to confirm this...

It's bad enough that something this big (imo) ended up in a major release, it another thing that even though it's been out for a few months already, there still isn't a 'fix' available in the repositories - at least the 340meg of upgrades I've just installed didn't fix it!  Not happy. :(

---

