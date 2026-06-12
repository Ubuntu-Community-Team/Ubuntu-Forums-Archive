---
title: "Help with WLAN driver installation."
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by houndbytes on 2010-09-16
I recentlty bought a RealTek WLAN adapter. The adapter came with Linux compatible driver cd, ,however I do not know the first thing about installing anything on Linux. Could someone please walk me through the process of installing the drivers from the supplied cd (the machine does not have internet access yet).

OS is Ubuntu 10.04; Realtek 11n USB WLAN: Model# RTL8191S.

 Thank you.

---

### Post by MaindotC on 2010-09-16
Realtek drivers are installed by default.  Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and you'll probably just need to follow the [modprobe section](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#modprobe) for whichever one you need.

---

### Post by houndbytes on 2010-09-21
Thanks for the help! New problem:

Linux now sees the WLAN Adapter, but the message I now get is "device disabled." How do I enable the WLAN?

---

### Post by MaindotC on 2010-09-24
Aside from the guide, you'll need to figure that out because you have the machine.  It sounds like the device could be disabled in the BIOS or you could have a killswitch on your machine that turns it on/off.  If it's not a hardware issue then commands like "ifconfig <device_name> up" are listed in the guide.

---

### Post by houndbytes on 2010-09-25
Thanks problem solved. Conflict with internal card vs usb card. Turned off internal card adapter and the usb now says "device is ready." Thanks again!

---

