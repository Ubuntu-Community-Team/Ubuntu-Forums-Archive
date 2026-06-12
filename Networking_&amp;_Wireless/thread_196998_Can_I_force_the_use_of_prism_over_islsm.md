---
title: "Can I force the use of prism over islsm?"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by dermdaly on 2006-06-15
Like many people on this forum, my wireless card stopped working after upgrading to dapper.  I spent some time looking into it, and have not solved it.
Here's what I have found out:
[LIST=1]
[*]The driver being used for the wireless card is islsm
[*]The firmware gets loaded fine (the link light comes on), but I cannot make any activity happen on it (dhclient appears to be working, but I know nothing is going out because the activity light does not come on)
[*]I've tried a number of different firmwares from prism54.org - Both softmac and full mac firmwares - None of these work.
[*]I tried the firmware received with the card; the kernel log shows that it doesn't even attempt to load it because it claims it is not a proper firmware file.
[*]For some reason, the wireless-tools show it up as a 802.11b card (its a 802.11g card)
[/LIST]
Ideally, I'd like to force the kernel to use prism54 as the driver, and then somehow get it to use the firmware supplied with the card (this was how it was working in Breezy AFAIK.
I've worked out how to blacklist islsm, islsm_pci and islsm_driver, but I don't know how to tell the kernel to use prism54 as the driver for a particular eth[n]. - Is this even possible?
I suspect that because hotplug has been replaced by udev, I may have to do something special to link the udev class with the relevant kernel module.

I don't want to use ndiswrapper, as I didn't have to before!
The card is a 3Com 3crwe154g72, version 1 which uses the prism chipset.

TIA
Dermot.

---

### Post by stupidkid on 2006-06-15
I believe you can blacklist modules in /etc/modules.d/blacklist.

I also have the prism chipset and my wireless works perfectly using ndiswrapper. Maybe you can also try ndiswrapper? It does have speed disadvantages considering it's a Windows driver emulator.

---

### Post by Lambert on 2006-06-15
With sudo privlidges open up the text file /etc/pcmcia/config
(I believe this is the correct file, can't verify currently)

Look for your device and you should see a line "bind xxxx"

You can change the xxx to the prism driver so it loads that driver for that device.

This is quick and sort of general. I believe there is a man page for pcmcia or config.

---

### Post by awaldram on 2006-06-15
That is only true for 16bit pc cards not 32bit pc cards as the prism 54 is

The prism54 kernel module is also bust so I wouldn't bother

The ndiswrapper does funtion though.

blacklist both islsm and prism54 and your set

Sorry to be correct Dappers implentation of the prism54 driver is bust along with a lot of other kernel stuff nash nash winge moan

---

