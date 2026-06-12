---
title: "Broadcom BCM43227 does not working on Acer Aspire 5755G"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by Pavel_Kulagin on 2013-09-03
Hi, I'm new in Linux, so some things are magic for me. I read dozens of threads about this Broadcom BCM43227 and did lots of things which were advised in them, but it still doesn't work for me.
I have Acer Aspire 5755G and Broadcom BCM43227 (14e4:4358), Ubuntu 12.04.

'sudo modprobe wl' shows:
FATAL: Module wl not found.

'sudo apt-get install --reinstall linux-headers-`uname -r`' and 'sudo apt-get --reinstall install bcmwl-kernel-source' fail with the same error and ask me to consult make.log, so I post the result here:
```
cat /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log
DKMS make.log for bcmwl-6.20.155.1+bdcom for kernel 3.8.0-29-generic (x86_64)
Tue Sep  3 13:56:31 MSK 2013
make: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function ‘wl_cfg80211_join_ibss’:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:705:26: error: ‘struct cfg80211_ibss_params’ has no member named ‘channel’
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: At top level:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warning: (near initialization for ‘wl_cfg80211_ops.scan’) [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warning: (near initialization for ‘wl_cfg80211_ops.set_tx_power’) [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warning: (near initialization for ‘wl_cfg80211_ops.get_tx_power’) [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function ‘wl_update_bss_info’:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1991:11: error: ‘struct cfg80211_bss’ has no member named ‘information_elements’
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1992:15: error: ‘struct cfg80211_bss’ has no member named ‘len_information_elements’
make[1]: *** [/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'
```

Could you help me to resolve this issue, please?

---

### Post by chili555 on 2013-09-03
Congratulations! It's an official bug! [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1095751](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1095751)

I am interested in comment #5 and #10:> I have been using raring version for a while (4 months) without any issue. Version 6.20.155.1+bdcom-0ubuntu6 manualy installedWhich version is being installed by apt?```
ls /var/cache/apt/archives/ grep bcmwl
```If it is not xx-0ubuntu[COLOR="#FF0000"]6[/COLOR], then I suggest you download and install it manually from here: [http://packages.ubuntu.com/raring/bcmwl-kernel-source](http://packages.ubuntu.com/raring/bcmwl-kernel-source) 

Install with:```
sudo dpkg -i bcmwl*.deb
```If it still ends in an error, we might try xx-0ubuntu3: [http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

If we find one that works, we'll tell Update Manager to *NOT* update the finally working version: ```
sudo apt-mark hold bcmwl-kernel-source
```I wish I could tell you the exact answer, however it installs perfectly on my 13.04 64-bit system!

Please post back the result so the searchers will learn what works!

---

### Post by Pavel_Kulagin on 2013-09-03
> **chili555 said:**
> 
Install with:```
sudo dpkg -i bcmwl*.deb
```

You're a magician, I thought that I have reinstalled bcmwl-kernel-source several times before posting this thread, but now it suddenly helps me and wi-fi starts working!

> **chili555 said:**
> 
```
ls /var/cache/apt/archives/ grep bcmwl
```If it is not xx-0ubuntu[COLOR=#FF0000]6[/COLOR], then I suggest you download and install it manually from here: [http://packages.ubuntu.com/raring/bcmwl-kernel-source](http://packages.ubuntu.com/raring/bcmwl-kernel-source) 


BTW, after installing xx-0ubuntu[COLOR=#FF0000]6 [/COLOR]sources, I see this output for 'ls /var/cache/apt/archives/ | grep bcmwl'
```
$ ls /var/cache/apt/archives/ | grep bcmwl
bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu[COLOR=#ff0000]0.0.1[/COLOR]_amd64.deb
```
So, it is not xx-0ubuntu6 even after installing downloaded bcmwl-kernel-source :)

Problem is solved now, thanks again!

---

