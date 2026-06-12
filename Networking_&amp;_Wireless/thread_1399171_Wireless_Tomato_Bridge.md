---
title: "Wireless Tomato Bridge"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by GregTheGerg on 2010-02-05
Hi, I was wondering if anybody had any experience using Ubuntu Server 9.10 x64 and a tomato router to act as a wireless bridge to connect to another router.

The reason I ask is because I do have the router set on WDS mode on the tomato firmware. I think I have it configured to the best of my ability, but when the interface is up, the signal doesn't get pushed out (no received packets) and it gives something at the bottom of an ifconfig eth0 "Interrupt:28".

Does this mean anything to anyone?

(If you need more info, please ask.)

---

### Post by GregTheGerg on 2010-02-05
Oh, by the way the only reason I'm doing this is because I figured if I took the work of the wireless connection off the server. Therefore, making the router do all the wireless work, I could just wire my server into the router.

So, it is a necessary thing for my situation.

---

### Post by GregTheGerg on 2010-02-05
I'm not exactly for sure what I should set the second router on (the one that's acting as a repeater/bridge).

I would think that I should set it either as a "Wireless Ethernet Bridge" or "Wireless Distribution System", but neither one seems to be an exact fit. I would like my router to not only take my wired connection to my server and push it to my other router, but if I can, I would like to have it act as a repeater.

If you think it's possible with tomato, shoot a message.

---

### Post by tgalati4 on 2010-02-05
I don't think it is possible.  You can either set up your router as a bridge which simply repeats the signal--helpful if you need two or more antennas to cover a large property.  A simple Access Point (AP) is just a single (i.e. stand-alone) antenna that routes signals from a modem (DSL or cable or T-1) and runs them through a firewall and sends them out on a wireless G band typically.

I've never seen a wireless router do both functions simultaneously.

---

### Post by GregTheGerg on 2010-02-05
Well, regardless if it can do both functions. Does anyone have a Tenda W268R router which they've tried something similar to this with a Linksys WRT54GL with the Tomato Firmware?

I know it's kind of specific, but it really doesn't matter if you've done it on those exact router's as long as one of them was a Tomato router. I just need to know how to you configured it to act as a repeater.

---

