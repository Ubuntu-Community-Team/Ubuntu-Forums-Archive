---
title: "Ubuntu 12.xx wireless driver issues for PEN testers"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by freemonj on 2012-05-30
In the event you have updated your kernel, etc. or recompiled your wireless driver for the purposes of packet injection (aircrack-ng),etc. and you mucked up the interface like I did this site was a rescue for me for all Intel Manufactured wifi cards both integrated, USB or SATA interfaces. 

[http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)

The microcode reinstallation solved my problem after hours/days of trouble shooting, uninstalling packages, etc. when I did not need to. I wanted to share this with the next troubled soul who encounters this problem. If your manufacture is not Intel as long as they suppot Linux their support page should provide the driver as well for that make and model. Either recompile, copy over the tainted version and after HAL is initiated during re-boot you should be good to go.

Word of advice use a USB wifi NIC for all packet injection use cases if you are a PEN tester. Make certain before you purchase the card you do your homework first to make sure the "chipset" (not the make or model) is supported by the Linux kernel 3.x if you using Ubuntu 12.xx.

---

