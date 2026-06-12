---
title: "Can't connect to wireless with new HP Mini 210"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by The Deacon on 2010-01-19
Hello. I just picked up a brand new HP Mini 210, and I'm not able to turn on the wireless capability when running the Ubuntu Notebook Remix. I haven't fully installed Ubuntu yet, and am just running it from a thumb drive now.
 
Anyway, there is a button on the keyboard (f12) that is supposed to turn on wireless internet capability. It works when I boot up the default OS (Windows 7), but not from Ubuntu Netbook. Any help is appreciated, and if you need any more information then let me know.

---

### Post by The Deacon on 2010-01-19
.

---

### Post by The Deacon on 2010-01-19
OK, I tried some fixes and they didn't work, so it looks like I'm going to need a lot of help on this one.

---

### Post by The Deacon on 2010-01-20
Bump.

---

### Post by JCasper on 2010-01-20
What have you done so far? Provide the steps you've tried and all of the information on this subject you have so far so people can better help.

Go into the device manager and see what wireless card you have. Then maybe you can find the linux wireless drivers for that card.

I also have a HP mini 210 HD with the wireless N card, but I haven't had a chance to research the issue.

On HP.com here are the wireless atheros cards listed for the mini 210:

Atheros AR9285 802.11b/g/n WiFi Adapter 
Atheros AR5009 802.11a/g/n WiFi Adapter 
Atheros AR5006 802.11a/b/g WiFi Adapter 
Atheros AR5007 802.11b/g WiFi Adapter

Now we can just look for the ubuntu wireless drivers for these cards.

I have the N compatible, and [http://madwifi-project.org/wiki/Compatibility/Atheros](http://madwifi-project.org/wiki/Compatibility/Atheros) at the very bottom shows it's compatible with madwifi. So we should be able to install that correct?

---

### Post by hyperandy on 2010-01-30
I was thinking of getting one of these with the Broadcom card but was seeing if there was support or it yet....I don't know why WiFi has to be a pain...but if it's atheros 5007 I posted a help on an older laptop I had [http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/") Don't know if that will help. Also I have had off and on luck using the 32bit drivers and using ndiswrapper to load them...what have you tried and what is your wireless chipset

---

