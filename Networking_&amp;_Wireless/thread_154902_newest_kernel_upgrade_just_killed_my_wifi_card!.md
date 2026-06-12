---
title: "newest kernel upgrade just killed my wifi card!"
date: 2006-04-04
forum: Networking &amp; Wireless
---

### Post by nemik on 2006-04-04
Hello,

I'm on breezy and just now did a regular upgrade with update manager and it got a new kernel and kernel headers. but now my eth0 wifi card is gone. i have a dell 700m and a ipw2200 card built in. everything worked PERFECTLY before and now this happened.

I have no idea what broke it or how to fix it. botting into the recover option also did nothing, there is no eth0 when i do iwconfig.

what should I do?

---

### Post by BoyOfDestiny on 2006-04-04
[QUOTE=nemik]Hello,

I'm on breezy and just now did a regular upgrade with update manager and it got a new kernel and kernel headers. but now my eth0 wifi card is gone. i have a dell 700m and a ipw2200 card built in. everything worked PERFECTLY before and now this happened.

I have no idea what broke it or how to fix it. botting into the recover option also did nothing, there is no eth0 when i do iwconfig.

what should I do?[/QUOTE]

Hmm, is it gone gone, like when you go to network settings there is no wireless card? Maybe it was using restricted modules... make sure you have them installed for your kernel (go to synaptic, look for linux-restricted). 

Otherwise try activating/deactivating the card in the network settings.

Last suggestion, give dapper a try ;) It's been great for me.

---

### Post by nemik on 2006-04-04
nope, just gone. not in network settings. doing dmesg | grep ipw it said it had problems with the ieee drivers and such. 2.6-9 works fine though...

as for dapper...i dunno....isn't it still too early? did it break automatix and stuff you had?

---

### Post by nemik on 2006-04-04
ok, i fixed it.

i got the newer 1.1.12 ipw2200 from here [http://ipw2200.sourceforge.net/#downloads](http://ipw2200.sourceforge.net/#downloads) and did `sudo make install`

then got newer 1.1.13 from here [http://prdownloads.sourceforge.net/ieee80211](http://prdownloads.sourceforge.net/ieee80211) and also did `sudo make install`

i already had the latest firmware so left that alone. then after a restart, it was all good! :)

---

