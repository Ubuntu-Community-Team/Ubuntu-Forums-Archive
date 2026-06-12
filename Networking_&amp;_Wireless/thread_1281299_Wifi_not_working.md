---
title: "Wifi not working"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by krishnamohan on 2009-10-03
I have an atheros 802.11 driver installed....It is enabled and the status is "in use"....although ubuntu warns me against using this driver as the source code is not free..

Network manager does not detect wifi...

I run iwconfig and I get...

lo        no wireless extensions.

eth0      no wireless extensions.


I have wifi working in windows.....how do i get it to work here?

---

### Post by sendblink23 on 2009-10-03
random question...  but did you get wireless access through running the Live Cd? (*clicking the network icon & receive any signal)

---

### Post by krishnamohan on 2009-10-04
No....in ubuntu....clicking on the network icon...I do not see any networks detected...if I got your question right...

---

### Post by Iowan on 2009-10-04
**lshw -C network** will provide more details.

---

### Post by krishnamohan on 2009-10-05
The command gave...

*-network UNCLAIMED
       description: Ethernet controller
product:AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id:0
bus info: pci@0000:01.:00.0
version:01
width:64 bits
clock:33 MHz
capabilites: pm msi pciexpress msix cap_list
configuration:latency=0


I dont know if there is anything useful in there.....

---

### Post by Iowan on 2009-10-05
[This]("http://ubuntuforums.org/showpost.php?p=8042532&postcount=3") post includes some links for the AR242x. Hope one will help.

---

