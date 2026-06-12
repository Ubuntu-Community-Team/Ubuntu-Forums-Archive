---
title: "D-Link DIR-615 wireless connection issues"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by tschorsf on 2012-10-19
Hi all, 

I am experiencing some wireless connection issues with my dir-615 router and my thinkpad x230 (ubuntu 12.04 LTS). Let me get this straight: 

First of all, on my iMac everything works as one would expect. So DHCP seems to work. On my thinkpad I can connect to the wifi and also get an IP, but cannot connect to the internet. I even cannot ping the iMac or the router itself. The network settings seem to be correct though. In particular, in Wireshark (recorded on my iMac) I see the pings of my thinkpad arriving. The iMac answers them with a reply, but the replies never get to the thinkpad. I confirmed that with Wireshark.  

With other wifi networks I actually never experienced something similar with my thinkpad. So, I suspect that the router is the problem but I have no idea what it could be. The firmware is updated to the newest version. I tried with and without WPA. MAC address filtering is deactivated of course. Any other hints or ideas? 

It would be great if anyone could help me in solving this issue.

Thanks in advance. 

Cheers, Flo.

---

### Post by ahallubuntu on 2012-10-19
I have two identical DIR-615 routers.  One is my main access point at home, and it uses the factory firmware from D-Link.  It gives me great connections and download speeds on the local network.

However, I deployed the spare somewhere once and people could not connect to it with their phones at all - it would lock up the entire network.  I had to use another (different model) router which worked fine.

Note that the "DIR-615" is really a marketing name for several completely different routers with different hardware.  Same box, different guts.  The two DIR-615s I have are hardware rev C1.

Rev C1. that I have is a couple of years old, and there has been no firmware update on mine for a couple of years.  You can try the DD-WRT firmware on some revs of the DIR-615.  I put it on one of mine - I assume this would have resolved the phone connection issues I had seen. It is a bit tricky to install DD-WRT on my version, and I did not keep it on my main router because the factory firmware version still gives me a higher data transfer rate.  But I don't have smart phone issues with it; if I did again, I'd switch to DD-WRT.

---

### Post by Derek Karpinski on 2012-10-19
+1 for dd-wrt.  I had nothing but problems with my dir-615, dropping wireless, no wired connection, if I connected my android, the whole network would stop, etc.

I bought another router, but kept the dir-615, flashed it with dd-wrt, and use it for G-band only.  No problems since.

---

### Post by ahallubuntu on 2012-10-19
I have three or four different N routers in use or as spares, and I have put DD-WRT (or Tomato) on all of them...but on my DIR-615 Rev C1 I still get the best sustained data transfer rate with the factory firmware vs any other router with DD-WRT (including same router with DD-WRT).  Factory firmware from Linksys (on their router) or Asus isn't faster either.  Not sure why this one works best.  I spent quite a bit of time tweaking settings trying to make DD-WRT faster but could not. Maybe my laptop wireless card likes the D-Link factory firmware better for some reason.  It's also quite reliable - never drop connections.  Do need to reset it every month or so but that's it.

As I said, I did have issues with phones on the DIR-615 but I don't connect mine to it so no issues for me.

Isn't your DIR-615 an N router like mine?  Why G only?

---

### Post by Derek Karpinski on 2012-10-19
Well, I became so frustrated with the dir-615, and wanted a router with enough RAM to run the full blown version of dd-wrt so I could run a VPN server on it, I bought an ASUS RT-N16.........which is a GREAT router BTW, especially for the price!

So, I had two routers.

But some of my devices like a squeezebox and an older smart phone only connect with G-band.  If you don't have a true dual band router, your N-band connection will slow to G-speeds if you connect with a G-device.

So, I run the ASUS with N-only, and the dlink with G-only.  With dd-wrt, connecting the two routers together on the same subnet is fairly simple.

I did notice that on the dlink before I flashed it with dd-wrt, the root of most of my problems was when I connected a G device and the router was in N-mode.  It required a reset daily.

---

### Post by tschorsf on 2012-10-20
> **ahallubuntu said:**
> Note that the "DIR-615" is really a marketing name for several completely different routers with different hardware.  Same box, different guts.  The two DIR-615s I have are hardware rev C1.

My dir-615 says hardware-version Hx. 

Any Ideas to solve this issue without using dd-wrt? I know it offers a lot of additional features, but installation is tricky and probably I am to lazy to do that. There must be a way that it also works with the factory's firmware. I am not trying to do any rocket science here; just would like to connect my device wirelessly.

---

### Post by ahallubuntu on 2012-10-20
You probably don't have a good DD-WRT option for that hardware rev anyway - there is a DD-WRT image for it but it's pretty new and seems somewhat experimental.

Can you try a wired connection temporarily to the DIR-615 from your Thinkpad?  That way at least you can figure out whether the wireless connection is the problem or not.

---

### Post by tschorsf on 2012-10-20
> **ahallubuntu said:**
> Can you try a wired connection temporarily to the DIR-615 from your Thinkpad?  That way at least you can figure out whether the wireless connection is the problem or not.

Yes, it works perfectly fine -- plug-n-play.

---

