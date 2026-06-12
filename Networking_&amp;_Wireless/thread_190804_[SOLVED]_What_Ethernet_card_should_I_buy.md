---
title: "[SOLVED] What Ethernet card should I buy?"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by RavenOfOdin on 2006-06-06
Hey, I just did some more checking into my network issue (see previous post about Arris drivers) and I may have to buy an Ethernet card anyway. I'm sitting here and wondering which one I should buy, since I have a dual boot XP/Linux setup and I want to buy something from a reputable manufacturer - I had my old Realtek RTL8139 for something on the order of 4 years.

The closest store near me is a CompUSA, and I've been browsing their main website.

My ISP supplies drivers for pretty much all of these cards, and where they don't said cards are listed as being Linux-compatible:

[http://www.compusa.com/products/product_info.asp?product_code=118210&pfp=cat3](http://www.compusa.com/products/product_info.asp?product_code=118210&pfp=cat3)

[http://www.compusa.com/products/product_info.asp?product_code=284641&pfp=SEARCH](http://www.compusa.com/products/product_info.asp?product_code=284641&pfp=SEARCH)

[http://www.compusa.com/products/product_info.asp?product_code=50350433&pfp=SEARCH](http://www.compusa.com/products/product_info.asp?product_code=50350433&pfp=SEARCH)

[http://www.compusa.com/products/product_info.asp?product_code=50170110&pfp=srch1](http://www.compusa.com/products/product_info.asp?product_code=50170110&pfp=srch1)

Any advice would be appreciated.

---

### Post by murph2481 on 2006-06-06
Personal perference says go with the Linksys.  It should be supported.  Do me a favor and just stay as far away as you can from netgear!

---

### Post by RavenOfOdin on 2006-06-06
Okay, I went with the LNE100TX.

I also have a Linksys wireless card in my comp (which hasn't been activated or configured in some time) that does a good job on both OS'.

The compilation instructions on my HSI CD are for Slackware, RedHat 6.1 through 7.1 (kernels 2.2 - 2.4)

With that last in mind, there's a very good chance that its compiled into the kernel already.

So. . .I'll check this out.

---

### Post by Skye on 2006-06-06
I'm pretty sure just about every 10/100 ethernet card under the sun is now supported by the linux kernel- I'd be very surprised if it wasn't.

---

### Post by valnar on 2006-06-07
For many reasons, some unrelated to Linux, you would want an Intel based NIC for broadest compatibility and performance.  Stay away from Realtek or Broadcom.

robert

---

### Post by RavenOfOdin on 2006-06-07
[QUOTE=valnar]Stay away from Realtek[/QUOTE]

I'd like to know just for what reason you say this.
I've never had any problems with them (until now, but that really isn't their fault), and they seem to make decent hardware.

---

### Post by RavenOfOdin on 2006-06-07
(EDIT: If I didn't hate *the Simpsons* so much, the first word out of my mouth right about now would be "D'oh!"

eth1 is my Linksys, since I DISABLED WIRELESS CARD SUPPORT in my recent kernel!

And that, other than persistent and annoying outages since Comcast has their head up their @$$, works fine.

*bangs head against keyboard . . .  hjb ftrghg ytytg*)

---

### Post by dvarsam on 2006-06-09
In the Windows world, I have always been "preferring" the US Robotics team...

Their products have been very good - they get detected in Windows without the need of drivers!!! (no setup or anything!!!)

The problem is that I can _NOT_ confirm that the same case appears in the Linux world...

I want to be straight with you (or when I suggest other people what to choose...):

I have NOT bought/tested any US Robotics product (other than a Router) on the Linux world...

Good Luck whatever NIC you choose!

P.S.> By the way, their Router works great!

---

