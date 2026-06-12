---
title: "WiFi problem on Dell inspiron 1525"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by gentleDean on 2010-01-05
Hi,

Have installed Ubuntu 9.10 on my dell inspiron 1525 laptop. I can connect to internet via wired connection, it just accessible by default.
But while connecting via WiFi, it doesnt show any wireless connection there. (I can access bluetooth at the same time). 

I also found some proprietary drivers in Hardware Management, Wireless Drivers were present but while activating the same only "downloading & installing" screen pops up and stale for hours.

Please help me on this issue, post any package available.

Thanks in advance !!

---

### Post by rednex on 2010-01-08
Yesterday I installed Ubuntu on Dell Inspiron 1525.
After installing updates Ubuntu can automatically discover wireless driver. So do the following:

1. Install Ububtu from CD/DVD
2. Temporary connect to the Internet using wired Ethernet port, download and install all updates.
3. Reboot your system.
4. Click System > Administration > Hardware Drivers. It should ask to activate the wireless driver.
5. Activate the driver, unplug wired connection and reboot. You are all set!

---

### Post by petesimson on 2010-01-14
I installed Ubuntu 9.10 on a Dell Inspiron 1525 and the wifi worked after turning on the little switch on the right side of the laptop.  Configure the security settings with <System/Preferences/Network Connections/Wireless>
This worked for me without having to do anything with drivers.  Forgetting to turn on the switch is easy to do!!!

---

