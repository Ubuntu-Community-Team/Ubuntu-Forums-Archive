---
title: "Wireless problems Realtek 8176"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by QuimNuss on 2011-04-04
Hi everyone!

The wireless didn't work out of the box with ubuntu studio (the ubuntu liveCD doesn't recognize it either). So here I am...

I don't have wired access at the moment, but I will later on for command outputs. Basically I have a Realtek network controlled Device 8176 (rev 01)

How do I know the model to know what to do from [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI)

I'd hope there's an alternative way to do it without manually download, build and install the driver, which I believe will have to be done every time the kernel is updated?

iwconfig shows no wireless extensions for lo and eth0, and there's no eth1 anywere.

I managed to get the wired ethernet working by ticking the option and installing the network manager, which does not come with the ubuntu studio.

Thanks! btw, worry if I'm repeating somebody else's questions, I found it difficult to be certain that I was having the same kind of problem as other similar threads.

Thank you!

---

### Post by fedetxf on 2011-04-04
I have a Toshiba netbook with that controller. It works out of the box with Ubuntu 11.04 beta (I booted from a USB stick created with the ISO image).

If you don't want to install it now, you can add this ppa

[https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

And install the driver (rtl8192ce).
In my case the driver works with occational freezes. You may have better luck. It is worth trying if you don't want to run 11.04 beta until it is released.

---

### Post by QuimNuss on 2011-04-04
Ok, so I tried the hard way and worked like charm.

Downloading the driver as pointed out by KingLear: [http://ubuntuforums.org/showthread.php?t=1608908](http://ubuntuforums.org/showthread.php?t=1608908)

building and installing worked for me. It's important to notice that you have to install it being root (not with sudo before each command but with sudo su), otherwise I got a source file missing.

hope this helps.

---

