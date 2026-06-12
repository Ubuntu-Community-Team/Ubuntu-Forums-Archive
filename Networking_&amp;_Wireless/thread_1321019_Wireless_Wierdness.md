---
title: "Wireless Wierdness"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by rp3 on 2009-11-09
So I upgraded my A305 Laptop to Karmic a week or so ago, all went as well as expected.  Wireless worked, still have 'restricted video' issue, but thats another story.

Well I wanted to setup a static IP for my wireless setup, so I updated the interfaces file and resolv.conf to match my needs.  All seems well for a couple days, then today when I get back from out of town the wireless on my laptop doesn't work?  Hmmm, so plug in CAT5 works fine.  Tinker for a bit, then wonder if it broke, so I put in a 9.04 disk, wireless works great, put in a 9.10 disk wireless works great.  

But in my install when I click on the graphic for network I don't get any choices for networks, etc. All greyed out, I have reset the /etc/network/interfaces to the bare min thinking that would cause it to 'reset' but nope.

I have added back in the wireless setup in network-manager to no avail, copied what the LIVE 9.10 did and still no go.

My question is, how can I reset it so that it looks for networks again, and asks for the key, etc.. I can't seem to get that back, I can live with DHCP if I have to.. :)

I have /etc/init.d/networking restart a couple times after trying multiple things, but I can't seem to get there.

I don't want to remove network-manager (gui) as I do every once in a bit use my laptop at other hotspots, so I need to be able to change networks easily, etc..

Any ideas?  Thoughts?  Things to try?

*** Ok this is just wierd, now it works, I moved the machine back to the front room and rebooted to continue the oddessy and now it is working.  Of course on DHCP, but I can live with that.

no idea what I did to fix it... that is the bummer part.. :(

****
Thanks in advance,

Rp3

---

