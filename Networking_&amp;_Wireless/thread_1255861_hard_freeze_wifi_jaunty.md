---
title: "hard freeze wifi jaunty"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by harrismh777 on 2009-09-02
Greetings,
I have been running jaunty 9.04 with full updates on my desk machine as well as my laptop.  I love it. :KS  Thanks much to the entire ubuntu community on a great product.

I have been having an intermittent issue with network manager and my wifi driver(s) creating a hard system freeze (num lock and caps lock flashing) requiring a forced power off and reboot---and unclean umounts!

I have experienced this hard freeze two different wifi cards and adapters---on pci based internal on the laptop (R30 2656 ThinkPad) and the other a USB WG111 from netgear. While the USB device is connecting the interface (gnome) is locked... this can take 30 seconds to a minute and a half. During that time if the network traffic is really busy or if the cable is bumped, the driver and/or network manager gets grumpy and the system hangs with a hard freeze (desktop as it was) caps lock and num lights often blinking and the keyboard and processor are dead.

If it gets connected (and it often does) it will stay connected and run for hours... 

A search of the ubuntu forums shows that this has been a common problem on previous releases also... what is going on, and, how can I get some stability from the wifi?

I have also read often on the ubuntu forums a recommendation to uninstall network-manager-gnome and install network administration. Why?  Is the issue related to network manager, vs. the wifi driver stability?

thanks much  :)

---

### Post by harrismh777 on 2009-09-10
> **harrismh777 said:**
> 

A search of the ubuntu forums shows that this has been a common problem on previous releases also... what is going on, and, how can I get some stability from the wifi?



I refuse to believe nobody else has seen this on 9.04 !

Does anyone read these postings?


#-o

---

### Post by Alias1407 on 2009-09-10
Are you trying to use any software that uses the wireless card and that needs root privelages...
e.g.
[LIST]
[*]Kismet
[*]Aircrack-ng
[*]Wireshark
[/LIST]

---

### Post by harrismh777 on 2009-09-12
[QUOTE=Alias1407;7925894]Are you trying to use any software that uses the wireless card and that needs root privelages...


no. 

It has been years since I have seen a genuine kernel panic, and I have never had the kernel just *freeze* before...  oh, I've had trouble getting a wifi card to work with a given driver... but never this... hard freeze with the caps light and num light flashing...

Searches show this happening with ubuntu distros in the past... but no resolutions.   Is this a kernel bug, driver bug, gnome bug.. what?  Am I the only one seeing this on 9.04?

thanks

---

