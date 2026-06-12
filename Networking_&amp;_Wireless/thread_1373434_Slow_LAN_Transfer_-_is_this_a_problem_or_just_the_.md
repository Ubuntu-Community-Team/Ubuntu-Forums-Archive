---
title: "Slow LAN Transfer - is this a problem or just the norm?"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by socistep on 2010-01-05
Hi All

I am experiencing what I perceive to be slow transfer speeds on my home LAN and am posting to see whether others believe this to be a problem. I use NFS as the main transfer but tried others for testing.

My network in the main includes a media server running fedora linux and 2 laptops running Ubuntu, the server connects to a netgear router via ethernet homeplugs whilst the laptops connect wirelessly. In addition there are other devices which connect mainly wireless but also via ethernet, these are squeezebox streaming music players x3, iPhones x2, & a Wii.

I often want to transfer data between a laptop and the server and have been getting frustrated with the speeds, have connected with smb, nfs & ssh and to/from the server are getting approx 500kb/s transfer rate.

From this I tried a few test combinations tonight to see what speeds I was getting, first of all I connected laptop to laptop (removed the server and this had 2 wireless hops) and was getting slightly better but still <1MB/s. Second was to move the server downstairs, remove the homeplugs & direct wire into router, then transfer from laptop over wireless - this improved to 1-2mb/s. The best transfer speed I got was laptop and server connnected both with ethernet and no homeplugs, this was coming back at 7-10MB/s. Finally I moved the server back upstairs routed through homeplugs and tried the laptop wired to router and this pulled back 1-1.5MB/S.

So main observations are that problem lies in 3 potential areas

1) Ethernet Homeplugs - Speed is reduced when server is wired to router via homeplugs against direct connection

2) Router - Wireless is significantly reducing transfer rate against wired connection which is to be expected, however in addition router might need upgrading to improve transfer rate/deal with multiple devices.

3) Ubuntu/Linux - I have read on this forum that other people have experienced slower transfer rates with Ubuntu v Windows, this is an unknown for me as currently don't have a windows laptop to test, however am due to buy a new laptop soon and can test this part as will be dual booting.

Main questions for the forum are 

- Are these transfer speeds common or slower then average ?
- What advice can be given to improve transfer speeds in any of the 3 problems areas above ? suggested kit to buy

Any help will be really appreciated

Thanks
Ian

---

### Post by adam814 on 2010-01-05
All things considered it doesn't sound that terrible.  I don't know that I've seen many LAN transfers faster than 1MB/s in practice with my own equipment.

It does sound like you have a LOT of devices connected directly or indirectly to the router.  That may be unavoidable, but it can't help with the speed.

My advice:
1) Check for any old network hardware than may be pulling other things down to "lowest common denominator" (i.e. an old 10Mbps switch or NIC).
2) Set a low RTS threshold in the NICs (iwconfig wlan0 rts 250) and at the router on wireless connections.  With as many active nodes as you have it sounds like you need it.
3) I assume these homeplugs are ethernet-over-powerline equipment.  I've never used them and while they sound like a cool concept I doubt they'll help if it's speed you're looking for.

---

