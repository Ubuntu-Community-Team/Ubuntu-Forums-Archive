---
title: "Problem with Xubuntu 8.10, ndiswrapper and pcmcia wireless adapter."
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by jaciminelli on 2009-05-02
I apologize in advance is this issue is redundant.
I am encountering problems while attempting to replace Windows XP on a friends computer with linux. This is the fifth system I have configured and have never run into anything like this. My friend needs her computer back in two days so my issue is somewhat urgent.

The machine is a Dell Inspiron 1200 laptop now running Xubuntu 8.10.
The wirless card is a PCMCIA 802.11b/g card (Trendnet 421-pc)
The PCMCIA slot seems fine, it is a Texas Intruments device, recognized with drivers, using the yenta bridge I beleive.
The card it's self is an Atheroes chipset (11ab:1faa)
The driver was downloaded from the Trendnet website, Windows XP driver 1130 driver.
and installed with ndiswrapper.

What I have done:

Installed Ndiswrapper, downloaded and installed the driver. Disabled the xubuntu default drrivers in the blacklist file, manually copied the Trendnet firmeware binaries to /lib/firmware. forced ndiswrapper to associate the 1130 driver with the 11ab:1faa device. Still nothing.

Nature of the problem, for most of the time ndiswrapper showed the driver installed properly but no present hardware. Now that I have done everything in my power to get the hardware recognized, it is unable to find a network configuration tool.

Please help, I don;t want to hand her back a laptop with Windows XP on it.

I will be happy to post the output ffrom anything you want here.

Thanks in advance.

---

