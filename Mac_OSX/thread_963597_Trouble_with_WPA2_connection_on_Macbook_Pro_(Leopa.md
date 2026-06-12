---
title: "Trouble with WPA2 connection on Macbook Pro (Leopard)"
date: 2008-10-30
forum: Mac OSX
---

### Post by aysiu on 2008-10-30
This isn't a new problem.

My wife used to have a G4 Powerbook with Tiger and it appeared to connect to WPA or WPA2 but the connection would drop continually. So we switched to the less secure WEP.

When she sold her Powerbook and got a Macbook Pro in its place (with Leopard), we tried WPA and WPA2 again. Same problem. So we switched the less secure WEP.

This whole time, on two separate computers (a Dell Inspiron 500m, and an Eee PC 701), Ubuntu has had no problem with WPA or WPA2 using either Network Manager or WICD. So I'm pretty sure it's not the router's problem.

Nevertheless, in effort to make our wireless network more secure, I tried installing a firmware upgrade on our router (it's a D-Link DI-624 revision C, in case that matters) and switching to WPA2 again.

Once again, no problem on the Ubuntu side with WICD on my Eee.

Initially, connecting to the WPA2 from my wife's MBP seemed fine. On resume from suspend, though, we get a message about how none of the preferred networks are found, and it gives us a list of available networks (which include the preferred network, actually). If we click to connect to the preferred network, it tells us *Connection Failed* twice. The third time, the connection succeeds and appears to last again until the laptop is put to sleep again, and the cycle repeats at resume.

So clearly WPA2 *can* work. It just doesn't want to work the first two times. Any ideas, Mac OS X users?

---

### Post by KiwiNZ on 2008-10-30
I am using wpa-tkip preshared key and have no issues in Leopard.
I am using a Belkin Router/modem.

I remember the days I used a D-Link , what a nightmare , it would drop out at least hourly or 1/2 hourly. I finally took it outside and introduced it to the pavement

---

### Post by aysiu on 2008-10-30
> **KiwiNZ said:**
> I am using wpa-tkip preshared key and have no issues in Leopard.
I am using a Belkin Router/modem.

I remember the days I used a D-Link , what a nightmare , it would drop out at least hourly or 1/2 hourly. I finally took it outside and introduced it to the pavement
I don't think it's the router, though, since it works just fine with Ubuntu. I never get these drops or flaky connections with WICD or Network Manager.

Do you mind sharing the exact model number of your Belkin router, though, in case we do ever trade up our D-Link for something else?

---

### Post by aysiu on 2008-10-31
Well, I haven't done extensive testing on it, but adjusting the router's wireless settings so that Super G is turned off and the channel is automatic instead of fixed at channel 6 seems for now to have fixed the problem. We'll see if it lasts. If it does, I'll confirm that here in case any other people are experiencing the same problem.

---

### Post by aysiu on 2008-11-01
Nope still patchy. Sometimes it works, sometimes it doesn't. Sometimes the connection will just randomly drop. Other times it'll take an extra 30 seconds to connect after resume from suspend.

---

### Post by aysiu on 2008-11-02
Well, she finally got sick and tired of her connection dropping. She'd rather have the less-secure WEP and have thing work. So we're back to WEP...

---

### Post by Eiríkr on 2008-11-08
FWIW, we've had the same problems with an old iBook and now a MacBook Pro, both now running Tiger -- connections secured with WPA fail when Mac OSX resumes from sleeping, leaving us stuck using obsolete WEP instead.  I strongly suspect it's some sort of bug in Mac's Airport drivers.  I'm researching now to see what I can find over on the Mac forums and elsewhere, and will report back with what I learn.  

Cheers,

-- Eiríkr

---

### Post by aysiu on 2008-11-08
I've found many people with this problem on Mac forums, but unfortunately no working solutions are offered, only proposed solutions ("Try this... maybe it'll fix the problem").

---

### Post by Eiríkr on 2008-11-08
Phooey -- that's all I'm finding too.  Some folks have zero trouble, others find only pain and suffering -- which begins to sound like maybe hardware bugs, where a batch or three of Airport cards had problems that Apple simply won't acknowledge (cynically speaking, why would they, when it would only entail a PR hit and extra expense replacing any bum cards).  I'll poke around some more, and post again if I have any successes.  :-\

Cheers,

Eiríkr

---

### Post by aysiu on 2008-11-08
Thanks. If I find anything, I'll post back here, too. Don't think my wife is up to having her laptop undergo further experimentation, though.

---

### Post by cprofitt on 2008-11-09
aysiu:

Where I work we had similar problems and we actually confirmed it was an issue with Apple sofftware/drivers by loading Windows via Bootcamp and Ubuntu on the equipment. The only time there was an issue was when it was running OS X.

In the end we believe that the problem was with the use of short pre-amble which we had to use based on our environment. In simple terms Apple OS X does not allow for you to change the pre-amble setting on your wirless card. If you can change the pre-amble on your router you might want to try that.

I see you said your wife does not want to have more experimentation, but perhaps loading Ubuntu via a live CD will determine if it is hardware or poor Apple drivers.

---

### Post by Frak on 2008-11-09
I had this problem (some time ago, I think you remember). I bought a broadcom based wireless card and inserted it into my powermac (it has an internal Airport Extreme PCMCIA slot on the internals, exactly like the iBook, though it also works under PCI and PCI-X). I could connect then to WPA2 without it dropping my connection every odd minute.

---

### Post by aysiu on 2008-11-09
> **PrivateVoid said:**
> 
I see you said your wife does not want to have more experimentation, but perhaps loading Ubuntu via a live CD will determine if it is hardware or poor Apple drivers. That sounds like a good idea. But how do I get a Macbook Pro's wireless working in Ubuntu? Is there some kind of proprietary driver I need to install?

---

### Post by cyberdork33 on 2008-11-10
> **aysiu said:**
> That sounds like a good idea. But how do I get a Macbook Pro's wireless working in Ubuntu? Is there some kind of proprietary driver I need to install?
If you can determine which card is in it or what MacBook Pro version it is, then we can help you out. The Intrepid LiveCD has the new wl driver in it which supports all but the newest Broadcom cards which were the most difficult to get working. If it has a Broadcom card, then you can unload b43 and ssb, and load wl. Then wireless should be operational. If you have the atheros cards, they are almost all supported by the ath9k driver.

My WPA2 is working fine with my MacBookPro4,1. I did have a lot of issues with my old iBook though. It seems that certain router settings would cause a failure (mostly the 802.11b/g/n compatbility options). I finally got something set right now where it works...

---

### Post by toci47 on 2009-01-24
Hi All,

I have been having similar issues with a range of devices - including iphone and some windows notebooks.  

Finally - I have found some information about the problem - it appears that there is a bug in Mac, Iphone and Windows NB's with Intel 4965ABGN chipsets.

The answer to the problems is not to allow mixed WPA + WPA2 on the router if you can.  On my netgear WNDR3300 I have set it to be WPA2 and it works perfectly - no more dropouts on any device.

---

