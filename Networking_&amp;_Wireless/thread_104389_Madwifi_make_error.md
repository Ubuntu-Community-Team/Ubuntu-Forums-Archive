---
title: "Madwifi make error"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by coderasm on 2005-12-16
I'm trying to compile madwifi for my DWL-G132 usb wifi adapter.  After issuing the make command I receive this error at the end of the output screen.  Any ideas on what I'm doing wrong?  Thanks for any help.

root@ubuntu:/madwiflies/madwifi-ng# make
Checking requirements... ok.
Checking kernel configuration... ok.
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath ./tools ; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/madwiflies/madwifi-ng/ath_hal'
cp -f ./../hal/public/i386-elf.opt_ah.h opt_ah.h
cp -f ./../hal/linux/ah_osdep.c ah_osdep.c
/usr/bin/uudecode ./../hal/public/i386-elf.hal.o.uu
make -C /usr/src/linux-headers-2.6.12-10-686 SUBDIRS=/madwiflies/madwifi-ng/ath_hal MODVERDIR=/madwiflies/madwifi-ng/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /madwiflies/madwifi-ng/ath_hal/ah_osdep.o
  LD [M]  /madwiflies/madwifi-ng/ath_hal/ath_hal.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /madwiflies/madwifi-ng/ath_hal/.hal.o.cmd for /madwiflies/madwifi-ng/ath_hal/hal.o
  CC      /madwiflies/madwifi-ng/ath_hal/ath_hal.mod.o
  LD [M]  /madwiflies/madwifi-ng/ath_hal/ath_hal.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: Leaving directory `/madwiflies/madwifi-ng/ath_hal'
make[1]: Entering directory `/madwiflies/madwifi-ng/net80211'
make -C /usr/src/linux-headers-2.6.12-10-686 SUBDIRS=/madwiflies/madwifi-ng/net80211 MODVERDIR=/madwiflies/madwifi-ng/net80211/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /madwiflies/madwifi-ng/net80211/if_media.o
cc1: warnings being treated as errors
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /madwiflies/madwifi-ng/net80211/if_media.c:60:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
make[3]: *** [/madwiflies/madwifi-ng/net80211/if_media.o] Error 1
make[2]: *** [_module_/madwiflies/madwifi-ng/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/madwiflies/madwifi-ng/net80211'
make: *** [all] Error 1

---

### Post by Kaah on 2005-12-18
i have the same problem :(.

---

### Post by Lambert on 2005-12-18
There is no usb support currently in the madwifi driver.

There are plans to add usb support but the road map shows it's currently not expected until release 2.0. current release in svn is .9.4.5. The stable release 1.0 currently has no set release date and as for release 2.0; quote from madwifi wiki 

[quote] version 2.0.0 - far away[quote]


[http://www.madwifi.org/ticket/33]("http://www.madwifi.org/ticket/33")

[http://www.madwifi.org/roadmap]("http://www.madwifi.org/roadmap")

But to ask and try to answer your question, do you have your linux-headers and build-essential installed?

---

