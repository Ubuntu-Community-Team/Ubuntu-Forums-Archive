---
title: "Wireless on Boot Up Question (Not the usual one I don't think)"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by tonofclay on 2006-07-12
Ok well I think the normal problem I saw most people posting about was their wireless device not being active on bootup. In my case, eth1 (my wireless device) is active when I boot up, as evidenced by system->administration->networking telling me eth1 is active. My internet doesn't work on bootup however, so what I have to do each time is go to networking, and then under properties for eth1 I have to reset the essid. The essid is correct when I boot up, but I just have to enter it in again to get things working.

Is there someway to get around doing this every bootup? Also if I was not clear, I apologize, I can try to explain more if something is unclear...

---

### Post by TFrog on 2006-07-20
I have a similar problem in Kubuntu.  I've got my Broadcom BCM4318 Air Force card working with ndiswrapper but with each reboot I have to log back into the network.  would be nice if I could boot right into it as you're talking about.  I've seen some things but most are for older versions of Ubuntu/Kubuntu.  Would be nice if someone were able to tell us what it is we need to do.

---

### Post by beemer on 2006-07-21
I had a similar issue.

if you do an lsmod from command line, you may see another driver in conjunction with ndiswrapper that is trying to control your card.

In mine, it showed an islsm_usb driver (others I've seen on web were islsm_pci).  I addeded the following line to the end of /etc/modprobe.d/blacklist:

blacklist islsm_usb

You may have something different to blacklist.  After I rebooted, ndiswrapper had the adapter all to itself and has been working fine under a 386 kernel (686 locks up after a bit - but that's another issue)

Beemer

---

