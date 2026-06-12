---
title: "Wireless crash after upgrading to 11.04"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by gavdari on 2011-04-30
I just upgraded to Kubuntu 11.04 and I have a problem with network manager. When I plug in my LAN, everything works fine, but when I try to use my wireless connection, everything hangs after a few seconds. I'm guessing it's a cpu overload problem, since CPU fan starts after a while. But I can't move my mouse and keyboard doesn't work either. I tried network-manager-gnome and reinstalling wireless driver, but it didn't solve the problem. Any idea?

---

### Post by gavdari on 2011-04-30
Just for the record, it looks like activating/deactivating the wireless driver fore a few more times solved the problem for now.

---

### Post by macrophenomenal on 2011-04-30
hi this is also happening to me.
I am using a HP2133 with Broadcom STA wireless driver BCM 4312 (Rev 1.0)

I upgraded to 11.04 and my system hangs if I connect to a wireless network.
LAN appears to work fine though.

---

### Post by blatanville on 2011-04-30
Seems like after a re-boot or two, my wifi interface completely disappeared from the system. The old wifi profile is still there in network management, excepting it has forgotten the WPA key.

using the "scan" button when trying to create a new wireless profile yields no results, i.e. the wireless adapter seems to be completely non-functional.

I have tethered my smartphone to the machine (a first-generation intel iMac), and am connecting well that way, but this is not an "optimal solution"

could this be a coincidence (that the wireless adapter failed at approx. the same time as my upgrade to 11.04)?
Is there a way to examine the hardware in more detail (like Windows's "device manager")?

help!

---

### Post by pdecarlos on 2011-05-03
> **macrophenomenal said:**
> hi this is also happening to me.
I am using a HP2133 with Broadcom STA wireless driver BCM 4312 (Rev 1.0)

I upgraded to 11.04 and my system hangs if I connect to a wireless network.
LAN appears to work fine though.

Same behaviour on my HP 2133 with 11.04. I have tested it after upgrading from 10.10 and with a clean installation.

---

### Post by Stephen_d on 2011-05-03
There appears to be a bugfix request in launchpad on this issue located [here]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/154568"). Lets hope this gets resolved quickly as I am missing my wireless connection. :(

---

### Post by Stephen_d on 2011-05-04
Gavdari do you have your wireless working? 
If you do are you able to provide the kernel driver the device is using? Minie is trying to use the b43-pci-bridge and is hanging as soon as I connect to a wireless network.

---

