---
title: "Myth frontend crash when trying to display recordings after watching a recording"
date: 2008-01-18
forum: Mythbuntu
---

### Post by ian dobson on 2008-01-18
I'm running the backend and frontend on 2 seperate PC's over a 100mb network connection.

I can connect to the backend from the frontend without any problems. 
But after watching a recorded program the frontend sometimes crashes when I stop playing the recording and it tries to display the list of available recorded programs.

It just displays "select program" or what ever the text is in English (I', running the Mythfrontend in German) for about 4 seconds without showing any programs, then just crashes out to the desktop.

If I just restart Mythfrontend everything works again until I repeat the process above. Note the frontend crashes if I exit the watch recording using the Stop button on my remote or if just let the recording end normally.

I've checked my network connection and it's 100% ok. 
I can't see anything strange in my Backend log.
I don't appear to have a frontend log!

It looks to me as if the frontend it trying to make contact with the SQL server on the backend and for some reason it can't and just dies.

Edit: If I watch a recording for only afew minutes and exit back to the recording list the frontend doesn't crash. But if I watch a 2 hour film it crashes about 50% of the time.

Currently running Mythbuntu 7.10 on the frontend with all the lastest updates as of 17.1.2008 and Gutsy 7.10 on the backend also with all the lastest updates as of 17.1.2008.

Anyone got any ideas what the problem could be? Solution maybe?

Edit 2: I'm running 64Bit ubuntu on the backend. 32bit on the frontend and a Nvidia G7300 graphic card with the Nvidia drivers (not open source) on the frontend.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-01-19
Ok I've just been able to reproduce the crash, with logging enabled. 
Here's the mythfrontend.log:-

stream: start_time: 0.276 duration: 8603.755 bitrate=1866 kb/s
2008-01-19 08:40:53.763 AFD: Opened codec 0x8428ad0, id(MPEG2VIDEO_XVMC) type(Video)
2008-01-19 08:40:53.763 AFD: Opened codec 0x869bca0, id(MP2) type(Audio)
2008-01-19 08:40:53.771 Opening ALSA audio device 'default'.
2008-01-19 08:40:53.823 Mixer unable to find control Master
2008-01-19 08:40:53.823 Mixer unable to find control Master
2008-01-19 08:40:54.066 VideoOutputXv: XvMCTex: Init failed
2008-01-19 08:40:54.066 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x196
2008-01-19 08:40:54.339 Realtime priority would require SUID as root.
2008-01-19 08:40:54.339 TV: Changing from None to WatchingPreRecorded
2008-01-19 08:40:54.465 Video timing method: SGI OpenGL
2008-01-19 08:41:03.341 TV: Attempting to change from WatchingPreRecorded to None
2008-01-19 08:41:03.502 TV: Changing from WatchingPreRecorded to None
2008-01-19 08:41:03.572 DPMS Reactivated.
*** glibc detected *** /usr/bin/mythfrontend.real: free(): invalid pointer: 0xb4278727 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb5a5fd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb5a63800]
/usr/lib/libqt-mt.so.3(_ZN7QGArrayD2Ev+0x6f)[0xb64d5061]
/usr/lib/libmythtv-0.20.2.so.0(_ZN9QMemArrayIcED1Ev+0x26)[0xb77a8356]
/usr/lib/libqt-mt.so.3(_ZN11QDataStreamD1Ev+0x4d)[0xb64c9cdd]
/usr/lib/libqt-mt.so.3(_ZNK11QTranslator11findMessageEPKcS1_S1_+0x520)[0xb61cb80c]
/usr/lib/libqt-mt.so.3(_ZNK12QApplication9translateEPKcS1_S1_NS_8EncodingE+0xb8)[0xb617928c]
/usr/lib/libqt-mt.so.3(_ZN7QObject2trEPKcS1_+0x55)[0xb656b6f1]
/usr/lib/libmythtv-0.20.2.so.0(_ZNK11ProgramInfo5ToMapER4QMapI7QStringS1_Eb+0x1568)[0xb7674b38]
[0xaf63b4a8]
======= Memory map: ========
08048000-0817e000 r-xp 00000000 08:01 13002      /usr/bin/mythfrontend.real
0817e000-08197000 rw-p 00135000 08:01 13002      /usr/bin/mythfrontend.real
08197000-0b47f000 rw-p 08197000 00:00 0          [heap]
ab300000-ab3ec000 rw-p ab300000 00:00 0
ab3ec000-ab400000 ---p ab3ec000 00:00 0
ab5bd000-ab5be000 rw-s e8c04000 00:0e 15701      /dev/nvidia0
ab700000-ab7e4000 rw-p ab700000 00:00 0
ab7e4000-ab800000 ---p ab7e4000 00:00 0
ad8d0000-ad8d1000 ---p ad8d0000 00:00 0
ad8d1000-ae0d1000 rwxp ad8d1000 00:00 0
ae5fe000-ae5ff000 ---p ae5fe000 00:00 0
ae5ff000-aedff000 rwxp ae5ff000 00:00 0
aedff000-aee00000 ---p aedff000 00:00 0
aee00000-af600000 rwxp aee00000 00:00 0
af600000-af700000 rw-p af600000 00:00 0
af706000-af725000 r-xp 00000000 08:01 13056      /usr/lib/libXvMCNVIDIA.so.100.14.19
af725000-af726000 rw-p 0001f000 08:01 13056      /usr/lib/libXvMCNVIDIA.so.100.14.19
af72f000-af731000 r-xp 00000000 08:01 13022      /usr/lib/mythtv/filters/libquickdnr.so
af731000-af732000 rw-p 00001000 08:01 13022      /usr/lib/mythtv/filters/libquickdnr.so
af732000-af733000 r-xp 00000000 08:01 13033      /usr/lib/mythtv/filters/libonefield.so
af733000-af734000 rw-p 00000000 08:01 13033      /usr/lib/mythtv/filters/libonefield.so
af734000-af735000 r-xp 00000000 08:01 13019      /usr/lib/mythtv/filters/liblinearblend.so
af735000-af736000 rw-p 00000000 08:01 13019      /usr/lib/mythtv/filters/liblinearblend.so
af736000-af738000 r-xp 00000000 08:01 13023      /usr/lib/mythtv/filters/libkerneldeint.so
af738000-af739000 rw-p 00001000 08:01 13023      /usr/lib/mythtv/filters/libkerneldeint.so
af739000-af73d000 r-xp 00000000 08:01 13035      /usr/lib/mythtv/filters/libivtc.so
af73d000-af73e000 rw-p 00003000 08:01 13035      /usr/lib/mythtv/filters/libivtc.so
af73e000-af73f000 r-xp 00000000 08:01 13017      /usr/lib/mythtv/filters/libinvert.so
af73f000-af740000 rw-p 00000000 08:01 13017      /usr/lib/mythtv/filters/libinvert.so
af740000-af741000 r-xp 00000000 08:01 13027      /usr/lib/mythtv/filters/libforce.so
af741000-af742000 rw-p 00000000 08:01 13027      /usr/lib/mythtv/filters/libforce.so
af742000-af744000 r-xp 00000000 08:01 13020      /usr/lib/mythtv/filters/libdenoise3d.so
af744000-af745000 rw-p 00001000 08:01 13020      /usr/lib/mythtv/filters/libdenoise3d.so
af745000-af746000 r-xp 00000000 08:01 13031      /usr/lib/mythtv/filters/libadjust.so
af746000-af747000 rw-p 00001000 08:01 13031      /usr/lib/mythtv/filters/libadjust.so
af747000-af748000 ---p af747000 00:00 0
af748000-aff48000 rwxp af748000 00:00 0
aff48000-b0148000 rw-s 0deae000 00:0e 15701      /dev/nvidia0
b0148000-b0449000 rw-p b0148000 00:00 0
b0449000-b0468000 r--p 00000000 08:01 33076      /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf
b0b22000-b0b9d000 rw-p b0b22000 00:00 0
b1726000-b1745000 r--p 00000000 08:01 33075      /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
b1764000-b1765000 rw-s e8c04000 00:0e 15701      /dev/nvidia0
b2257000-b2265000 r-xp 00000000 08:01 14010      /usr/lib/libdirect-0.9.so.25.0.0
b2265000-b2266000 rw-p 0000e000 08:01 14010      /usr/lib/libdirect-0.9.so.25.0.0
b2266000-b226b000 r-xp 00000000 08:01 14081      /usr/lib/libfusion-0.9.so.25.0.0
b226b000-b226c000 rw-p 00004000 08:01 14081      /usr/lib/libfusion-0.9.so.25.0.0
b226c000-b22c1000 r-xp 00000000 08:01 14012      /usr/lib/libdirectfb-0.9.so.25.0.0
b22c1000-b22c3000 rw-p 00055000 08:01 14012      /usr/lib/libdirectfb-0.9.so.25.0.0
b22c3000-b22d0000 r-xp 00000000 08:01 13975      /usr/lib/libcdda_interface.so.0.10.0
b22d0000-b22d1000 rw-p 0000d000 08:01 13975      /usr/lib/libcdda_interface.so.0.10.0
b22d1000-b22d8000 r-xp 00000000 08:01 13977      /usr/lib/libcdda_paranoia.so.0.10.0
b22d8000-b22d9000 rw-p 00006000 08:01 13977      /usr/lib/libcdda_paranoia.so.0.10.0
b22d9000-b231e000 r-xp 00000000 08:01 13985      /usr/lib/libFLAC.so.8.0.1
b231e000-b231f000 rw-p 00045000 08:01 13985      /usr/lib/libFLAC.so.8.0.1
b231f000-b232f000 r-xp 00000000 08:01 13973      /usr/lib/libcdaudio.so.1.0.0
b232f000-b2330000 rw-p 0000f000 08:01 13973      /usr/lib/libcdaudio.so.1.0.0
b2330000-b233b000 r-xp 00000000 08:01 14549      /usr/lib/libvorbisenc.so.2.0.3
b233b000-b2429000 rw-p 0000b000 08:01 14549      /usr/lib/libvorbisenc.so.2.0.3
b2429000-b2443000 r-xp 00000000 08:01 14547      /usr/lib/libvorbis.so.0.4.0
b2443000-b2451000 rw-p 0001a000 08:01 14547      /usr/lib/libvorbis.so.0.4.0
b2451000-b2458000 r-xp 00000000 08:01 14551      /usr/lib/libvorbisfile.so.3.2.0
b2458000-b2459000 rw-p 00006000 08:01 14551      /usr/lib/libvorbisfile.so.3.2.0
b2459000-b245d000 r-xp 00000000 08:01 14416      /usr/lib/libogg.so.0.5.3
b245d000-b245e000 rw-p 00003000 08:01 14416      /usr/lib/libogg.so.0.5.3
b245e000-b246c000 r-xp 00000000 08:01 14183      /usr/lib/libid3tag.so.0.3.0
b246c000-b246e000 rw-p 0000d000 08:01 14183      /usr/lib/libid3tag.so.0.3.0
b246e000-b25e7000 r-xp 00000000 08:01 16023      /usr/lib/mythtv/plugins/libmythmusic.so
b25e7000-b25f6000 rw-p 00179000 08:01 16023      /usr/lib/mythtv/plugins/libmythmusic.so
b25f6000-b2938000 rw-p b25f6000 00:00 0
b2939000-b294e000 r-xp 00000000 08:01 14332      /usr/lib/libmad.so.0.2.1
b294e000-b294f000 rw-p 00014000 08:01 14332      /usr/lib/libmad.so.0.2.1
b294f000-b2957000 r-xp 00000000 08:01 14355      /usr/lib/libmp4ff.so.0.0.0
b2957000-b2958000 rw-p 00008000 08:01 14355      /usr/lib/libmp4ff.so.0.0.0
b2958000-b299d000 r-xp 00000000 08:01 14054      /usr/lib/libfaad.so.0.0.0
b299d000-b29a0000 rw-p 00045000 08:01 14054      /usr/lib/libfaad.so.0.0.0
b29a0000-b2a05000 r-xp 00000000 08:01 13831      /usr/lib/libSDL-1.2.so.0.11.0
b2a05000-b2a07000 rw-p 00065000 08:01 13831      /usr/lib/libSDL-1.2.so.0.11.0
b2a07000-b2a2f000 rw-p b2a07000 00:00 0
b2a2f000-b2a59000 r-xp 00000000 08:01 14060      /usr/lib/libfftw.so.2.0.5
b2a59000-b2a5a000 rw-p 0002a000 08:01 14060      /usr/lib/libfftw.so.2.0.5
b2a5a000-b2a7f000 r-xp 00000000 08:01 14478      /usr/lib/librfftw.so.2.0.5
b2a7f000-b2a80000 rw-p 00025000 08:01 14478      /usr/lib/librfftw.so.2.0.5
b2a80000-b2a81000 rw-s 00000000 00:09 458764     /SYSV00000000 (deleted)
b2a81000-b2a82000 r-xp 00000000 08:01 13026      /usr/lib/mythtv/filters/libcrop.so
b2a82000-b2a83000 rw-p 00000000 08:01 13026      /usr/lib/mythtv/filters/libcrop.so
b2a83000-b2a89000 r--p 00000000 08:01 51372      /usr/share/mythtv/i18n/mythmusic_de.qm
b2a89000-b2b0c000 r-xp 00000000 08:01 16022      /usr/lib/mythtv/plugins/libmythgame.so
b2b0c000-b2b20000 rw-p 00082000 08:01 16022      /usr/lib/mythtv/plugins/libmythgame.so
b2b20000-b2b6a000 r-xp 00000000 08:01 16019      /usr/lib/mythtv/plugins/libmythdvd.so
b2b6a000-b2b72000 rw-p 00049000 08:01 16019      /usr/lib/mythtv/plugins/libmythdvd.so
b2b72000-b2ba2000 r-xp 00000000 08:01 16018      /usr/lib/mythtv/plugins/libmythcontrols.so
b2ba2000-b2ba5000 rw-p 0002f000 08:01 16018      /usr/lib/mythtv/plugins/libmythcontrols.so
b2ba5000-b2c31000 r-xp 00000000 08:01 16016      /usr/lib/mythtv/plugins/libmytharchive.so
b2c31000-b2c38000 rw-p 0008c000 08:01 16016      /usr/lib/mythtv/plugins/libmytharchive.so
b2c38000-b2cc3000 r--p 00000000 08:01 33128      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b2cc3000-b2ccb000 r-xp 00000000 08:01 7639       /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b2ccb000-b2ccd000 rw-p 00007000 08:01 7639       /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b2ccd000-b2cd4000 r-xp 00000000 08:01 7631       /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b2cd4000-b2cd6000 rw-p 00006000 08:01 7631       /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b2cd6000-b2cd7000 r-xp 00000000 08:01 13029      /usr/lib/mythtv/filters/libconvert.so
b2cd7000-b2cd8000 rw-p 00000000 08:01 13029      /usr/lib/mythtv/filters/libconvert.so
b2cd8000-b2cd9000 r-xp 00000000 08:01 13034      /usr/lib/mythtv/filters/libbobdeint.so
b2cd9000-b2cda000 rw-p 00000000 08:01 13034      /usr/lib/mythtv/filters/libbobdeint.so
b2cda000-b2cdc000 r--p 00000000 08:01 51359      /usr/share/mythtv/i18n/mythgame_de.qm
b2cdc000-b2cdf000 r--p 00000000 08:01 51300      /usr/share/mythtv/i18n/mythdvd_de.qm
b2cdf000-b2d25000 r--p 00000000 08:01 33057      /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b2d25000-b2d26000 ---p b2d25000 00:00 0
b2d26000-b3526000 rwxp b2d26000 00:00 0
b3526000-b3527000 ---p b3526000 00:00 0
b3527000-b3d27000 rwxp b3527000 00:00 0
b3d27000-b3d28000 rw-s 00000000 00:09 229382     /SYSV00000000 (deleted)
b3d28000-b3d29000 rw-s 00000000 00:09 196613     /SYSV00000000 (deleted)
b3d29000-b3d69000 rw-s e7bb2000 00:0e 15701      /dev/nvidia0
b3d69000-b3e69000 rw-s 10cea000 00:0e 15701      /dev/nvidia0
b3e69000-b3fab000 rw-s 1106f000 00:0e 15701      /dev/nvidia0
b3fab000-b4006000 rw-p 00000000 00:0e 2648       /dev/zero
b4006000-b4007000 r--p 00000000 08:01 51290      /usr/share/mythtv/i18n/mythcontrols_de.qm
b4007000-b4187000 rw-s e0000000 00:0e 15701      /dev/nvidia0
b4187000-b41a5000 rw-s 00000000 00:09 0          /SYSV00000000 (deleted)
b41a5000-b41d2000 r-xp 00000000 08:01 14313      /usr/lib/liblcms.so.1.0.16
b41d2000-b41d4000 rw-p 0002c000 08:01 14313      /usr/lib/liblcms.so.1.0.16
b41d4000-b41d6000 rw-p b41d4000 00:00 0
b41d6000-b4241000 r-xp 00000000 08:01 14349      /usr/lib/libmng.so.1.1.0.9
b4241000-b4244000 rw-p 0006a000 08:01 14349      /usr/lib/libmng.so.1.1.0.9
b4244000-b4247000 r--p 00000000 08:01 51270      /usr/share/mythtv/i18n/mytharchive_de.qm
b4247000-b424b000 rw-s 10ce5000 00:0e 15701      /dev/nvidia0
b424b000-b424c000 rw-s e7bf3000 00:0e 15701      /dev/nvidia0
b424c000-b424d000 rw-s 10ce3000 00:0e 15701      /dev/nvidia0
b424d000-b4279000 r--p 00000000 08:01 50348      /usr/share/mythtv/i18n/mythfrontend_de.qm
b4279000-b427a000 ---p b4279000 00:00 0
b427a000-b4a7a000 rwxp b427a000 00:00 0
b4a7a000-b4abe000 r--p 00000000 08:01 33055      /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b4abe000-b4ac7000 r-xp 00000000 08:01 7635       /lib/tls/i686/cmov/libnss_files-2.6.1.so
b4ac7000-b4ac9000 rw-p 00008000 08:01 7635       /lib/tls/i686/cmov/libnss_files-2.6.1.so
b4ac9000-b4add000 r-xp 00000000 08:01 7626       /lib/tls/i686/cmov/libnsl-2.6.1.so
b4add000-b4adf000 rw-p 00013000 08:01 7626       /lib/tls/i686/cmov/libnsl-2.6.1.so
b4adf000-b4ae1000 rw-p b4adf000 00:00 0
b4ae1000-b4ae6000 r-xp 00000000 08:01 7595       /lib/tls/i686/cmov/libcrypt-2.6.1.so
b4ae6000-b4ae8000 rw-p 00004000 08:01 7595       /lib/tls/i686/cmov/libcrypt-2.6.1.so
b4ae8000-b4b0f000 rw-p b4ae8000 00:00 0
b4b0f000-b4cb4000 r-xp 00000000 08:01 14142      /usr/lib/libmysqlclient.so.15.0.0
b4cb4000-b4cf8000 rw-p 001a4000 08:01 14142      /usr/lib/libmysqlclient.so.15.0.0
b4cf8000-b4cf9000 rw-p b4cf8000 00:00 0
b4cf9000-b4cfa000 rw-s 10ce2000 00:0e 15701      /dev/nvidia0
b4cfa000-b4cfb000 rw-s e8001000 00:0e 15701      /dev/nvidia0
b4cfb000-b4cfc000 rw-s e8c02000 00:0e 15701      /dev/nvidia0
b4cfc000-b4d01000 r-xp 00000000 08:01 21426      /usr/lib/qt3/plugins/imageformats/libqmng.so
b4d01000-b4d02000 rw-p 00004000 08:01 21426      /usr/lib/qt3/plugins/imageformats/libqmng.so
b4d02000-b4d0f000 r-xp 00000000 08:01 19578      /usr/lib/qt3/plugins/sqldrivers/libqsqlmysql.so
b4d0f000-b4d10000 rw-p 0000c000 08:01 19578      /usr/lib/qt3/plugins/sqldrivers/libqsqlmysql.so
b4d10000-b4d11000 rw-p b4d10000 00:00 0
b4d11000-b4d17000 r--s 00000000 08:01 115        /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4d17000-b4d1d000 r--s 00000000 08:01 110        /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4d1d000-b4d1f000 r--s 00000000 08:01 124        /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4d1f000-b4d36000 r--s 00000000 08:01 563        /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4d36000-b4d3c000 r--s 00000000 08:01 122        /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4d3c000-b4d43000 r--s 00000000 08:01 468        /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4d43000-b4d44000 r--s 00000000 08:01 120        /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b4d44000-b4d46000 r--s 00000000 08:01 119        /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4d46000-b4d49000 r--s 00000000 08:01 117        /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4d49000-b4d4d000 r--s 00000000 08:01 126        /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4d4d000-b4d4e000 r--s 00000000 08:01 103        /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4d4e000-b4d51000 r--s 00000000 08:01 113        /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4d51000-b4d52000 r--s 00000000 08:01 112        /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b4d52000-b4d54000 r--s 00000000 08:01 105        /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b4d54000-b4d5a000 r--s 00000000 08:01 104        /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4d5a000-b4d60000 r--s 00000000 08:01 116        /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2

