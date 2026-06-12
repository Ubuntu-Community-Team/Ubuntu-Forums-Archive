---
title: "IVTV Install Failing"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by scubapup on 2006-12-12
I'm new to Ubuntu (I just installed 6.10) and am trying to setup MythTV, but running into trouble getting Ubuntu to see my PVR-350 card  

I've tried installing IVTV through Synaptic, but no luck

So I tried this HowTo:  [https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper) and everything seems to work until I get to the sudo m-a a-i ivtv0.4 (the buildlog is posted below)

Any idea what I'm doing wrong?

dh_clean
/usr/bin/make KVER=2.6.17-10-generic KDIR=/lib/modules/2.6.17-10-generic/build HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 clean
make[1]: Entering directory `/usr/src/modules/ivtv0.4'
/usr/bin/make -C /lib/modules/2.6.17-10-generic/build M=/usr/src/modules/ivtv0.4 clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CLEAN   /usr/src/modules/ivtv0.4/.tmp_versions
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
rm -f ivtv-svnversion.h ivtv-svnversion.h.tmp
make[1]: Leaving directory `/usr/src/modules/ivtv0.4'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ivtv0.4'
dh_clean
/usr/bin/make KVER=2.6.17-10-generic KDIR=/lib/modules/2.6.17-10-generic/build HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 clean
make[2]: Entering directory `/usr/src/modules/ivtv0.4'
/usr/bin/make -C /lib/modules/2.6.17-10-generic/build M=/usr/src/modules/ivtv0.4 clean
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
rm -f ivtv-svnversion.h ivtv-svnversion.h.tmp
make[2]: Leaving directory `/usr/src/modules/ivtv0.4'
/usr/bin/gcc-4.1
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.17-10-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.17-10-generic/g ;s/#KVERS#/2.6.17-10-generic/g ; s/_KVERS_/2.6.17-10-generic/g ; s/##KDREV##/2.6.17-10.33/g ; s/#KDREV#/2.6.17-10.33/g ; s/_KDREV_/2.6.17-10.33/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
/usr/bin/make KVER=2.6.17-10-generic KDIR=/lib/modules/2.6.17-10-generic/build HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1
make[2]: Entering directory `/usr/src/modules/ivtv0.4'
created ivtv-svnversion.h
/usr/bin/make  -C /lib/modules/2.6.17-10-generic/build M=/usr/src/modules/ivtv0.4 KERNELRELEASE=2.6.17-10-generic modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /usr/src/modules/ivtv0.4/msp3400.o
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_reset’:
/usr/src/modules/ivtv0.4/msp3400.c:229: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:233: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_read’:
/usr/src/modules/ivtv0.4/msp3400.c:258: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:264: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:269: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_write’:
/usr/src/modules/ivtv0.4/msp3400.c:284: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:289: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:295: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_set_scart’:
/usr/src/modules/ivtv0.4/msp3400.c:458: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_setvolume’:
/usr/src/modules/ivtv0.4/msp3400.c:490: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_setbass’:
/usr/src/modules/ivtv0.4/msp3400.c:503: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_settreble’:
/usr/src/modules/ivtv0.4/msp3400.c:511: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_setmode’:
/usr/src/modules/ivtv0.4/msp3400.c:520: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_setstereo’:
/usr/src/modules/ivtv0.4/msp3400.c:599: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:608: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:622: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:641: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:647: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:651: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:655: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:658: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:673: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:687: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_print_mode’:
/usr/src/modules/ivtv0.4/msp3400.c:708: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:711: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:715: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:718: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:722: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘autodetect_stereo’:
/usr/src/modules/ivtv0.4/msp3400.c:778: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:792: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:825: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:839: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:845: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3400c_thread’:
/usr/src/modules/ivtv0.4/msp3400.c:939: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:941: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:943: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:946: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:958: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:982: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:994: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1030: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1119: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp34xx_modus’:
/usr/src/modules/ivtv0.4/msp3400.c:1173: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1183: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1186: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1189: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1192: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp3410d_thread’:
/usr/src/modules/ivtv0.4/msp3400.c:1224: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1227: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1229: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1232: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1243: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1263: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1279: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1285: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1293: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1385: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp34xxg_thread’:
/usr/src/modules/ivtv0.4/msp3400.c:1467: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1471: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1473: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1476: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1492: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1503: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1506: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1511: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1515: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1530: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp34xxg_set_source’:
/usr/src/modules/ivtv0.4/msp3400.c:1555: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp34xxg_detect_stereo’:
/usr/src/modules/ivtv0.4/msp3400.c:1606: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: At top level:
/usr/src/modules/ivtv0.4/msp3400.c:1669: error: unknown field ‘owner’ specified in initializer
/usr/src/modules/ivtv0.4/msp3400.c:1669: warning: initialization makes integer from pointer without a cast
/usr/src/modules/ivtv0.4/msp3400.c:1671: error: unknown field ‘name’ specified in initializer
/usr/src/modules/ivtv0.4/msp3400.c:1671: warning: initialization makes integer from pointer without a cast
/usr/src/modules/ivtv0.4/msp3400.c:1673: error: unknown field ‘flags’ specified in initializer
/usr/src/modules/ivtv0.4/msp3400.c:1673: error: ‘I2C_DF_NOTIFY’ undeclared here (not in a function)
/usr/src/modules/ivtv0.4/msp3400.c:1688: error: ‘I2C_CLIENT_ALLOW_USE’ undeclared here (not in a function)
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp_attach’:
/usr/src/modules/ivtv0.4/msp3400.c:1707: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1737: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1747: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1750: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1774: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1775: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1808: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp_command’:
/usr/src/modules/ivtv0.4/msp3400.c:1953: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1994: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:1996: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2047: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2075: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2082: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2084: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2086: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2088: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2090: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2092: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2094: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2096: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2111: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2121: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2131: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c:2308: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp_suspend’:
/usr/src/modules/ivtv0.4/msp3400.c:2332: error: ‘struct i2c_driver’ has no member named ‘name’
/usr/src/modules/ivtv0.4/msp3400.c: In function ‘msp_resume’:
/usr/src/modules/ivtv0.4/msp3400.c:2345: error: ‘struct i2c_driver’ has no member named ‘name’
make[4]: *** [/usr/src/modules/ivtv0.4/msp3400.o] Error 1
make[3]: *** [_module_/usr/src/modules/ivtv0.4] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ivtv0.4'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ivtv0.4'
make: *** [kdist_build] Error 2

---

### Post by majoridiot on 2006-12-12
it looks like you might not have the correct (or any) kernel headers.  check that first. :)

---

### Post by superm1 on 2006-12-13
Your following the dapper howto on edgy.  Not gonna go.... Use the edgy howto.

---

### Post by scubapup on 2006-12-13
Thanks - that solved it - Here's the howto I used:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

---

