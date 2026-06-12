---
title: "Can anyone recommend a good USB wireless adapter that you know works with ubuntu?"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by javajames97 on 2011-10-27
Can anyone recommend a good USB wireless adapter that you know works with ubuntu?

I need a more powerfull wireless adapter, with 802.11n capabilities.

---

### Post by Unterseeboot_234 on 2011-10-27
I had good luck with Ocelot, Belkin N300 USB to an AT&T, but let me give you my experiences..

On Ubuntu Lucid64 I was hard-wired. We moved, and the new location prevented a direct-connect ethernet. I had no internet access after our move.

I wanted to try connection to a DSL-modem with built-in router (AT&T). I didn't know wireless at all, researched it, determined I needed to download SourceForge source code and build ndiswrapper. I did that. Installed the resulting .deb. Worked like it should on a single-core AMD64. Would not work on a multi-core AMD64, yet the multi-core the adapter works fine in Win7. It has to be my built version of ndiswrapper. I learned Ubuntu already comes with ndiswrapper.

ndiswrapper is known to make Linux unstable and perhaps I did have a conflict happening with the Ubuntu pre-installed ndiswrapper.

I reformatted my hard drive on the AMD64 single-core, installed Ocelot, the N300 Belkin Adapter was plug-n-play. All I had to do was select the router-network name, type in the serial number on the bottom of the modem.

I will add my Adapter did not work on the REAR panel, but does work on the front panel USB. I look forward to reformatting the multi-core AMD64 to see if I get the same success.

I tell you all this, because the Adapter is not just hardware choice... it is part of a loop. IMHO

As far as good? On my direct-connect wired I was getting 310/kps. With the wifi Belkin I'm getting 322/kps downloads.

---

### Post by haqking on 2011-10-27
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Unterseeboot_234 on 2011-10-28
I just tried LiveCD Ocelot on our AMD64 hexacore, which is Linux kernel 3.0.0-12-generic.

The Belkin N300 USB dongle was plug and play, and the result: I was on the internet. 

With Natty the computer crashed as soon as I plugged in the dongle. So, I'll be busy in the next hour installing a new Ocelot.

---

### Post by kurt18947 on 2011-10-28
I have 2 that have been plug & play since 11.04.  Both would work <11.04 but required tweaks/additional software.

[http://www.trendnet.com/products/proddetail.asp?prod=200_TEW-649UB&cat=169](http://www.trendnet.com/products/proddetail.asp?prod=200_TEW-649UB&cat=169)  Decent choice for portable devices.

[http://www.netgear.com/home/products/wireless-adapters/simplesharing/WNA1100.aspx](http://www.netgear.com/home/products/wireless-adapters/simplesharing/WNA1100.aspx)

Both are N150, not N300 but N150 is plenty fast for my purposes.

I also have one old warhorse.  I keep it around because it has been plug & play since I started messing around with Linux, around 8.10 or 9.04.

[http://www.trendnet.com/products/proddetail.asp?prod=265_TEW-424UB&cat=3](http://www.trendnet.com/products/proddetail.asp?prod=265_TEW-424UB&cat=3)

I would use this one like others use plugging into a router to download initial updates, additional drivers, backports and such before the first two devices were plug & play.  It still works if you're on a G WiFi network.

---

### Post by javajames97 on 2011-10-28
Cheers :D

---

