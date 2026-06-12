---
title: "remote logging &amp; cellular modem issues"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by justcarroll on 2009-07-31
I have several Acer Aspire One laptops that are acting as data loggers.  I installed Ubuntu 8.10 on all of them.  The hope was to use them to log the data and then relay it back to a local server.  We wrote some software that does that is it works wonderfully when connected to the internet.

The cellular modems, when they are connected, work great.  The problem occurs when the lease on the IP address is up.  From my experience a new one isn't assigned or it is assigned and the computer won't recognize it.  When this happens the modem can be unplugged from the USB socket then reinserted and generally everything is fine, however this is unexeceptable for a remote unmanned facility.

This was an unexpected problem and I came up with a crappy work around.  I just pinged sites on a regular basis and if a reply wasn't received the machine rebooted.  This was quick and dirty.

I tried stopping and restarting networking.  This didn't work, I believe the modem need to have the power cycled.  I tried to cycle the power from internally by it won't work on these computers.  I even cut into the usb cable and switched the power to the modem with an external relay.  This works except that I can't get the network manager auto connect back up.

Any help or advice is appreciated. I have a lot more information if it is needed.

---

