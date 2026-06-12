---
title: "X8SIL-F Intel 82574L driver for 10.04"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by waspinator on 2011-03-04
Hi,

Just got a SuperMicro X8SIL-F board, and I'm having trouble getting the onboard Ethernet controllers to work. They are both Intel 82574L Gigabit. One of them has (rev ff) at the end in lspci.

Out of the box, both controllers show up as eth0 and eth1, but the connection on either is flaky and unreliable. I installed an updated driver from the [Intel Download Center]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817"), but now I lost one of my controllers and only have eth0. They still both show up in lspci. I installed the driver by extracting the archive and running **make install** in the **src** folder, then restarting.

I'm running Ubuntu 10.04 amd64 64bit 2.6.32-24-generic.

Has anyone used this board with success?

Thanks,
Waspinator

---

### Post by waspinator on 2011-03-05
found something interesting in /var/log/messages. Any Ideas of what I could do?
Thanks

```
Mar  5 09:01:45 ubuntu kernel: [ 1143.053567] e1000e 0000:05:00.0: Refused to change power state, currently in D3
Mar  5 09:01:45 ubuntu kernel: [ 1143.053576] e1000e 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar  5 09:01:45 ubuntu kernel: [ 1143.054021] e1000e 0000:05:00.0: PCI INT A disabled
Mar  5 09:01:45 ubuntu kernel: [ 1143.054030] e1000e: probe of 0000:05:00.0 failed with error -2

```

---

### Post by waspinator on 2011-03-11
I solved this problem by updating to a newer kernel (2.6.37) using the kernel ppa ( ppa:kernel-ppa/ppa ). It included an older than the 1.3 version I downloaded from Intel, but it worked for both network cards.

```

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo apt-get install linux-headers-2.6.37-17-generic linux-image-2.6.37-17-generic

```

---

