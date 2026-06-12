---
title: "Realtek 8188cus can't connect to network"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by IAmWhatWasDavidBowman on 2011-12-08
Hello everyone!

I'm hoping someone can help me to sort a problem I'm having with a usb wifi adapter (Realtek 8188cus chipset). I looked around on the forums for an answer and tried several things to no avail. 

I've been using this adapter in various devices and computers, and it works fine. My old motherboard recently ate it, so I replaced it and upgraded to Ocelot.

In 8.10, 10.04, and I think some other versions, this adapter worked fine after I installed the drivers using the Realtek-provided script.

On my new motherboard (Asus F1A75-V Pro paired with AMD A8-3850), I can get the driver install script to run, appear to install and initialize the adapter, see wifi networks, but not connect to one. It never moves past asking me for a network password (and I'm absolutely certain I've given it the right one).

The output from the end of the install script shows:

```
##################################################
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.0.0-12-generic
##################################################
The Setup Script is completed !
##################################################
```

The "Device or resource busy" has me curious. I get the same message if I "modprobe 8192cu". Does anyone think this is the cause of the problem?

Thank you in advance for any help you can provide. Please let me know if there is any additional information that I can post that will help solve this.

- Dave

[Update] I found this site: [http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)
and I'm going to try that when I'm back in front of my machine. That's my exact card. I don't know how I didn't find that page first.

[Update 2] No luck. And I'm still getting that message about the device or resource being busy. The terminal copypasta you see above was from a more updated version of the driver than the linked guide was using, and I did not need to edit any of the header files under the "driver" folder. Even when I do use the older version of the file and follow the guide's instructions, I cannot connect to a network.

I am using the 64 bit version of Ocelot and that guide is for the 32 bit version. I wonder if that's the problem.

---

### Post by rinring on 2011-12-14
Exactly the same happens to me.
I have placed a question here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190)

---

### Post by IAmWhatWasDavidBowman on 2011-12-14
My temporary solution to this was to install Lucid, however I'd much rather be running one of the more recent releases for various reasons - though I love how stable Lucid has been for me across three different computers. It was a great release!

I had to replace a couple dying hard drives with a large 3TB drive, and the default setup in Lucid doesn't handle the drive's 4Kb sectors properly if you need to re-partition (at least before any updates. I haven't tried since I ran update manager).

Other people reported success with the instructions I found, but I simply *could not* get them to work for me. I'll post back if I have any success, as I'm not done fighting this yet. :-k

---

