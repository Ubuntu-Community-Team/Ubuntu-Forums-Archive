---
title: "Compiling ACX for the new Ubuntu 9.10"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Adfc on 2009-11-02
I have a wireless pci card USR 5416, which has the chipset ACX 111. It worked fine in Ubuntu 9.04, but it is no more supported in Ubuntu 9.10, so I need to manually compile the acx module. I followed these instructions [http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu) but I found an error:

```
andrea@andrea-desktop:/usr/src/acx-20070101$ sudo make -C /lib/modules/2.6.31-14-generic/build M=`pwd`
[sudo] password for andrea: 
make: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /usr/src/acx-20070101/wlan.o
In file included from /usr/src/acx-20070101/acx.h:2,
                 from /usr/src/acx-20070101/wlan.c:49:
/usr/src/acx-20070101/wlan_compat.h:224: error: conflicting types for ‘irqreturn_t’
include/linux/irqreturn.h:16: note: previous declaration of ‘irqreturn_t’ was here
make[1]: *** [/usr/src/acx-20070101/wlan.o] Error 1
make: *** [_module_/usr/src/acx-20070101] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
```

Could someone help me in solving this problem?

Thank you very much.

---

### Post by chili555 on 2009-11-02
> but it is no more supported in Ubuntu 9.10No? What about this doesn't work for you?:> /lib/modules/2.6.28-16-generic/kernel/ubuntu/misc/wireless/acx/[COLOR="Red"]acx[/COLOR].ko

---

### Post by Adfc on 2009-11-02
2.6.28-16 is not the kernel of the new Ubuntu 9.10. If you check in the 9.10 (2.6.31-14 kernel), you will not find acx.ko module.

---

### Post by chili555 on 2009-11-02
Yikes! I need a trip to the eye doctor to get a few more grinds on these old tri-focals, it seems. I'm sorry about that.

I have googled this and it seems that ndiswrapper may the only way to get the *acx* going. 

As far as compiling the Sourceforge driver, I think that a driver built in January of 2007 is just too old to work successfully. Development stopped in early 2008, it seems, when the *acx* module was incorporated in the mainline kernel. Now, it seems it's an orphan.

---

### Post by aapo4 on 2009-11-09
There are official bug report and patch to compile acx.
[https://sourceforge.net/tracker/?func=detail&aid=2885407&group_id=75380&atid=543745](https://sourceforge.net/tracker/?func=detail&aid=2885407&group_id=75380&atid=543745)

Now it can be compiled, but I didn't get driver fully working.

---

### Post by superdav42 on 2009-11-24
I was also able to get it to compile with the patch but it did not work at all. 

I wish someone would put this in the mainline kernel so we don't have this problem.

---

### Post by aapo4 on 2010-03-30
I have removed networkmanager on my Ubuntu and have used patched ACX for 5 months without any harm.
(running with same time with networkmanager cause system freeze)

[http://cc.oulu.fi/~rantalai/acx_karmic.patch](http://cc.oulu.fi/~rantalai/acx_karmic.patch)

---

### Post by 5hawnk3lly on 2010-04-19
OMG I finally got this working on Karmic.    Needed to:   1] apt-get remove network-manager (other posts just say to stop it),  2] get most recent firmware and driver from sf.net,  3] get the patch for karmic,  4] apply the patch, compile, and install acx.ko,  5] insmod acx.ko,  6] use iwconfig and/or /etc/network/interfaces to set any parameters,  Acx kernel driver is no longer writing 1.5 GB per hour to syslog, messages, and kern.log!  Hurray.

---

