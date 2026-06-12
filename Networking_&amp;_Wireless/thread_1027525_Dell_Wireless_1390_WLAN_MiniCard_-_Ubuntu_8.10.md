---
title: "Dell Wireless 1390 WLAN MiniCard - Ubuntu 8.10"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by vonsperb on 2009-01-01
Greetings!

I'm a great fan of Ubuntu since the first version (being used to Debian before that and Slackware before Debian) but unfortunately I have bought a DELL Vostro 1000, which is a crappy laptop. It has a Broadcom 1390 wireless adapter, which doesn't work right even with Windows and I can't get any version of Ubuntu since the first version to work with it properly.

With every new version of Ubuntu I go through the hassle of doing all the manual steps of installing Ubuntu from scratch, setting the bcm module, reinstalling everything again and trying it with the ndiswrapper. I sometimes get it to actually work, but with very limited range. If I get a few meters away from the access point, the connection dies. Other Ubuntu users who have the same adapter have reported the same situation.

Going straight to the point, it sux. I dream about installing Ubuntu from scratch and everything 'just works'. I mean, working wireless that would keep connected far away from the access point, just like it does with Windows.

I'm not sure if I can replace my wireless adapter for something better or if my complaint would get the attention of some nice Ubuntu developers who could make it work on the next release.

Sorry for the complaint and thanks for your attention!

---

### Post by vonsperb on 2009-01-01
Update: I have just switched the 1390 WLAN for a "Broadcom Corporation BCM4312 802.11b/g" (according to lspci) and guess what... Ubuntu 8.10 installed from scratch with everything working.

That solves my problem, but it doesn't make it for the other Vostro 1000 users who still have the default 1390 adapter.

---

### Post by ieee488 on 2009-01-01
LOL.

You didn't tell us what chipset is in the Dell 1390.
That is what MATTERS.

For what its worth, Broadcom isn't entirely Linux friendly. Intel is the way to go.

---

### Post by vonsperb on 2009-01-01
Sorry, I forgot that. Let's see what lspci tell us about Broadcom 1390:

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Is that what we need? Let me know if you want me to have a look at the device itself.

---

### Post by kevdog on 2009-01-01
The 4311 chipset is capable of operating with the b43 driver, the new STA driver (wl), or ndiswrapper.  4311 has two known revisions (1 and 2).  By checking with lshw -C network, this will show you the driver you are using.  My bet is that you are using the new STA driver, however your output will reveal all!

---

### Post by vonsperb on 2009-01-01
Sorry, I forgot that. Let's see what lspci tell us about Broadcom 1390:

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Is that what we need? Let me know if you want me to have a look at the device itself.

---

### Post by kevdog on 2009-01-01
Is there a question related to the device -- we've established its a bcm 4311 rev 01 chipset.

---

### Post by vonsperb on 2009-01-01
Well, yes. Question is: How could somebody get everything working after installing Ubuntu 8.10 on a standard DELL Vostro 1000?

---

