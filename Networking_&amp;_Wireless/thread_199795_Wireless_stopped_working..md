---
title: "Wireless stopped working."
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by Jan Jansen on 2006-06-19
I tried the live cd and found to my delight that my wireless worked. After a while I decided to drop MS and installed Ubuntu 6.06. I did a couple of reboots and the wireless still worked. I did a shutdown, started the laptop again and the wireless no longer works. The bright wireless light is off and switching the wireless switch on/off does nothing. Here is an excerpt from dmesg:

```

[17179591.736000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179591.736000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179591.736000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!

[17179592.180000] ipw2200: Radio Frequency Kill Switch is On:
[17179592.180000] Kill switch must be turned off for wireless networking to work.

```

Any clues?

---

### Post by mjm115 on 2006-06-19
**[17179592.180000] ipw2200: Radio Frequency Kill Switch is On:**

That line sticks out.  Do you remember making any changes to your laptop before it stopped working?  Do you remember getting any type of updates?  That kill switch must be disabled.  Are you dual-booting at all?  I do know that if you turn it off in one OS, it will stay off regardless of the OS, because its a hardware setting.  You can also try [http://www.linuxquestions.org/questions/showthread.php?s=&threadid=364134](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=364134)

Someone had the same exact issue you're having.

---

### Post by Jan Jansen on 2006-06-19
I installed the updates the update-notifier offered me without looking at them. I don't have dual-boot. Others have reported having to boot Windows to enable the wireless, but I no longer have Windows. I tried looking in the BIOS, but didn't find anything that looked related. I'm a bit disappointed, because I really like Ubuntu.

---

### Post by ngeren on 2006-06-19
I feel your pain, mine did the same after last nights upgrades .. so much for staying on the bleeding edge of releases, from now on, I won't trust the recommended package updates!

---

### Post by ngeren on 2006-06-19
Reverting back to the 2.6.15-23 kernel got my wireless working again. Obviously the recently (updater-installed) 2.6.15-25 kernel has some issues. Q/A might have been high?

---

### Post by Mr. Picklesworth on 2006-06-20
Have you tried installing ndiswrapper from source using the (finally available!) linux-headers for 2.6.15-25?
Worked for me.
The trick is actually getting the package, but should be easy if you have a medium to transfer it.

Look at [this page](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-headers&searchon=names&subword=1&version=dapper&release=all) for the appropriate packages (remember, 2.6.15-25). Both [this one](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-25) and the one appropriately named for the platform you are on (386, 686, amd64). Dependencies shouldn't be a problem.

Then you'll need [ndiswrapper from here](http://ndiswrapper.sourceforge.net/). To install from source, [see their Wiki.](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Hope that helps :D

I share your pain, btw... shouldn't that update have included a recompiled ndiswrapper? (And could such things be done automatically?)

---

### Post by stupidkid on 2006-06-20
If your wireless works using a native Linux driver, then stick to it. After all, ndiswrapper is a "wrapper" or emulator for Windows drivers. It is slower (obviously) than native Linux drivers, kind of like Wine.

---

### Post by Jan Jansen on 2006-06-23
This page gave me the solution: [http://folk.uio.no/krisvh/linux/cl56.html](http://folk.uio.no/krisvh/linux/cl56.html)

I needed to install the Acer Hotkey driver.

---

