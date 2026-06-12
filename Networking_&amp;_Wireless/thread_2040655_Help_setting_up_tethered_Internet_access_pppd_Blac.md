---
title: "Help setting up tethered Internet access pppd BlackBerry"
date: 2012-08-11
forum: Networking &amp; Wireless
---

### Post by BruceG on 2012-08-11
I'm trying to set up tethered Internet access on my Ubuntu Precise netbook with a BlackBerry Bold 9780. I had tethering working with an older BlackBerry on the same netbook, but I upgraded and have been fighting with it ever since.

I have the chat script working and all, but there is some confusion between the other end of the link and pppd.

This is the log from the pppd session: [http://paste.ubuntu.com/1141108/](http://paste.ubuntu.com/1141108/)

I am able to use this device with Windows. I captured a PPP trace with it as well: [http://paste.ubuntu.com/1141125/](http://paste.ubuntu.com/1141125/) From what I can see, it goes through a similar series of IPCP ConfReq/ConfNak madness, but after the last IPCP ConfNak, it uses the local given in the Nak instead of discarding it.

The IP given changes every time, and hard-coding one into the pppd config file doesn't work neither.

Has anybody else seen this before?

---

### Post by BruceG on 2012-08-13
After reading the sources of pppd, I found the solution. I had to set ipcp-max-failure to a much larger number than the default of 100. I had tried 1000, but I couldn't see the difference. However, so far 10,000 seems to work adequately reliably.

---

### Post by haseebjaved on 2013-03-17
Can some one please tell me the complete process to do it?
I have blackberry bold 9780 and Ubuntu 10.04 LTS. Please guide me which packages should I install and how to do it all.
Or kindly give me any link where I can get the help because I couldn't fine one.
Thanks in advance

---

