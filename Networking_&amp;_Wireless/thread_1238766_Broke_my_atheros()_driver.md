---
title: "Broke my atheros(?) driver"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by bobtfish on 2009-08-12
I believe my wireless card is an atheros one, but it worked from a fresh install of 9.04. A few weeks ago I was having trouble connecting (turned out to be the router) but at the time I went System->Administration->Hardware Drivers, and there was one there which was labelled as some kind of wireless driver, and was disabled. I enabled it. Since then it has disappeared from the Hardware Drivers box (which now shows nothing) and my wireless has stopped working completely.
Clearly there was some kind of problem or incompatibility with the thing I enabled, but I don't know where to start to get back to the original setup. Reinstalling Ubuntu wouldn't be a complete disaster, but obviously I'd prefer not to have to resort to that.
If I do ifconfig I only get eth0 and lo (and pan0 if I do ifconfig -a). If I do lspci the only networky thing apparent to me is Ethernet controller: Realtek Semiconductor Co. etc, which I presume is for wired connections.
So any suggestions? Have I stopped it recognising the wireless card altogether, or is it just not loading the right driver? And of course, in these cases, what should I do?
Thanks.

---

### Post by bobtfish on 2009-08-13
Please, any suggestions anyone? I don't even know where to start narrowing down the problem, and I'm getting very fed up of Vista.

---

### Post by bobtfish on 2009-08-14
After some searching, I thought ath_pci, ath_hal, and ath5k are the relevant drivers, but only found recommendations for Intrepid. However, I changed a blacklist file and it now works:
I changed /etc/modprobe.d/blacklist-ath_pci.conf from

#Some comments I don't really understand...
blacklist ath5k

to

#blacklist ath5k
blacklist ath_hal
blacklist ath_pci

So it does work now, but I'd still appreciate anyone's thoughts on why it happened, if I've reverted it back to how it was originally or just found a way round, and if this is the best way to do it.
Incidentally, "Alternate Atheros "madwifi" driver" has now reappeared in the Hardware Drivers box.
Thanks.

---

### Post by djchandler on 2009-08-14
Having same problem, bobtfish. Thanks for posting. I'll give this a try.

Wonder why the driver is getting blacklisted. But I had no problem until I tried the madwifi proprietary driver too. Warnings about its use could be stronger.

---

### Post by djchandler on 2009-08-14
My driver was blacklisted too. All is well now. Will check on launchpad for bug. The driver should not be left blacklisted after trying the proprietary Atheros driver and subsequent removal. Sounds like a Jockey bug to me.

---

### Post by djchandler on 2009-09-28
This has been listed as a low-priority bug on launchpad.

> OK, thanks. Jockey should look into this file as a special case, unless
it's a conffile (I have to check).

** Changed in: jockey (Ubuntu)
   Importance: Undecided => Low

** Changed in: jockey (Ubuntu)
       Status: Incomplete => Triaged

-- 
jockey not restoring ath5k driver from blacklist
[https://bugs.launchpad.net/bugs/413781](https://bugs.launchpad.net/bugs/413781)
You received this bug notification because you are a direct subscriber
of the bug.


---

