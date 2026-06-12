---
title: "Power on after outage"
date: 2010-08-27
forum: Mythbuntu
---

### Post by itlarson on 2010-08-27
Is there a way to get a computer to reboot automatically after a power outage if there isn't a setting for this in the bios?  This is for the Zotac ion frontend/backend i built for my parents.  It has settings for network and usb power on, but nothing for power on at AC power restore.  Would it work to just short the pins that go to the power switch, or would this damage the motherboard?

---

### Post by pricetech on 2010-08-27
You said Wake On LAN was supported.  Here's a workaround if there's another computer in the house;  Set the other computer up to send a magic packet to the computer in question whenever it boots and set it to power on  after a power failure.

Clunky I know, but it should work.

And no you don't want to short the pins.

---

### Post by larsolav on 2010-08-27
I think if you buy an APC UPS it should be able to send a signal via USB to the motherboard to fire up the PC when the power is back on. It is always good to use an Uninterruptible power supply anyway, as it prevents spikes in electricity from damaging your computer (even surge protectors don't really protect against it always).
I think there is a way to make it all compatible with Ubuntu so that the computer shuts down on its own (without damaging the database) if the battery is about to run out.

Do some searches for APC and Ubuntu. I bought an APC UPS at Sam's Club, but never took the time to set up the controlled power down and USB wakeup.... If you buy one too, then maybe we can figure out how to set it up. :-)

Here is a Ubuntu link: [https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

---

### Post by cycling-rod on 2010-08-27
Have you thought of adding an uninterruptible Power Supply (UPS)?

---

