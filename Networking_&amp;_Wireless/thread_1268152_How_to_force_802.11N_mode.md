---
title: "How to force 802.11N mode?"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by isterios on 2009-09-16
Hello,

I own a wifi router which permits the 802.11 N mode, and a eeepc with Ralinktech 2860 wifi card (N mode).

By the way, the connection shows a 802.11 G link. The router is well configured (verified many times).

Is there a way to force or to set the N mode please?

thanks.



lshw -C network
*-network
description: Wireless interface
product: RT2860
vendor: RaLink
physical id: 0
bus info: pci@0000:01:00.0
logical name: ra0
version: 00
serial: 00:15:af:...
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2860 ip=X.X.X.X latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless

Kernel 2.6.29-1

---

### Post by akmofo on 2009-09-17
I have an AR5008 chipset using the ATH9k driver.

I'm having a hell of a time getting this to work as well.  I can connect to the 802.11n access point using the 5ghz band, but it's only connecting at 54mbps.  Running 'iw list' only shows speeds up to 54mbps.

Anyone had any success connecting at anything higher than 54 on a 11n network?

---

### Post by t0mppa on 2009-09-18
Well, you can manually force a new rate by running **sudo iwconfig <interface_logical_name> rate <rate_in_Mbs>M**, however only the rates supported by the AP can be used, which you can find by doing a **sudo iwlist scan** and checking the details of your AP.

The draft-n support is not fully finished in these programs though, so it may be that you cannot get iwconfig to show any higher rates than 54M or 60M, which has been reported by other users as well, but then checking the connection information from the AP has confirmed that they've had draft-n rates on their connections.

---

### Post by solca on 2009-11-19
If you want 802.11n speeds check this [post]("http://ubuntuforums.org/showthread.php?p=8346399#post8346399").

---

### Post by kubuntuuser on 2010-10-16
After compiling the latest driver from ralinktech.com and after some investigation I found that the driver been loaded was rt2800pci not rt2860sta. I found if I blacklisted the driver it meant it worked perfectly and I get N speeds upto 270

---

