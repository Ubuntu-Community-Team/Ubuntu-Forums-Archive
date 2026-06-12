---
title: "raLink 3090 will not work"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by Janitor-Blue on 2010-07-17
I am running Ubuntu 10.04 (32-bit) on a [MSI A5000]("http://www.msimobile.com/level3_productpage.aspx?cid=9&id=222") which appears to have a RaLink **[COLOR=#ff0000]RT3090[/COLOR]** wireless card. So far everything seems to work except the Wireless card.
 
The problem is that no option for wireless appears in the network manager, it only shows the options for wired connection. This computer does have a button on the front to enable/disable wireless and I have confirmed that is is on, as there is a green indicator light showing this.
 
Can anyone tell me the status of the RaLink **[COLOR=#ff0000]RT3090[/COLOR]** with Ubuntu 10.04? I have looked through various posts here about getting this card working with earlier versions of the OS, where complicated procedures with mixed and apparently intermittent results are described. Do these measures also need to be followed with 10.04?
 
I have attempted several older solutions found in assorted threads here and I am still unable to get the card to even so much as show up in the network manager. The proceedure which seemed the most promising is here [http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/) but this did not help me at all. I will post more information about the card on request.
 
Thank you in advance to anyone who can point me in the right direction towards getting this working.

---

### Post by Zizuph on 2010-08-08
Same laptop running 10.04 64-bit.  Wireless not supported yet.  Please provide estimated time to support this new wireless chip.


Thanks.

---

### Post by Janitor-Blue on 2010-08-08
Actually, did 'sudo modprobe rt3090' and it works!
 
see if this works for you as well

---

