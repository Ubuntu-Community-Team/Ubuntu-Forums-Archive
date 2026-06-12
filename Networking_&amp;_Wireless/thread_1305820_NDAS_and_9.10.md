---
title: "NDAS and 9.10"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by sonic167 on 2009-10-30
Has anyone tried NDAS driver with Ubuntu 9.10 yet (kernel 2.6.31)?
I mean following these infamous instructions: [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB]("http://http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB")
Given past experience/threads with this driver, I'm hesitating in upgrading to 9.10 as I don't want to lose my wireless connection to my NDAS drive ...
I skipped 9.4 for that reason ... (although it seems 9.4 finally worked with Linux2.6.28.patch.zip).

Thanks,

Vince.

---

### Post by joanmunoz on 2009-11-01
> **sonic167 said:**
> Has anyone tried NDAS driver with Ubuntu 9.10 yet (kernel 2.6.31)?
I mean following these infamous instructions: [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB]("http://http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB")
Given past experience/threads with this driver, I'm hesitating in upgrading to 9.10 as I don't want to lose my wireless connection to my NDAS drive ...
I skipped 9.4 for that reason ... (although it seems 9.4 finally worked with Linux2.6.28.patch.zip).

Thanks,

Vince.

Yes, I did. And it worked. But now you have to patch 5 times instead of 3 and in a particular order (provided here [http://code.ximeta.com/trac-ndas/ticket/1110#comment:36](http://code.ximeta.com/trac-ndas/ticket/1110#comment:36)). And you have to add a file (ndas-core.conf) to etc/modprobe.d providing the name of the interface you use to connect to the NDAS device (eth1 in my case) as commented here ([http://code.ximeta.com/trac-ndas/ticket/839#comment:1](http://code.ximeta.com/trac-ndas/ticket/839#comment:1)) It takes time, but it works.

Regards

Joan

---

### Post by bitjeklein on 2009-11-01
> **joanmunoz said:**
> Yes, I did. And it worked. But now you have to patch 5 times instead of 3 and in a particular order (provided here [http://code.ximeta.com/trac-ndas/ticket/1110#comment:36](http://code.ximeta.com/trac-ndas/ticket/1110#comment:36)). And you have to add a file (ndas-core.conf) to etc/modprobe.d providing the name of the interface you use to connect to the NDAS device (eth1 in my case) as commented here ([http://code.ximeta.com/trac-ndas/ticket/839#comment:1](http://code.ximeta.com/trac-ndas/ticket/839#comment:1)) It takes time, but it works.

Regards

Joan

Hi Joan,

Thanks for confirming that NDAS works on ubuntu 9.10.
I went to the links you provided, but it is unclear to me, what patches need to be applied, and how to do that.
Is it possible to outline all the steps that are needed to install NDAS correctly on ubuntu 9.10??

Thanks a million!

Bitje

---

### Post by sonic167 on 2009-11-13
Well ... somehow I got the guts to upgrade from 8.10 to 9.4 hoping to next get on 9.10 ... oh boy! the things you learn by making mistakes ... and now (on 9.4 I think, not sure anymore ...) the Desktop won't launch! 
I'm searching the forum to fix this, but it might be awhile until I get to test this NDAS thing on 9.10 (if I ever get Ubuntu on my computer again ...).

I hate to say this, but good old w2k gets things done.

Ubuntu: It ain't broken until you upgrade it!

Keep you posted.

Vince.

---

