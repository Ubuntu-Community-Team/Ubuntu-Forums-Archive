---
title: "I think I killed my wireless card using macchanger"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by kindhead on 2009-01-26
I used macchanger to change the mac of my wireless card. The change was succesfull and I continued to use Ubuntu with my wireless card working.

However...after rebooting back into XP, my card appears to be dead now.  It no longer shows up under Device Manager in windows. I tried booting back up Ubuntu to see if it still worked under linux, but Ubuntu doesn't seem to see it anymore either.

Did I just kill my wireless card by using macchanger?

Please tell me no!!!

My computer is a Compaq Presario V6101US, with a built in Broadcom (bcm43xx) wireless card. 

Running Windows XP, and Ubuntu

---

### Post by kakotako on 2009-02-06
I doubt you can do any permanent damage like that. Does the card work in Ubuntu? Maybe reinstalling the XP driver will help.

---

### Post by russo.mic on 2009-02-06
I would recommend reinstalling the driver on both XP and ubuntu, to see if that would help.  I'm not sure, but it wouldn't suprise me if it was such that the mac address allowed for driver communication.  

Does XP see it as an alerted device?  i.e. one that it doesn't have drivers for?  Maybe under "unknown hardware"?

Try lspci under ubuntu.  that should let you know if linux sees it, even without a driver.

What method of driver for the broadcom were you using?  NDISWrapper?  BCM drivers?

Russo

---

### Post by russo.mic on 2009-02-06
Oh, and why would one want to change there MAC address?  You can just cloak it...

Just wondering.

---

### Post by michaeless on 2009-02-07
> **kindhead said:**
> My computer is a Compaq Presario V6101US, with a built in Broadcom (bcm43xx) wireless card. 


I have a Compaq V6305NR and the wireless card just stopped working one day. It would come on maybe once every 5 times I restarted my laptop. I talked to HP support about it and the laptop had a recall on it for the wireless card. The motherboard slot for the wireless card was faulty. My laptop was out of warranty but they still did the repair work for free. You should see if your laptop also had the faulty motherboard installed in it.

---

