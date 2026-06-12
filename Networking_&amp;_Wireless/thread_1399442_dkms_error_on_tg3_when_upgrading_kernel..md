---
title: "dkms error on tg3 when upgrading kernel."
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by phorgan1 on 2010-02-05
did an apt-get distupgrade and got a new kernel (2.6.31-19) today and got this error:
> Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-19-generic
 *  tg3 (3.72.1)...                                                             tg3 (3.72.1): Unable to locate /var/lib/dkms/tg3/3.72.1/source/dkms.conf
        DKMS tree must be manually fixed.

/var/lib/dkms/tg3/3.72.1/source is a symbolic link to /usr/src/tg3-3.72.1, which doesn't exist.
/var/lib/dkms/tg3/3.72.1 contains:
2.6.20-15-generic/  2.6.20-16-generic/	source@
which looks pretty old, so I'm wondering if this whole dkms thing is not used anymore?  

Since it's my tg3 is the driver for my ethernet hardware (a Broadcom NetLink BCM5906M Fast Ethernet PCI Express), I'm afraid that if I reboot, I'll lose ethernet access, but I presume that my wireless will still work.

I checked packages with apt-cache search tg3 and found tg3-dkms. I tried install, it was at the current level.  I tried aptitude reinstall tg3-dkms and was told 
> E: I wasn't able to locate file for the tg3-dkms package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the tg3-dkms package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download


I do have:
[QUOTE]
/lib/firmware/2.6.31-18-generic/tigon/tg3_tso5.bin
/lib/firmware/2.6.31-19-generic/tigon/tg3.bin
/lib/firmware/2.6.31-19-generic/tigon/tg3_tso.bin
/lib/firmware/2.6.31-19-generic/tigon/tg3_tso5.bin

/lib/modules/2.6.31-19-generic/kernel/drivers/net/tg3.ko


HELP!!!

---

