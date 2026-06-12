---
title: "Mobidata EDGE modem issue with Linux Kernel (cp2101.c)"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by omarshehab on 2009-06-16
Hi,

I was trying to plug in a Mobidata EDGE modem (100EU) to my Linux (Ubuntu 8.04.2, kernel 2.6.24). It was not working. The lsusb command shows a device id 10CE:EA6A. In the line of 100 of cp2101.c, it says the device id should be 10C5:EA61. I think that's the source of problem everyone is facing with Mobidata EDGE modem. You may like to follow this link to see how many people are acing this problem.

I assume the solution is to edit the line or add a new line for Mobidata EDGE Modem 100EU and recompile the kernel.

The new line should be,

    { USB_DEVICE(0x10CE, 0xEA6A) }, /* Silicon Labs MobiData GPRS USB Modem 100EU */

Here in Bangladesh, a lot number of people and enterprises  are using this model and facing problem while migrating to Linux. So, we, Bangladesh Open Source Network ([www.bdosn.org](www.bdosn.org)), are trying to come up with a solution so that we can promote migration to Linux more cost effectively.

Thanks in advance for your reply.

---

