---
title: "HP 6450b wireless driver unable to be installed"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by linux83 on 2011-07-26
Hello Friends,

i have HP 6450b that installed with Ubuntu 10.04, i'm unable to install it's wireless driver.
the cable is working fine and bluetooth.

when i try to activiate the driver i got this error:

Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

this is the last log file lines if i try to install the driver:
-----------------------------------------------------------------------------------
2011-07-26 17:44:08,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa551d6c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:LaserJet P2055dn;')
2011-07-26 17:44:08,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa551d6c> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2011-07-26 17:44:08,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa551d6c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-26 17:44:08,668 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-26 17:44:08,702 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-26 17:44:08,766 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-26 17:44:23,470 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-26 17:44:23,677 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-26 17:44:23,678 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-07-26 17:44:23,749 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-26 17:44:28,238 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-26 17:44:28,271 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-26 17:44:28,332 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
---------------------------------------------------------------------------------------


i check all these solutions but fail to bring WL up:

[http://ubuntuforums.org/showthread.php?t=1371881](http://ubuntuforums.org/showthread.php?t=1371881)
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
[http://ubuntuforums.org/showthread.php?t=1369975](http://ubuntuforums.org/showthread.php?t=1369975)


any help will be appreciated,

---

### Post by linux83 on 2011-07-26
Hello,
i got this command and it's the only command that help me to resolve my issue:

sudo apt-get install linux-headers-$(uname -r)
for the reference, my hardisk was installed on other laptop before i change it to my current laptop.
this command seem to update my NW driver on my new laptop.

thanks.

Linux83

---

### Post by Peter09 on 2011-07-26
Have you tried using the third party drivers application. Are you trying to install this driver from a downloaded file?

---

### Post by linux83 on 2011-07-26
> **Peter09 said:**
> Have you tried using the third party drivers application. Are you trying to install this driver from a downloaded file?


Hello [Peter09]("http://ubuntuforums.org/member.php?u=300963"),

thanks alot for your prompted help, i solve this issue by using this command that update my driver:

sudo apt-get install linux-headers-$(uname -r)

it update the kernel then reboot and it's solved,

thanks again for help.

---

