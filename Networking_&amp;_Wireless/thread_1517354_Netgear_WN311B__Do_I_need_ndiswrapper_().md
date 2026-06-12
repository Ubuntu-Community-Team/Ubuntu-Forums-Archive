---
title: "Netgear WN311B:  Do I need ndiswrapper (?)"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by mparker1113 on 2010-06-24
I have installed Ubuntu Server 10.x and want to use it as a  router/gateway to internet for a small intranet. I have two nic cards on  the machine, one of them is detected when i do lspci or ifconfig, the  other is not detected (Netgear WN311B Wireless card.)

I am not sure what my next step should be. Should i use ndiswrapper,  install the windows drivers for the card, and then expect it to be  recognized when i do ifconfig ? I don't see anything labeled "chipset"  when i do lspci and am not sure where to go with that either.

If anybody can help me get some distance with this, I'd be grateful.

mp

---

### Post by Fist_Rothbone on 2010-06-25
I reccomend using the ndiswrapper . I spent hours trying to get it goin and that's the only working solution i could find. It is a bit tedious, but it pays off- havent had a single problem with it.

At first, I too did not see my apater listed in lspci, but after i removed and reseated the card it did show up. 

if you bring up a terminal and type [COLOR=Red][COLOR=Green]lspci -nn[/COLOR] [COLOR=Black]your WN311B should be listed as [COLOR=Red]"[/COLOR][COLOR=Red]Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)[/COLOR]"[/COLOR][/COLOR] or something close to that ('BCM43XG' is what you're looking for).  If/when you so see it listed, try following the steps i posted here:
[COLOR=Blue]_[http://ubuntuforums.org/showthread.php?t=1480323&highlight=wn311b](http://ubuntuforums.org/showthread.php?t=1480323&highlight=wn311b)_[/COLOR]

Good luck!

---

### Post by mparker1113 on 2010-06-25
Thank you very much for replying. I will be working on this later, (hopefully tonight) and will post back results. :guitar::guitar:

---

