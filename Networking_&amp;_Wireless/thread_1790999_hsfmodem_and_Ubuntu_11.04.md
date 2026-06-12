---
title: "hsfmodem and Ubuntu 11.04"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by Je Et on 2011-06-26
I need help. This is a section from scanmodem:

From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download **hsfmodem-7.80.02.05full_k2.6.38_8_generic_ubuntu_i386.deb.zip** 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.

The thing is, **there is no hsfmodem-7.80.02.05full_k2.6.38_8_generic_ubuntu_i386.deb.zip**, or if it is, I can't find it.  So I try to install the generic deb from the site, and here is build log file:

driver version 7.80.02.06full
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1320:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1369:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1396:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
/usr/lib/hsfmodem/modules/osnvm.c:408:8: error: 'MUTEX' undeclared here (not in a function)
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2


I don't know what most of this says and any help would be appreciated.

Je Et:(:confused::(

---

### Post by rock_rebel on 2011-07-07
> **Je Et said:**
> I need help. This is a section from scanmodem:

From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download **hsfmodem-7.80.02.05full_k2.6.38_8_generic_ubuntu_i386.deb.zip** 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.

The thing is, **there is no hsfmodem-7.80.02.05full_k2.6.38_8_generic_ubuntu_i386.deb.zip**, or if it is, I can't find it.  So I try to install the generic deb from the site, and here is build log file:

driver version 7.80.02.06full
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1320:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1369:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1396:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
/usr/lib/hsfmodem/modules/osnvm.c:408:8: error: 'MUTEX' undeclared here (not in a function)
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2


I don't know what most of this says and any help would be appreciated.

Je Et:(:confused::(

I'm getting those exact same error messages when I try to install the generic hsfmodem driver. I have an IBM Thinkpad T60 with Ubuntu 11.04 running kernel 2.6.38-8.

"MUTEX" sounds like a breakfast cereal to me.

---

### Post by Je Et on 2011-07-08
> **rock_rebel said:**
> I'm getting those exact same error messages when I try to install the generic hsfmodem driver. I have an IBM Thinkpad T60 with Ubuntu 11.04 running kernel 2.6.38-8.

"MUTEX" sounds like a breakfast cereal to me.

Thanks for posting.  I did find some Agere modems and am waiting on them now, at least that's the solution for me. For all the people with on-board modems, it seems to me that linuxant would offer better support to people that already have their products.[U][B][URL="http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php"]
[/URL][/B][/U]

---

