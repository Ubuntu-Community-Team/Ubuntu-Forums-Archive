---
title: "PCI and USB WiFi intermittant?!"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by yorkwils on 2012-07-02
Thanks in advance to anyone with technical knowledge who can help me...

Acer Aspire 5633LMi laptop which has a built-in PCI WiFi card that I can see no way of disabling in the BIOS. I have Ubuntu 11.04 loaded (I did try to do a fresh install of 12.04LTS but it hangs about half way through loading. I'll try the upgrade route from 11.04 later.)

I need to get better WiFi reception than the internal card can offer but I can't use a repeater. My solution was to try a USB WiFi dongle with Realtek chipset. This has a detachable aerial and I was then going to install a directional aerial on an aerial extension cable.

Both WiFis detect my Belkin G Plus MIMO ED217C router so there are two entries in the network list: One under Intel PRO/Wireless 3945ABG[Golan] and the other under Realtek RTL8191S WLAN Adapter.

Normally I can connect on the PCI WiFi and the Internet works fine. If I try and connect on the Realtek dongle very occasionally it will work ok but normally it will just cycle through connecting and then disconnecting until it gives up, at no point is the Internet usable when it is doing this.

I'm guessing that the two WiFi cards are fighting over channels but that is just an ignorant guess!

If I try lsusb in a terminal, it finds the dongle and reports it as RTL8191S WLAN which seems correct.

If I try nm-tool (I don't know exactly what these commands are I have just collected them whilst browsing) then it reports the drivers and other information about WiFi and says that the driver for the Realtek dongle is R8712u ??? This is different to the RTL8191S I would have expected for the device.

I know earlier drivers are sometimes used on later devices but it would help me to know if this is the correct driver or do I need to load another one? If the driver is ok, what do you think is going on and how might I solve it?

Many thanks

---

