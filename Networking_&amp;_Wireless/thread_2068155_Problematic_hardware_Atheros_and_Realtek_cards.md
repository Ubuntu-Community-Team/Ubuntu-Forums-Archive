---
title: "Problematic hardware: Atheros and Realtek cards"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by Inoki on 2012-10-08
Hi lads,

could the devs have a closer look at support for these cards?

- Realtek RTL8191SEvB Wireless LAN Controller
- Atheros AR8152 v1.1 Fast Ethernet

I'm currently not running Ubuntu or any of its derivates for this very reason, which has been causing me trouble for ages now.

The only version that perfectly supported these cards was Oneiric. All prior versions and versions afterwards didn't.

---

### Post by Bucky Ball on 2012-10-08
Realtek RTL8191SEvB Wireless LAN Controller is working faultlessly for me and has since 10.10. What problems are you having with it exactly? It works pretty much out of the box now ... or should.

As far as I know the other card should work fine, too. Generic.

My advice: Plug in an ethernet cable, do an update (with your wireless dongle plugged in if not internal card), check Additional Drivers. 

Be aware that you might want to email Realtek and Atheros or the devs directly rather than post here. This is a support forum for the community; there is absolutely no guarantee any dev will ever look here or anywhere else on the forums, at least not the ones working on your driver (if there are). Depending on what drivers you are talking about they may not have anything to do with Ubuntu or Linux devs anyhow, but to do with Realtek and Atheros. ;)

---

### Post by Inoki on 2012-10-08
Thanks Bucky for the reply. Well my issue was simple. What seemed odd was, that while using the Live USB everything went flawless, no connection interruptions. Once fully installed, after a brief period of time the wireless connection got completely lost.

That's all I can say. That's why I stopped using Ubuntu after Oneiric wasn't supported anymore. I upgraded to Precise with a fresh re-install and this occured.

---

