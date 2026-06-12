---
title: "Wireless Not Working: Natty Narwhal in VMWare Workstation"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by matingara on 2011-07-30
Hi!

I started playing with Natty Narwhal (11.04) last week.  I have a Toshiba Portege R700 laptop with 4GB of memory.

Firstly, let me say that when I run 11.04 on the bare metal laptop (installed via WUBI) it appears to work flawlessly.  That is, both the ethernet (hard wired) network and the wifi network work just fine.

The networking problem occurs when I try to run 11.04 as a (Type 2) VM in VMWare workstation with an underlying o/s of Windows 7 Enterprise.

In this mode, the ethernet network works fine but the wireless network does not work.  The o/s does not even see the wireless card.  I have downloaded and installed about 216 MB of updates from the update center to no avail.  I have "bridged" the VMWare "virtual switch" across to both the ethernet port and the wireless port (see below):

Basically, it appears that the interface is not being presented to the VM.

Also, of interest, Unity which works fine on the bare metal install does not run on the Ubuntu 11.04 VM.

Any suggestions welcomed.

Thanks,

  -- Joel.

---

### Post by matingara on 2011-07-30
BTW, VMWare workstation version is 7.1.4 build-385536.

---

