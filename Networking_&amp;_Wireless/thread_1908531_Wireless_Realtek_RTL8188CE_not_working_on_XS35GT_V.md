---
title: "Wireless Realtek RTL8188CE not working on XS35GT V2"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by cblanquer on 2012-01-13
Hello,

I am trying to get wireless working on a Shuttle XS35GT V2 with Ubuntu 11.10.

XS35GT had an issue to activate the wireless hardware that was fixed installing a BIOS higher version that 1.08 (so 1.09 or now 1.0B). I have myself such a box working silently (no fan) under Ubuntu 11.10.

X35GT V2 has a different BIOS which came with v.103. This BIOS has a parameter to allow always on wireless - which is my setting.
There are no other upgrades at Shuttle's download site.

After installing Ubuntu 11.10 I found out that no wireless interface was detected.
I figured out that the Realtek drivers are not part of the kernel installed (v 3.0.0.14) so I followed another thread (cannot find it anymore but thank you):

[LIST=1]
[*]downloaded last drivers from Realtek ([download]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") )
[*]unpacked the tar file
[*]sudo su , make , make install and then reboot, without errors
[/LIST]

After rebooting, no change apparently in the system: the device does not appear, I checked it unsuccessfully with "dmesg | net" and "dmesg | rtl".

So I suspect that actually the BIOS is still "hiding" the device from the system, and I posted a question to Shuttle.

=> Does anybody face the same issue or solved it on this hardware?

Regards.

---

### Post by cblanquer on 2012-01-15
Solved today and a bit puzzled.
I installed "hardinfo 0.5.1" to understand what happens with the Realtek hardware, which actually did not appear in the PCI list!

Suspecting a technical issue from Shuttle, I decided before reporting it to check my older XS35GT (V1) where the Realtek device was present (a different version of the device, as expected).

I then did on the new XS35GT v2 the opposite that was suggested: I went to BIOS at reboot and DISABLED THE ALWAYS ON parameter in BIOS.
After saving and restarting Ubuntu, the good suprise was that my Realtek PCI device was there, I just plugged off the wired, my WiFi network was discovered and working like a charm for the last 2 hours at least!

So I either misunderstood what other adviced to do on BIOS OR the BIOS is working the opposite at it seems to....
I would rather think the second is right, as the BIOS per default is supposed not to support ALWAYS ON (disabled) but this is the way I got it working.

Now even connected to my WiFi printer via hplip. \\:D/
No matter, the good thing is to know that now this tiny box works from any place at home. :popcorn:

---

