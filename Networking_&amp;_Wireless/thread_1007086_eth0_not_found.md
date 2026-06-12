---
title: "eth0 not found"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by aswin on 2008-12-10
Dear all,
I just installed ubuntu 8.10 on my single board Intel Atom chipset. I cannot connect to the internet.

Output of ifconfig -a gives only "lo" and "pan0"

Output of sudo lshw -C network
*-network UNCLAIMED
description: 82574L Gigabit Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width :32 bits
clock: 33MHz

Thanks in advance
Aswin

---

### Post by jinx099 on 2008-12-30
I had a similar problem with my new Intel PCI-e NIC (same chipset).  It appears that Ubuntu 8.10's e1000e driver does not yet support the new chipset.  I compiled the new driver from intel's website and now it is working great.

You may find these links useful:

[http://www.intel.com/products/desktop/adapters/gigabit-ct/gigabit-ct-overview.htm]("http://www.intel.com/products/desktop/adapters/gigabit-ct/gigabit-ct-overview.htm")
[Linux driver downloads]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3025&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go!")

---

