---
title: "stuck on making zd1211"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Porch on 2006-06-07
root@PorchNET:/home/porch/zd1211-driver-r77# make
/lib/modules/2.6.15-23-386/build
/home/porch/zd1211-driver-r77
-I/home/porch/zd1211-driver-r77/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/porch/zd1211-driver-r77 modules
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
make: *** [all] Error 2


I got the kernel source and headers installed. I can't figure out what I have to install that puts stuff in build that the driver is looking for.  What am I missing. 

Thanks

---

### Post by flurl on 2006-06-07
try creating a symlink from /usr/src/linux-headers-2.6.15-23-386 to /lib/modules/2.6.15-23-386/build
```
ln -s /usr/src/linux-headers-2.6.15-23-386 /lib/modules/2.6.15-23-386/build
```

---

### Post by shof2k on 2006-06-12
Try my how to at [http://www.ubuntuforums.org/showthread.php?t=195259](http://www.ubuntuforums.org/showthread.php?t=195259)

---

