---
title: "Ubuntu 5.04 wireless"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by Nixforce on 2006-07-04
Hi All,

Ive installed a pc at home, its running Ubuntu 5.04.. Im looking for drivers for a wireless usb stick .. it is a USB 2.0 802.11g wireless lan adapter, it has a FCC ID of NHPWLG1500... Does anyone know where i can get drivers for this?

Thanks

---

### Post by Dr. Nick on 2006-07-04
from a terminal run 

**lsmod**

and look on the line usbcore, their may already be a driver their, If not then you may need to look into ndiswrapper

---

