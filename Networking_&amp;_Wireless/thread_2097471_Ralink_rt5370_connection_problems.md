---
title: "Ralink rt5370 connection problems"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by iLikeRuby on 2012-12-23
Hi,

I'm using 32bit Mint 14 (but I have the exact same problem in 32bit Ubuntu 12.10).

I'm having trouble with my rt5370 Ralink wireless N usb dongle.

I've read a lot on different things people do to make it work, and I'm not sure if mine is working properly.  I don't think it is.

Here's what I did:

after downloading the latest driver 2.5.0.3 and extracting it I did:

changed this: HAS_WPA_SUPPLICANT=y
and: HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

sudo su
make clean
make
make install
modprobe rt5370
exit

And it *works* I guess.  see what happens is, the connection speed in the network manager wireless area is rather variable.  When idling, it is remains at 135Mb/s; however, if I try to do stuff, it drops to say ~40Mb/s or ~20Mb/s or less...

Also when I do speed tests on Speedtest.net, the results vary heaps, sometimes I get 10Mb/s sometimes 2Mb/s.

I have no idea why...

Advice would be appreciated.

I am happy to provide any information necessary to get this resolved.

Thank you.

---

### Post by dwb814 on 2012-12-23
> **iLikeRuby said:**
> Hi,

I'm using 32bit Mint 14 (but I have the exact same problem in 32bit Ubuntu 12.10).

I'm having trouble with my rt5370 Ralink wireless N usb dongle.

I've read a lot on different things people do to make it work, and I'm not sure if mine is working properly.  I don't think it is.

Here's what I did:

after downloading the latest driver 2.5.0.3 and extracting it I did:

changed this: HAS_WPA_SUPPLICANT=y
and: HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

sudo su
make clean
make
make install
modprobe rt5370
exit

And it *works* I guess.  see what happens is, the connection speed in the network manager wireless area is rather variable.  When idling, it is remains at 135Mb/s; however, if I try to do stuff, it drops to say ~40Mb/s or ~20Mb/s or less...

Also when I do speed tests on Speedtest.net, the results vary heaps, sometimes I get 10Mb/s sometimes 2Mb/s.

I have no idea why...

Advice would be appreciated.

I am happy to provide any information necessary to get this resolved.

Thank you.

Hi,
I have numerous issues with the "Ralink" chip sets, thanks to the good folks here and  [http://askubuntu.com/ ]("http://askubuntu.com/")the issues get sorted out.

First of all the direct downloads from "Ralink" are questionable, sometimes they work, other time not. Also it seems that no matter what your chip set name is it doesn't work very well with the imbedded driver in the kernel. 

So, here are the solutions, first of all you have to use the "rt2800usb" driver to get things to work. The one downloaded from "Ralink" errors out so there is another solution:
[http://ubuntuforums.org/showthread.php?t=2081775](http://ubuntuforums.org/showthread.php?t=2081775) starting at post #3 if you follow those instructions, you will get a steady connection.

I haven't tried it but there is another post with your Ralink rt5370 chip set at [http://askubuntu.com/questions/134170/how-do-i-get-a-tp-link-tn-wn727n-usb-wireless-stick-working,  ]("http://askubuntu.com/questions/134170/how-do-i-get-a-tp-link-tn-wn727n-usb-wireless-stick-working")it may work, then again it may not.

I can tell you with [flash63]("http://ubuntuforums.org/member.php?u=815324")'s advice my connection because rock solid.

Hope this helps you out.

---

### Post by iLikeRuby on 2012-12-24
Thanks for the reply.  I tried what you said and it pretty much works perfectly except for one thing.  Sometimes, when using the wireless, the connection strength halved (from like ~95% to ~40%) and the download speed decreases proportionally.  I feel as though it is switching between wireless G and wireless N though I am not sure.  Perhaps there be a way to force wireless N to always be used.

Actually the wireless even dropped out once.

Nonethless it certainly is much better, but I'd still like to know why it's fully working as it should.  Any ideas would be appreciated.

Thanks.

P.S.  I think you're right about Ralink's downloads being questionable!  I think that may have been the issue.

---

### Post by dwb814 on 2012-12-24
> **iLikeRuby said:**
> Thanks for the reply.  I tried what you said and it pretty much works perfectly except for one thing.  Sometimes, when using the wireless, the connection strength halved (from like ~95% to ~40%) and the download speed decreases proportionally.  I feel as though it is switching between wireless G and wireless N though I am not sure.  Perhaps there be a way to force wireless N to always be used.

Well, it can be many different variables involved, distance from the router, radio wave interference, microwaves, bad weather can interfere with the wireless signal, etc...

> 
Actually the wireless even dropped out once.

Nonethless it certainly is much better, but I'd still like to know why it's fully working as it should.  Any ideas would be appreciated.

Thanks.

P.S.  I think you're right about Ralink's downloads being questionable!  I think that may have been the issue.I tell you my experience, you can take it for what it's worth.  Ralink chipsets are JUNK! I've had nothing but problems with them. If I use a Realtek or  Atheros chipset device it's smooth sailing.

I had the same issue you did with signal drop and fluctuation with Ralink chipset devices. I thought it was because my router is upstairs and my computer is downstairs on the other side of the house. So, after going through 2 Ralink devices I went and invested in a long range network adapter with antenna's. [http://www.amazon.com/Etekcity-Wireless-Network-Adapter-Antenna/dp/B006JWMOOI](http://www.amazon.com/Etekcity-Wireless-Network-Adapter-Antenna/dp/B006JWMOOI)
This is also a Ralink chipset device, everything we great for about 5 weeks, then the signal fluctuation and drop offs started again. So out of frustration, and to confirm it was this adapter, I took a little mini usb wifi dongle with a Realtek chipset,  plugged it in, loaded the software, rebooted and BOOM, 100% lock!

I bought it from here for $6.00: [http://www.ebay.com/itm/271033874479?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649](http://www.ebay.com/itm/271033874479?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649) it has the Realtek rtl8192CU chipset with the installer .sh script. Piece of cake for getting it running.

If you need a longer range devices, I can say that these two haven't failed me yet. The TP-LINK TL-WN722N and the Netgear WNA1100 both run the Atheros chipset, you don't even need a driver installed because it's built into the 12.04 kernel. 

Hope that helps you out.

---

