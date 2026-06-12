---
title: "Samba Broken"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by cbhargava on 2010-04-07
Hi,

I'm running samba on xubuntu 8.10 and it was running ok until recent updates. In the var/log/samba/log.<ipaddress-of-client> I get the following dump. The client is an ubuntu machine.

Any pointers would be appreciated.

Thanks.

*** glibc detected *** /usr/sbin/smbd: free(): invalid pointer: 0xb9b951e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb759a454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb759c4b6]
/usr/sbin/smbd(str_list_substitute+0x189)[0xb7b6f11d]
/usr/sbin/smbd[0xb7a2db27]
/usr/sbin/smbd(authorise_login+0xf1)[0xb7a2dd06]
/usr/sbin/smbd[0xb7a53914]
/usr/sbin/smbd(make_connection+0x796)[0xb7a55ecf]
/usr/sbin/smbd(reply_tcon_and_X+0x404)[0xb7da9cd3]
/usr/sbin/smbd[0xb7a4f4a6]
/usr/sbin/smbd(smbd_process+0x435)[0xb7a516c9]
/usr/sbin/smbd(main+0xfa6)[0xb7a18b7f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7541685]
/usr/sbin/smbd[0xb7a15b91]
======= Memory map: ========
b7200000-b7221000 rw-p b7200000 00:00 0 
b7221000-b7300000 ---p b7221000 00:00 0 
b7396000-b73a3000 r-xp 00000000 08:01 407343     /lib/libgcc_s.so.1
b73a3000-b73a4000 r--p 0000c000 08:01 407343     /lib/libgcc_s.so.1
b73a4000-b73a5000 rw-p 0000d000 08:01 407343     /lib/libgcc_s.so.1
b73b1000-b73c4000 rw-s 00000000 08:01 725702     /var/lib/samba/group_mapping.ldb
b73c4000-b73cd000 r-xp 00000000 08:01 407234     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b73cd000-b73ce000 r--p 00008000 08:01 407234     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b73ce000-b73cf000 rw-p 00009000 08:01 407234     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b73cf000-b73d6000 r-xp 00000000 08:01 407230     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b73d6000-b73d7000 r--p 00006000 08:01 407230     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b73d7000-b73d8000 rw-p 00007000 08:01 407230     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b73de000-b73e7000 rw-s 00000000 08:01 725689     /var/lib/samba/passdb.tdb
b73e7000-b73eb000 rw-s 00000000 08:01 725703     /var/lib/samba/account_policy.tdb
b73eb000-b73ed000 rw-s 00000000 08:01 725715     /var/lib/samba/ntdrivers.tdb
b73ed000-b73f7000 rw-s 00000000 00:12 14508      /var/run/samba/locking.tdb
b73f7000-b7401000 rw-s 00000000 00:12 14507      /var/run/samba/brlock.tdb
b7401000-b7417000 rw-s 00000000 00:12 14481      /var/run/samba/connections.tdb
b7417000-b7421000 r-xp 00000000 08:01 407232     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7421000-b7422000 r--p 00009000 08:01 407232     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7422000-b7423000 rw-p 0000a000 08:01 407232     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7424000-b7426000 rw-s 00000000 08:01 725716     /var/lib/samba/ntprinters.tdb
b7426000-b7427000 rw-s 00000000 08:01 725717     /var/lib/samba/ntforms.tdb
b7427000-b7428000 rw-s 00000000 00:12 14509      /var/run/samba/gencache.tdb
b7428000-b7429000 rw-s 00000000 00:12 14506      /var/run/samba/sessionid.tdb
b7429000-b742f000 rw-s 00000000 08:01 724850     /var/lib/samba/secrets.tdb
b742f000-b743f000 r--s 00000000 08:01 425127     /usr/share/samba/valid.dat
b743f000-b7441000 r-xp 00000000 08:01 355217     /usr/lib/gconv/IBM850.so
b7441000-b7442000 r--p 00001000 08:01 355217     /usr/lib/gconv/IBM850.so
b7442000-b7443000 rw-p 00002000 08:01 355217     /usr/lib/gconv/IBM850.so
b7443000-b7463000 r--s 00000000 08:01 423522     /usr/share/samba/lowcase.dat
b7463000-b7483000 r--s 00000000 08:01 425126     /usr/share/samba/upcase.dat
b7483000-b7486000 rw-p b7483000 00:00 0 
b7486000-b7489000 r-xp 00000000 08:01 407445     /lib/libgpg-error.so.0.3.0
b7489000-b748a000 rw-p 00002000 08:01 407445     /lib/libgpg-error.so.0.3.0
b748a000-b748c000 r-xp 00000000 08:01 407436     /lib/libkeyutils-1.2.so
b748c000-b748e000 rw-p 00001000 08:01 407436     /lib/libkeyutils-1.2.so
b748e000-b7495000 r-xp 00000000 08:01 353372     /usr/lib/libkrb5support.so.0.1
b7495000-b7496000 r--p 00006000 08:01 353372     /usr/lib/libkrb5support.so.0.1
b7496000-b7497000 rw-p 00007000 08:01 353372     /usr/lib/libkrb5support.so.0.1
b7497000-b74fd000 r-xp 00000000 08:01 407443     /lib/libgcrypt.so.11.4.4
b74fd000-b74fe000 r--p 00065000 08:01 407443     /lib/libgcrypt.so.11.4.4
b74fe000-b7500000 rw-p 00066000 08:01 407443     /lib/libgcrypt.so.11.4.4
b7500000-b7501000 rw-p b7500000 00:00 0 
b7501000-b7511000 r-xp 00000000 08:01 352711     /usr/lib/libtasn1.so.3.0.15
b7511000-b7513000 rw-p 0000f000 08:01 352711     /usr/lib/libtasn1.so.3.0.15
b7513000-b7529000 r-xp 00000000 08:01 351972     /usr/lib/libsasl2.so.2.0.22
b7529000-b752a000 r--p 00015000 08:01 351972     /usr/lib/libsasl2.so.2.0.22
b752a000-b752b000 rw-p 00016000 08:01 351972     /usr/lib/libsasl2.so.2.0.22
b752b000-b7683000 r-xp 00000000 08:01 407223     /lib/tls/i686/cmov/libc-2.8.90.so
b7683000-b7685000 r--p 00158000 08:01 407223     /lib/tls/i686/cmov/libc-2.8.90.so
b7685000-b7686000 rw-p 0015a000 08:01 407223     /lib/tls/i686/cmov/libc-2.8.90.so
b7686000-b7689000 rw-p b7686000 00:00 0 
b7689000-b7690000 r-xp 00000000 08:01 353403     /usr/lib/libwbclient.so.0
b7690000-b7691000 r--p 00006000 08:01 353403     /usr/lib/libwbclient.so.0
b7691000-b7692000 rw-p 00007000 08:01 353403     /usr/lib/libwbclient.so.0
b7692000-b7699000 r-xp 00000000 08:01 357158     /usr/lib/libtalloc.so.1.2.0
b7699000-b769a000 r--p 00006000 08:01 357158     /usr/lib/libtalloc.so.1.2.0
b769a000-b769b000 rw-p 00007000 08:01 357158     /usr/lib/libtalloc.so.1.2.0
b769b000-b76a3000 r-xp 00000000 08:01 407453     /lib/libpopt.so.0.0.0
b76a3000-b76a4000 r--p 00007000 08:01 407453     /lib/libpopt.so.0.0.0
b76a4000-b76a5000 rw-p 00008000 08:01 407453     /lib/libpopt.so.0.0.0
b76a5000-b76a6000 rw-p b76a5000 00:00 0 
b76a6000-b76a8000 r-xp 00000000 08:01 407226     /lib/tls/i686/cmov/libdl-2.8.90.so
b76a8000-b76a9000 r--p 00001000 08:01 407226     /lib/tls/i686/cmov/libdl-2.8.90.so
b76a9000-b76aa000 rw-p 00002000 08:01 407226     /lib/tls/i686/cmov/libdl-2.8.90.so
b76aa000-b76bf000 r-xp 00000000 08:01 407229     /lib/tls/i686/cmov/libnsl-2.8.90.so
b76bf000-b76c0000 r--p 00014000 08:01 407229     /lib/tls/i686/cmov/libnsl-2.8.90.so
b76c0000-b76c1000 rw-p 00015000 08:01 407229     /lib/tls/i686/cmov/libnsl-2.8.90.so
b76c1000-b76c3000 rw-p b76c1000 00:00 0 
b76c3000-b76d3000 r-xp 00000000 08:01 407238     /lib/tls/i686/cmov/libresolv-2.8.90.so
b76d3000-b76d4000 r--p 0000f000 08:01 407238     /lib/tls/i686/cmov/libresolv-2.8.90.so
b76d4000-b76d5000 rw-p 00010000 08:01 407238     /lib/tls/i686/cmov/libresolv-2.8.90.so
b76d5000-b76d7000 rw-p b76d5000 00:00 0 
b76d7000-b76da000 r-xp 00000000 08:01 407202     /lib/libattr.so.1.1.0
b76da000-b76dc000 rw-p 00003000 08:01 407202     /lib/libattr.so.1.1.0
b76dc000-b76e2000 r-xp 00000000 08:01 407219     /lib/libacl.so.1.1.0
b76e2000-b76e4000 rw-p 00005000 08:01 407219     /lib/libacl.so.1.1.0
b76e4000-b76ee000 r-xp 00000000 08:01 407345     /lib/libpam.so.0.81.12
b76ee000-b76ef000 r--p 00009000 08:01 407345     /lib/libpam.so.0.81.12
b76ef000-b76f0000 rw-p 0000a000 08:01 407345     /lib/libpam.so.0.81.12
b76f0000-b76f1000 rw-p b76f0000 00:00 0 
b76f1000-b76fa000 r-xp 00000000 08:01 407225     /lib/tls/i686/cmov/libcrypt-2.8.90.so
b76fa000-b76fb000 r--p 00008000 08:01 407225     /lib/tls/i686/cmov/libcrypt-2.8.90.so
b76fb000-b76fc000 rw-p 00009000 08:01 407225     /lib/tls/i686/cmov/libcrypt-2.8.90.so
b76fc000-b7723000 rw-p b76fc000 00:00 0 
b7723000-b7747000 r-xp 00000000 08:01 407227     /lib/tls/i686/cmov/libm-2.8.90.so
b7747000-b7748000 r--p 00023000 08:01 407227     /lib/tls/i686/cmov/libm-2.8.90.so
b7748000-b7749000 rw-p 00024000 08:01 407227     /lib/tls/i686/cmov/libm-2.8.90.so
b7749000-b775e000 r-xp 00000000 08:01 407237     /lib/tls/i686/cmov/libpthread-2.8.90.so
b775e000-b775f000 r--p 00014000 08:01 407237     /lib/tls/i686/cmov/libpthread-2.8.90.so
b775f000-b7760000 rw-p 00015000 08:01 407237     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7760000-b7762000 rw-p b7760000 00:00 0 
b7762000-b7776000 r-xp 00000000 08:01 352205     /usr/lib/libz.so.1.2.3.3
b7776000-b7778000 rw-p 00013000 08:01 352205     /usr/lib/libz.so.1.2.3.3
b7778000-b780f000 r-xp 00000000 08:01 351965     /usr/lib/libgnutls.so.26.4.5
b780f000-b7814000 r--p 00097000 08:01 351965     /usr/lib/libgnutls.so.26.4.5
b7814000-b7815000 rw-p 0009c000 08:01 351965     /usr/lib/libgnutls.so.26.4.5
b7815000-b7848000 r-xp 00000000 08:01 351953     /usr/lib/libcups.so.2
b7848000-b7849000 ---p 00033000 08:01 351953     /usr/lib/libcups.so.2
b7849000-b784a000 r--p 00033000 08:01 351953     /usr/lib/libcups.so.2
b784a000-b784b000 rw-p 00034000 08:01 351953     /usr/lib/libcups.so.2
b784b000-b784c000 rw-p b784b000 00:00 0 
b784c000-b784e000 r-xp 00000000 08:01 407209     /lib/libcom_err.so.2.1
b784e000-b784f000 r--p 00001000 08:01 407209     /lib/libcom_err.so.2.1
b784f000-b7850000 rw-p 00002000 08:01 407209     /lib/libcom_err.so.2.1
b7850000-b7872000 r-xp 00000000 08:01 353369     /usr/lib/libk5crypto.so.3.1
b7872000-b7873000 r--p 00022000 08:01 353369     /usr/lib/libk5crypto.so.3.1
b7873000-b7874000 rw-p 00023000 08:01 353369     /usr/lib/libk5crypto.so.3.1
b7874000-b7903000 r-xp 00000000 08:01 353371     /usr/lib/libkrb5.so.3.3
b7903000-b7905000 r--p 0008e000 08:01 353371     /usr/lib/libkrb5.so.3.3
b7905000-b7906000 rw-p 00090000 08:01 353371     /usr/lib/libkrb5.so.3.3
b7906000-b792f000 r-xp 00000000 08:01 352488     /usr/lib/libgssapi_krb5.so.2.2
b792f000-b7930000 r--p 00028000 08:01 352488     /usr/lib/libgssapi_krb5.so.2.2
b7930000-b7931000 rw-p 00029000 08:01 352488     /usr/lib/libgssapi_krb5.so.2.2
b7931000-b793d000 r-xp 00000000 08:01 351976     /usr/lib/liblber-2.4.so.2.1.0
b793d000-b793e000 r--p 0000b000 08:01 351976     /usr/lib/liblber-2.4.so.2.1.0
b793e000-b793f000 rw-p 0000c000 08:01 351976     /usr/lib/liblber-2.4.so.2.1.0
b793f000-b797e000 r-xp 00000000 08:01 351977     /usr/lib/libldap_r-2.4.so.2.1.0
b797e000-b797f000 r--p 0003e000 08:01 351977     /usr/lib/libldap_r-2.4.so.2.1.0
b797f000-b7980000 rw-p 0003f000 08:01 351977     /usr/lib/libldap_r-2.4.so.2.1.0
b7980000-b7982000 rw-p b7980000 00:00 0 
b7982000-b7983000 rw-s 00000000 00:12 14479      /var/run/samba/messages.tdb
b7983000-b7985000 r-xp 00000000 08:01 355327     /usr/lib/gconv/UTF-16.so
b7985000-b7986000 r--p 00001000 08:01 355327     /usr/lib/gconv/UTF-16.so
b7986000-b7987000 rw-p 00002000 08:01 355327     /usr/lib/gconv/UTF-16.so
b7987000-b798e000 r--s 00000000 08:01 351134     /usr/lib/gconv/gconv-modules.cache
b798e000-b798f000 rw-p b798e000 00:00 0 
b798f000-b79a9000 r-xp 00000000 08:01 408595     /lib/ld-2.8.90.so
b79a9000-b79aa000 r-xp b79a9000 00:00 0          [vdso]
b79aa000-b79ab000 r--p 0001a000 08:01 408595     /lib/ld-2.8.90.so
b79ab000-b79ac000 rw-p 0001b000 08:01 408595     /lib/ld-2.8.90.so
b79ac000-b7f27000 r-xp 00000000 08:01 354050     /usr/sbin/smbd
b7f27000-b7f30000 r--p 0057a000 08:01 354050     /usr/sbin/smbd
b7f30000-b7f38000 rw-p 00583000 08:01 354050     /usr/sbin/smbd
b7f38000-b7f3a000 rw-p b7f38000 00:00 0 
b9ae4000-b9bae000 rw-p b9ae4000 00:00 0          [heap]
bf9bb000-bf9d0000 rw-p bffeb000 00:00 0          [stack]

---

