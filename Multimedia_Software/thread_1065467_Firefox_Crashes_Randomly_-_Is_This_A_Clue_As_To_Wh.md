---
title: "Firefox Crashes Randomly - Is This A Clue As To Why It Crashes?"
date: 2009-02-09
forum: Multimedia Software
---

### Post by umechanism on 2009-02-09
So Firefox 3.0X crashes.  This is nothing new to this forum.  There is a bug in flash or something that causes mine to crash randomly.  Youtube - forget it.  Crashes every time.  So, I decided to run Firefox from the termimal using "sudo firefox".  It launched, I surfed, it crashed.  But this time, there is some information to be found.  Look at the last line of the hash I collected from the terminal output.  

I'm no Linux expert but perhaps this is useful to someone as to why Firefox is crashing.

[B]Firefox 3.05
Ubuntu 8.10
flashplugin-nonfree[/B]


> michael@ubuntu-dell:~$ sudo firefox
[sudo] password for michael: 
*** glibc detected *** /usr/lib/firefox-3.0.5/firefox: double free or corruption (fasttop): 0xb25011f0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e7d3f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7e7f456]
/usr/lib/libtalloc.so.1(talloc_free+0x153)[0xb5879503]
/lib/libnss_wins.so.2[0xb5aa1289]
/usr/lib/libtalloc.so.1(talloc_free+0x271)[0xb5879621]
/lib/libnss_wins.so.2(alloc_sub_basic+0xa87)[0xb5acc7a8]
/lib/libnss_wins.so.2(talloc_sub_basic+0x33)[0xb5accd8f]
/lib/libnss_wins.so.2[0xb5a0c281]
/lib/libnss_wins.so.2(lp_lockdir+0x27)[0xb5a0d3f2]
/lib/libnss_wins.so.2(lock_path+0x17)[0xb5ac6ac5]
/lib/libnss_wins.so.2(receive_unexpected+0x21)[0xb5a65767]
/lib/libnss_wins.so.2(receive_nmb_packet+0x65)[0xb5a68375]
/lib/libnss_wins.so.2(name_query+0x32e)[0xb5a6ae4d]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x38a)[0xb5a08555]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x4f)[0xb5a08853]
/lib/tls/i686/cmov/libc.so.6[0xb7ed3666]
/lib/tls/i686/cmov/libc.so.6(getaddrinfo+0x1c9)[0xb7ed5039]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0x129)[0xb7d4a6b9]
/usr/lib/xulrunner-1.9.0.5/libxul.so[0xb732aa60]
/usr/lib/libnspr4.so.0d[0xb7d581e1]
/lib/tls/i686/cmov/libpthread.so.0[0xb809a50f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7eef7ee]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:05 6464247    /usr/lib/firefox-3.0.5/firefox
0804f000-08050000 r--p 00006000 08:05 6464247    /usr/lib/firefox-3.0.5/firefox
08050000-08051000 rw-p 00007000 08:05 6464247    /usr/lib/firefox-3.0.5/firefox
08311000-09065000 rw-p 08311000 00:00 0          [heap]
a91fd000-a91fe000 ---p a91fd000 00:00 0 
a91fe000-a99fe000 rwxp a91fe000 00:00 0 
a99fe000-a99ff000 ---p a99fe000 00:00 0 
a99ff000-aa1ff000 rwxp a99ff000 00:00 0 
aaa00000-aaaf2000 rw-p aaa00000 00:00 0 
aaaf2000-aab00000 ---p aaaf2000 00:00 0 
aab00000-aabf2000 rw-p aab00000 00:00 0 
aabf2000-aac00000 ---p aabf2000 00:00 0 
aac00000-aacfd000 rw-p aac00000 00:00 0 
aacfd000-aad00000 ---p aacfd000 00:00 0 
aad00000-aade5000 rw-p aad00000 00:00 0 
aade5000-aae00000 ---p aade5000 00:00 0 
aae00000-aaefd000 rw-p aae00000 00:00 0 
aaefd000-aaf00000 ---p aaefd000 00:00 0 
aaf00000-aafe1000 rw-p aaf00000 00:00 0 
aafe1000-ab000000 ---p aafe1000 00:00 0 
ab000000-ab0fd000 rw-p ab000000 00:00 0 
ab0fd000-ab100000 ---p ab0fd000 00:00 0 
ab100000-ab1dd000 rw-p ab100000 00:00 0 
ab1dd000-ab200000 ---p ab1dd000 00:00 0 
ab200000-ab2fd000 rw-p ab200000 00:00 0 
ab2fd000-ab300000 ---p ab2fd000 00:00 0 
ab300000-ab3d9000 rw-p ab300000 00:00 0 
ab3d9000-ab400000 ---p ab3d9000 00:00 0 
ab400000-ab4e8000 rw-p ab400000 00:00 0 
ab4e8000-ab500000 ---p ab4e8000 00:00 0 
ab500000-ab5d5000 rw-p ab500000 00:00 0 
ab5d5000-ab600000 ---p ab5d5000 00:00 0 
ab600000-ab6cf000 rw-p ab600000 00:00 0 
ab6cf000-ab700000 ---p ab6cf000 00:00 0 
ab700000-ab7e7000 rw-p ab700000 00:00 0 
ab7e7000-ab800000 ---p ab7e7000 00:00 0 
ab800000-ab8c5000 rw-p ab800000 00:00 0 
ab8c5000-ab900000 ---p ab8c5000 00:00 0 
ab900000-ab9e3000 rw-p ab900000 00:00 0 
ab9e3000-aba00000 ---p ab9e3000 00:00 0 
aba00000-abada000 rw-p aba00000 00:00 0 
abada000-abb00000 ---p abada000 00:00 0 
abb00000-abbdf000 rw-p abb00000 00:00 0 
abbdf000-abc00000 ---p abbdf000 00:00 0 
abc00000-abce9000 rw-p abc00000 00:00 0 
abce9000-abd00000 ---p abce9000 00:00 0 
abd00000-abdf4000 rw-p abd00000 00:00 0 
abdf4000-abe00000 ---p abdf4000 00:00 0 
abe00000-abef8000 rw-p abe00000 00:00 0 
abef8000-abf00000 ---p abef8000 00:00 0 
abf00000-abfe3000 rw-p abf00000 00:00 0 
abfe3000-ac000000 ---p abfe3000 00:00 0 
ac000000-ac0f3000 rw-p ac000000 00:00 0 
ac0f3000-ac100000 ---p ac0f3000 00:00 0 
ac120000-ac1b1000 rw-p ac120000 00:00 0 
ac1b1000-ac2e3000 r-xp 00000000 08:05 6308276    /usr/lib/i686/cmov/libcrypto.so.0.9.8
ac2e3000-ac2e4000 ---p 00132000 08:05 6308276    /usr/lib/i686/cmov/libcrypto.so.0.9.8
ac2e4000-ac2ec000 r--p 00132000 08:05 6308276    /usr/lib/i686/cmov/libcrypto.so.0.9.8
ac2ec000-ac2f9000 rw-p 0013a000 08:05 6308276    /usr/lib/i686/cmov/libcrypto.so.0.9.8
ac2f9000-ac2fd000 rw-p ac2f9000 00:00 0 
acafe000-acaff000 ---p acafe000 00:00 0 
acaff000-ad2ff000 rwxp acaff000 00:00 0 
adb00000-adbfd000 rw-p adb00000 00:00 0 
adbfd000-adc00000 ---p adbfd000 00:00 0 
adc00000-adcfb000 rw-p adc00000 00:00 0 
adcfb000-add00000 ---p adcfb000 00:00 0 
add00000-adef3000 rw-p add00000 00:00 0 
adef3000-adf00000 ---p adef3000 00:00 0 
adf00000-adfff000 rw-p adf00000 00:00 0 
adfff000-ae000000 ---p adfff000 00:00 0 
ae000000-ae1cb000 rw-p ae000000 00:00 0 
ae1cb000-ae200000 ---p ae1cb000 00:00 0 
ae200000-ae3fd000 rw-p ae200000 00:00 0 
ae3fd000-ae400000 ---p ae3fd000 00:00 0 
ae400000-ae5fe000 rw-p ae400000 00:00 0 
ae5fe000-ae600000 ---p ae5fe000 00:00 0 
ae600000-ae6ff000 rw-p ae600000 00:00 0 
ae6ff000-ae700000 ---p ae6ff000 00:00 0 
ae700000-ae800000 rw-p ae700000 00:00 0 
ae800000-ae8e5000 rw-p ae800000 00:00 0 
ae8e5000-ae900000 ---p ae8e5000 00:00 0 
ae900000-aea00000 rw-p ae900000 00:00 0 
aea00000-aeb00000 rw-p aea00000 00:00 0 
aeb00000-aec00000 rw-p aeb00000 00:00 0 
aec66000-aec7f000 r--s 00000000 08:05 6382285    /usr/share/mime/mime.cache
aed00000-aeefe000 rw-p aed00000 00:00 0 
aeefe000-aef00000 ---p aeefe000 00:00 0 
aef00000-af000000 rw-p aef00000 00:00 0 
af018000-af05a000 r-xp 00000000 08:05 6308857    /usr/lib/i686/cmov/libssl.so.0.9.8
af05a000-af05b000 r--p 00041000 08:05 6308857    /usr/lib/i686/cmov/libssl.so.0.9.8
af05b000-af05e000 rw-p 00042000 08:05 6308857    /usr/lib/i686/cmov/libssl.so.0.9.8
af05e000-af08e000 r-xp 00000000 08:05 6286477    /usr/lib/libidn.so.11.5.37
af08e000-af08f000 r--p 00030000 08:05 6286477    /usr/lib/libidn.so.11.5.37
af08f000-af090000 rw-p 00031000 08:05 6286477    /usr/lib/libidn.so.11.5.37
af090000-b0090000 rw-p af090000 00:00 0 
b0090000-b09e2000 r-xp 00000000 08:05 6291458    /usr/lib/flashplugin-nonfree/libflashplayer.so
b09e2000-b0a16000 rw-p 00951000 08:05 6291458    /usr/lib/flashplugin-nonfree/libflashplayer.so
b0a16000-b0b00000 rw-p b0a16000 00:00 0 
b0b00000-b0bff000 rw-p b0b00000 00:00 0 
b0bff000-b0c00000 ---p b0bff000 00:00 0 
b0c00000-b0cff000 rw-p b0c00000 00:00 0 
b0cff000-b0d00000 ---p b0cff000 00:00 0 
b0d04000-b0d40000 r-xp 00000000 08:05 6286094    /usr/lib/libcurl.so.4.1.0
b0d40000-b0d41000 r--p 0003c000 08:05 6286094    /usr/lib/libcurl.so.4.1.0
b0d41000-b0d42000 rw-p 0003d000 08:05 6286094    /usr/lib/libcurl.so.4.1.0
b0d42000-b0d6f000 r-xp 00000000 08:05 6734363    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/libjavaplugin_nscp.so
b0d6f000-b0d75000 rw-p 0002d000 08:05 6734363    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/libjavaplugin_nscp.so
b0d75000-b0d8b000 r-xp 00000000 08:05 6734515    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/plugin/i386/ns7/libjavaplugin_oji.so
b0d8b000-b0d8f000 rw-p 00015000 08:05 6734515    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/plugin/i386/ns7/libjavaplugin_oji.so
b0d8f000-b0da3000 r-xp 00000000 08:05 6324919    /usr/lib/mozilla/plugins/gecko-mediaplayer.so
b0da3000-b0da4000 r--p 00013000 08:05 6324919    /usr/lib/mozilla/plugins/gecko-mediaplayer.so
b0da4000-b0da5000 rw-p 00014000 08:05 6324919    /usr/lib/mozilla/plugins/gecko-mediaplayer.so
b0da5000-b0db8000 r-xp 00000000 08:05 6325297    /usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so
b0db8000-b0db9000 r--p 00013000 08:05 6325297    /usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so
b0db9000-b0dba000 rw-p 00014000 08:05 6325297    /usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so
b0dba000-b0e00000 r--p 00000000 08:05 11223150   /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b0e00000-b0eff000 rw-p b0e00000 00:00 0 
b0eff000-b0f00000 ---p b0eff000 00:00 0 
b0f12000-b0f25000 r-xp 00000000 08:05 6325300    /usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so
b0f25000-b0f26000 r--p 00013000 08:05 6325300    /usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so
b0f26000-b0f27000 rw-p 00014000 08:05 6325300    /usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so
b0f27000-b0f6b000 r--p 00000000 08:05 11223152   /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b0f6b000-b0f72000 r-xp 00000000 08:05 6286174    /usr/lib/libfam.so.0.0.0
b0f72000-b0f73000 rw-p 00006000 08:05 6286174    /usr/lib/libfam.so.0.0.0
b0f73000-b0f79000 r-xp 00000000 08:05 4857881    /lib/libacl.so.1.1.0
b0f79000-b0f7b000 rw-p 00005000 08:05 4857881    /lib/libacl.so.1.1.0
**b0f7b000-b0f87000 r-xp 00000000 08:05 6309284    /usr/lib/gnome-vfs-2.0/modulAborted**
michael@ubuntu-dell:~$ 



---