Maybe I should try and create a bug report.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-01-20
Hi,

Just gone over to the weekly builds, and exactly the same error.

Am I talking to myself here? Is anyone actually reading this.

Regards
Ian Dobson

---

### Post by Mrbbad on 2008-01-21
Sometimes I've noticed the backend likes to crash after I've left watching tv mode, done something else, and tried to come back to watch tv mode ...

So I think I sort-ish-kinda know what you're feeling (granted, I know your frontend is crashing, not backend).

What I did, since I've no idea why in the world the backend does this, is create a script that checks to see if the backend is running every 30 seconds and restart it if it is not ... at the very least I don't have to get up and mess with it to restart the backend.

Perhaps you can find an idea in that.  But ultimately, I don't know what's up with it making it do these things.

Good luck.

---

### Post by ian dobson on 2008-01-23
Hi,

I could use a script that restarts the frontend when it dies, but that's just fighting the symtom rather than "curing the problem".

I've started going through the MythTV bug list looking for anything that looks like my problem. But I've not found anything yet.

Regards
Ian Dobson

ps. I've not had any problems with my backend, it only crashed once on me but that was my fault (I was playing with the mysql database and screwed up afew settings).

---

### Post by ian dobson on 2008-01-23
OK,

I've finally been through the SVN bug list and found this :- [http://svn.mythtv.org/trac/ticket/4148](http://svn.mythtv.org/trac/ticket/4148). It looks as if the problem is solved, I just need to wait for the weekly compile to be updated.

If that doesn't happen then I'll try backporting the patch myself. It doesn't look like it's a major change as it shouldn't take all to long to implement.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-01-27
Bump.

The SVN patch doesn't look as if it's my problem.

Using Standard xV and the kernel Deinterlacer seems to have "improved" the problem. It only happens once in about 20-30 times.

OK. I've also optimized my MySql backend (More cache for the Query buffer).

Regards
Ian Dobson.

ps. How often are the weekly builds "built"? I've not seen an update for over a week now.

---

### Post by myth1914 on 2011-02-01
I know this is a very old post; however, In case anyone comes across this, I had this error on 10.10 myth .23   It turns out, I had the Nvidia driver/modaliases installed from a different video card.  Purged the Nvidia drivers (as I'm now using an ATI HD4350 HDMI) and SUCCESS.

---

