---
title: "Broadcom STA kernel stub update for 2.6.28/2.6.29 kernel"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by vlovich on 2009-02-13
I recently found that the Broadcom STA driver does indeed work - when I had previously tried it from the Ubuntu repositories, it hadn't worked.  The version from the [Broadcom website]("http://www.broadcom.com/support/802.11/linux_sta.php") worked from the first time for me, but it's kernel stub doesn't work past 2.6.27 - didn't find the specific reason, but presumably due to refactoring work in the wireless Linux subsystem.

Here's the patch (I haven't tested it with 2.6.28, but it's working fine with 2.6.29-rc4).  In fact, the driver appears to work far better than the ndiswrapper version (better signal strength, better battery life).

The wifi chip I tested with is the tx2000 (BCM4328 802.11 a/b/g/n rev 03).

This is the best option so far until b43 supports this chipset.

---

### Post by Ayuthia on 2009-02-13
What version of the module are you using?  I have been able to compile 5.10.27.14 without patches on 2.6.28.3.

---

### Post by vlovich on 2009-03-02
Whatever the one was on the site I gave the link to.

---

### Post by TSJason on 2009-03-29
This didn't work for me in 2.6.29 stable. The module failed to compile with the patch provided in this post. I found another patch that worked from the Pardus project and was able to get it compiled and loaded, however I couldn't connect to any AP's (iwlist scanning did, however work). Here was what I did:

```

svn co [http://svn.pardus.org.tr/pardus/devel/kernel/drivers/broadcom-wl](http://svn.pardus.org.tr/pardus/devel/kernel/drivers/broadcom-wl)
wget [http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5_10_79_10.tar.gz](http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5_10_79_10.tar.gz)
mkdir hybrid_wl
cd hybrid_wl
tar zxfv ../hybrid-portsrc-x86_32-v5_10_79_10.tar.gz
patch -p1 < ../broadcom-wl/files/iwe_stream_api.patch
patch -p1 < ../broadcom-wl/files/linux-2.6.29.patch
patch -p1 < ../broadcom-wl/files/remove-module-aliases.patch
patch -p1 < ../broadcom-wl/files/wl_iw.patch
make -C /lib/modules/2.6.29/source M=`pwd` clean
make -C /lib/modules/2.6.29/source M=`pwd`
cp wl.ko /lib/modules/2.6.29/kernel/drivers/net/wireless/
depmod -a
modprobe wl

```

Maybe this will help someone else.

This is my hardware:
```

04:01.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
        Subsystem: Netgear Unknown device [1385:7d00]
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at dccfc000 (32-bit, non-prefetchable) [size=16K]

```

Unfortunately, according to linuxwireless [http://linuxwireless.org/en/users/Drivers/b43/devices](http://linuxwireless.org/en/users/Drivers/b43/devices) this hardware isn't supported under b43 either. I'm stuck with ndiswrapper for the time being.

---

