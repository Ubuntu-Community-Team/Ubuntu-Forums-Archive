---
title: "Wireless Card Woes"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by tianhaupt on 2009-11-11
Help - 

Need help getting my wireless card/connection to work.  Upgraded from dual boot windows/ubuntu to just unbuntu 9.10.  Existing Wireless card I was using before no longer works at all (linksys WMP54gs, bcm4318 broadcom) although I installed ndiswrapper and windows drivers.  Installed ndiswapper thru synpathic manager and tried another card, Belkin, which shows as RT2500, RALink.  Installed drivers for this card.  Says I have connection but with 0%.  Set up my ssid, mac filter, and WPA passphrase just won't connect.  Says connection is active.   Any ideas? To many hours wasted already.  Thanks, Newbie in distress

---

### Post by nobster on 2009-11-11
bump... me too facing similar problem

---

### Post by raygj on 2009-11-11
see if this post helps using your **original** default wireless driver(kernel module) 
[http://ubuntuforums.org/showpost.php?p=8295253&postcount=6]("http://ubuntuforums.org/showpost.php?p=8295253&postcount=6")

---

### Post by tianhaupt on 2009-11-13
Raygi,

Thanks for your help although I did get it working.  The IW command wouldn't run (no command found).  After considerable frustration I wiped out 9.10 and went back to 8.04.  It recognized the card immediately without having to use ndiswrapper and windows drivers although I did use the Belkin card instead of the linksys.  No matter neither card would work in 9.10.  I'm up and running.  It's my son's computer so I may try again after a few 9.10 updates have occurred to upgrade.  Thanks again, Marty

---

