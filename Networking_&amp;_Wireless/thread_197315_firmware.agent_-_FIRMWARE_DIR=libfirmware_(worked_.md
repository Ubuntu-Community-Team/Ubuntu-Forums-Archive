---
title: "firmware.agent - FIRMWARE_DIR=/lib/firmware (worked for Intel 2200 wireless card)"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by dan4444 on 2006-06-15
Ok, I have been pulling my hair out looking for a solution on this for the last 2 and a half days. The solution I have found makes me both very happy and angry at the same time. 

I had removed previous versions (by using "sudo make uninstall" and by removing all stray related files) and intstalled the new ieee80211 (version 1.1.14 - [http://ieee80211.sourceforge.net/#downloads](http://ieee80211.sourceforge.net/#downloads)) and ipw2200 (version 1.1.3 - [http://ipw2200.sourceforge.net/index.php#downloads](http://ipw2200.sourceforge.net/index.php#downloads)) drivers. And I placed the appropriate ipw2200 firmware files (version 3.0 - [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)) in the directory that firmware.agent specified (/usr/lib/hotplug/firmware/). 

Despite these efforts to carefully follow the above steps I had found at a handful of different sources (and trying a host of other possible solutions I located), I was getting the following lines in my /var/log/kern.log ("dmesg | grep ipw" gave me more or less identical results):

Jun 15 11:23:46 localhost kernel: [4294771.465000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.3
Jun 15 11:23:46 localhost kernel: [4294771.465000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jun 15 11:23:46 localhost kernel: [4294771.468000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 20 (level, low) -> IRQ 50
Jun 15 11:23:46 localhost kernel: [4294771.469000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Jun 15 11:23:46 localhost kernel: [4294771.484000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
Jun 15 11:23:46 localhost kernel: [4294771.484000] ipw2200: Unable to load firmware: -2
Jun 15 11:23:46 localhost kernel: [4294771.485000] ipw2200: failed to register network device
Jun 15 11:23:46 localhost kernel: [4294771.486000] ACPI: PCI interrupt for device 0000:06:03.0 disabled
Jun 15 11:23:46 localhost kernel: [4294771.486000] ipw2200: probe of 0000:06:03.0 failed with error -5

All previous posts I had read always said the firmware directory specified in firmware.agent would most likely be /lib/firmware or /usr/lib/hotplug/firmware, and mine was the latter, so I had no reason to believe I should change this or worry about it, especially as the path was supposedly taken straight from firmware.agent.

That can't load firmware error was killing me, until I re-read a post I had seen at [http://www.mail-archive.com/linux-il@cs.huji.ac.il/msg44122.html](http://www.mail-archive.com/linux-il@cs.huji.ac.il/msg44122.html) by a Rami Rosen, where he spoke only of the firmware.agent directory being /lib/firmware. On a whim I tried changing firmware.agent - FIRMWARE_DIR to /lib/firmware, copying over the firmware files to that dir, and rebooting.

When my system was back up, bamb, wireless was back in every way! 

Why my system was requiring my firmware directory to be /lib/firmware (or at least, not /usr/lib/hotplug/firmware) is beyond me, but you may wish to try this if you are having similar problems.

---

### Post by dan4444 on 2006-06-15
BTW: I am running Ubuntu 2.6.16, Dapper Drake install. I had no problem with my wireless until I upgraded my kernal from 2.6.15 to 2.6.16

---

### Post by inacoma on 2006-06-18
[QUOTE=dan4444]BTW: I am running Ubuntu 2.6.16, Dapper Drake install. I had no problem with my wireless until I upgraded my kernal from 2.6.15 to 2.6.16[/QUOTE]

Dude, this totally solved my problem.  I just upgraded to dapper yesterday and did the "typical" ipw2200 rigamarole and no dice.  Thanks for your post...the /lib/firmware directory was KEY!!!

oh, btw...My machine did not have a firmware.agent file...guess it's gone the way with all other things depricated....i.e. apt-get hotplug shows that it has bee replaced by:

udev module-init-tools

thanks again!

Kumar

---

### Post by Zeratul7 on 2006-07-20
I am having the same problem. But how did You solve it, when You had udev module-init-tools instead of firmware.agent?

---

### Post by ckippiii on 2008-02-10
Very interesting post.  The problem with the firmware tripped me up as well.  I just made a soft link from the original kernel /lib/firmware/$KernelName to the new kernel name.  Brought the modem online with a reboot.

The question is what did I miss in building a kernel ? :)

---

