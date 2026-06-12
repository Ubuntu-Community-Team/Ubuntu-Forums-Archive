---
title: "[SOLVED] Ati Linux driver wiki installation HELP"
date: 2009-01-03
forum: Multimedia Software
---

### Post by hzs11112 on 2009-01-03
i am following the procedures given here 
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)
to install the restricted rivers manually but i am stuck at this part.

For 32-bit systems
Terminal Command

sudo dpkg -i xorg-driver-fglrx_8.561-0ubuntu1_i386.deb fglrx-kernel-source_8.561-0ubuntu1_i386.deb fglrx-amdcccle_8.561-0ubuntu1_i386.deb

**(This may fail due to a missing dpmk. If so install this first)** 

what does the above bold line means. I have no idea what is a missing dpmk and how do i install it. I am to tally blank on that. pls help

Thank you

---

### Post by cariboo on 2009-01-03
That may be a typo there is no dpmk package. I think it might be dkms that is needed. Open System-->Administration-->Synaptic, and searc to see if dkms is installed. Before you continue trying to install the driver, make sure you are fully updated.

Jim

---

### Post by hzs11112 on 2009-01-03
thanx for the info ... i updated my pc first and then followed the procedures and now my graphics card is working fine.

---

