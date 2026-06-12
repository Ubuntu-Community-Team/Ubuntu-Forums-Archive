---
title: "Broadcom BCM 4318 poor wireless range"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by redb on 2009-10-11
Hello,   I am having problems with my wirless range, I am sitting right next to my router and can only  get about 30%. It is a broadcom wirless card  BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)  I have another notebook in the house that has no problems at all with hooking up, so I know it's not my router.  I have the Broadcom B43 wireless drivers installed.  I have the 2.6.27-14-generic kernel under Intrepid 8.10 system updated.  

Incedentally I have a  RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
 that I purchased a while ago that I would be glad to use if it turns out that my broadcom is fried.  I heard that linux will not support n but the card should still work.  I have not been able to make this one work at all but it does show up when I put lspci into the terminal.  

I have been looking around trying to find an answer to this issue for a couple of weeks now with out any solutions.  
Any help would be greatly appreciated.

Thanks

---

### Post by kevdog on 2009-10-11
Give this open source driver a try:
[http://www.ing.unibs.it/openfwwf/](http://www.ing.unibs.it/openfwwf/)

---

### Post by NoBugs! on 2009-10-25
I also notice slightly lower wifi range with Ubuntu 9.04, broadcom BCM4328, using the proprietary broadcom STA driver.

---

### Post by redb on 2009-10-25
> **NoBugs! said:**
> I also notice slightly lower wifi range with Ubuntu 9.04, broadcom BCM4328, using the proprietary broadcom STA driver.

Strange.  I used to be able to see all the networks within a two block range now the best I can do is 40% standing next to my wireless router and cant see any other networks, god forbid someone closes the closet door (where I keep my router), then it disconnects!  I have been searching for weeks on this issue.  I gave up but now am stonewalled trying to run a Ralink pci card.  :confused:

---

