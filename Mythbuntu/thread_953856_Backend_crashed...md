---
title: "Backend crashed.."
date: 2008-10-20
forum: Mythbuntu
---

### Post by JugeHuge on 2008-10-20
Hello..

I'm using combined Frontend/Backend and updated it couple days ago.
Myth version is 0.21.20080304-1 18704
Today when i got home i found out that frontend couldn't connect to backend.

I dig out backend log and found this.

```
2008-10-20 13:43:44.632 Preview: Grabbed preview '/var/lib/mythtv/recordings/1009_20081020131100.mpg' 720x576@180s
2008-10-20 13:55:15.794 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 14:10:15.848 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 14:25:15.905 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 14:40:15.963 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 14:55:16.047 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 15:10:16.096 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 15:25:16.148 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 15:40:16.204 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 15:55:16.263 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 16:10:16.330 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 16:25:16.380 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-20 16:40:16.429 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
*** glibc detected *** /usr/bin/mythbackend: free(): invalid next size (fast): 0xab2e8468 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb5b9fa85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb5ba34f0]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb5d6ab11]
/usr/lib/libqt-mt.so.3(_ZN11QStringData10deleteSelfEv+0x2e)[0xb661d3ba]
/usr/lib/libqt-mt.so.3(_ZN15QDomNodePrivateD2Ev+0xb5)[0xb6574145]
/usr/lib/libqt-mt.so.3(_ZN15QDomAttrPrivateD0Ev+0x2b)[0xb65747cf]
/usr/lib/libqt-mt.so.3(_ZN23QDomNamedNodeMapPrivate8clearMapEv+0x7b)[0xb657b31d]
/usr/lib/libqt-mt.so.3(_ZN23QDomNamedNodeMapPrivateD1Ev+0x1d)[0xb657b379]
/usr/lib/libqt-mt.so.3(_ZN18QDomElementPrivateD0Ev+0x4c)[0xb657b3da]
/usr/lib/libqt-mt.so.3(_ZN15QDomNodePrivateD2Ev+0x5e)[0xb65740ee]
/usr/lib/libqt-mt.so.3(_ZN18QDomElementPrivateD0Ev+0x62)[0xb657b3f0]
/usr/lib/libqt-mt.so.3(_ZN15QDomNodePrivateD2Ev+0x5e)[0xb65740ee]
/usr/lib/libqt-mt.so.3(_ZN18QDomElementPrivateD0Ev+0x62)[0xb657b3f0]
/usr/lib/libqt-mt.so.3(_ZN15QDomNodePrivateD2Ev+0x5e)[0xb65740ee]
/usr/lib/libqt-mt.so.3(_ZN18QDomElementPrivateD0Ev+0x62)[0xb657b3f0]
/usr/lib/libqt-mt.so.3(_ZN15QDomNodePrivateD2Ev+0x5e)[0xb65740ee]
/usr/lib/libqt-mt.so.3(_ZN19QDomDocumentPrivateD0Ev+0x99)[0xb6574207]
/usr/lib/libqt-mt.so.3(_ZN8QDomNodeD2Ev+0x76)[0xb6573410]
/usr/lib/libqt-mt.so.3(_ZN12QDomDocumentD1Ev+0x2b)[0xb657349b]
/usr/bin/mythbackend[0x807d102]
======= Memory map: ========
08048000-08159000 r-xp 00000000 08:05 310700     /usr/bin/mythbackend
08159000-0815a000 rw-p 00111000 08:05 310700     /usr/bin/mythbackend
0815a000-083db000 rw-p 0815a000 00:00 0          [heap]
a649e000-a649f000 ---p a649e000 00:00 0 
a649f000-a6c9f000 rwxp a649f000 00:00 0 
a7dcf000-a7dd0000 ---p a7dcf000 00:00 0 
a7dd0000-a85d0000 rwxp a7dd0000 00:00 0 
a8afe000-a8aff000 ---p a8afe000 00:00 0 
a8aff000-a92ff000 rwxp a8aff000 00:00 0 
a9700000-a9800000 rw-p a9700000 00:00 0 
a9b02000-a9b03000 ---p a9b02000 00:00 0 
a9b03000-aa303000 rwxp a9b03000 00:00 0 
aa303000-aa304000 ---p aa303000 00:00 0 
aa304000-aab04000 rwxp aa304000 00:00 0 
aac00000-aac6d000 rw-p aac00000 00:00 0 
aac6d000-aad00000 ---p aac6d000 00:00 0 
aad7f000-aae68000 rw-p aad7f000 00:00 0 
aae68000-aaf00000 ---p aae68000 00:00 0 
ab005000-ab086000 rw-p ab005000 00:00 0 
ab200000-ab300000 rw-p ab200000 00:00 0 
ac339000-ac33a000 ---p ac339000 00:00 0 
ac33a000-acb3a000 rwxp ac33a000 00:00 0 
acb3a000-acb3b000 ---p acb3a000 00:00 0 
acb3b000-ad33b000 rwxp acb3b000 00:00 0 
ad33b000-ad33c000 ---p ad33b000 00:00 0 
ad33c000-adb3c000 rwxp ad33c000 00:00 0 
adb3c000-adb3d000 ---p adb3c000 00:00 0 
adb3d000-ae33d000 rwxp adb3d000 00:00 0 
ae33d000-ae33e000 ---p ae33d000 00:00 0 
ae33e000-aeb3e000 rwxp ae33e000 00:00 0 
aeb3e000-aeb3f000 ---p aeb3e000 00:00 0 
aeb3f000-af33f000 rwxp aeb3f000 00:00 0 
af33f000-af340000 ---p af33f000 00:00 0 
af340000-afb40000 rwxp af340000 00:00 0 
afb40000-afb41000 ---p afb40000 00:00 0 
afb41000-b0341000 rwxp afb41000 00:00 0 
b0341000-b0342000 ---p b0341000 00:00 0 
b0342000-b0b42000 rwxp b0342000 00:00 0 
b0b42000-b0b43000 ---p b0b42000 00:00 0 
b0b43000-b1343000 rwxp b0b43000 00:00 0 
b1343000-b1344000 ---p b1343000 00:00 0 
b1344000-b1b44000 rwxp b1344000 00:00 0 
b1b44000-b1b45000 ---p b1b44000 00:00 0 
b1b45000-b2345000 rwxp b1b45000 00:00 0 
b2345000-b2346000 ---p b2345000 00:00 0 
b2346000-b2b46000 rwxp b2346000 00:00 0 
b2b46000-b2b47000 ---p b2b46000 00:00 0 
b2b47000-b3347000 rwxp b2b47000 00:00 0 
b3347000-b3348000 ---p b3347000 00:00 0 
b3348000-b3b48000 rwxp b3348000 00:00 0 
b3b48000-b3b49000 ---p b3b48000 00:00 0 
b3b49000-b4349000 rwxp b3b49000 00:00 0 
b4349000-b434a000 ---p b4349000 00:00 0 
b434a000-b4b4a000 rwxp b434a000 00:00 0 
b4b4a000-b4b4b000 ---p b4b4a000 00:00 0 
b4b4b000-b534b000 rwxp b4b4b000 00:00 0 
b534b000-b5354000 r-xp 00000000 08:05 189862     /lib/tls/i686/cmov/libnss_files-2.7.so
b5354000-b5356000 rw-p 00008000 08:05 189862     /lib/tls/i686/cmov/libnss_files-2.7.so
b5356000-b536a000 r-xp 00000000 08:05 189859     /lib/tls/i686/cmov/libnsl-2.7.so
b536a000-b536c000 rw-p 00013000 08:05 189859     /lib/tls/i686/cmov/libnsl-2.7.so
b536c000-b536e000 rw-p b536c000 00:00 0 
b536e000-b5377000 r-xp 00000000 08:05 189855     /lib/tls/i686/cmov/libcrypt-2.7.so
b5377000-b5379000 rw-p 00008000 08:05 189855     /lib/tls/i686/cmov/libcrypt-2.7.so
b5379000-b53a0000 rw-p b5379000 00:00 0 
b53a0000-b553c000 r-xp 00000000 08:05 310108     /usr/lib/libmysqlclient.so.15.0.0
b553c000-b557f000 rw-p 0019b000 08:05 310108     /usr/lib/libmysqlclient.so.15.0.0
b557f000-b5580000 rw-p b557f000 00:00 0 
b558d000-b559a000 r-xp 00000000 08:05 351738     /usr/lib/qt3/plugins/sqldrivers/libqsqlmysql.so
b559a000-b559b000 rw-p 0000c000 08:05 351738     /usr/lib/qt3/plugins/sqldrivers/libqsqlmysql.so
b559b000-b559c000 rw-p b559b000 00:00 0 
b559c000-b55db000 r--p 00000000 08:05 345814     /usr/lib/locale/fi_FI.utf8/LC_CTYPE
b55db000-b55dc000 r--p 00000000 08:05 345815     /usr/lib/locale/fi_FI.utf8/LC_NUMERIC
b55dc000-b55dd000 r--p 00000000 08:05 345816     /usr/lib/locale/fi_FI.utf8/LC_TIME
b55dd000-b56be000 r--p 00000000 08:05 345817     /usr/lib/locale/fi_FI.utf8/LC_COLLATE
b56be000-b56bf000 r--p 00000000 08:05 345818     /usr/lib/locale/fi_FI.utf8/LC_MONETARY
b56bf000-b56c0000 r--p 00000000 08:05 345820     /usr/lib/locale/fi_FI.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b56c0000-b56c4000 rw-p b56c0000 00:00 0 
b56c4000-b56c8000 r-xp 00000000 08:05 311297     /usr/lib/libXdmcp.so.6.0.0
b56c8000-b56c9000 rw-p 00003000 08:05 311297     /usr/lib/libXdmcp.so.6.0.0
b56c9000-b56cd000 r-xp 00000000 08:05 311301     /usr/lib/libXfixes.so.3.1.0
b56cd000-b56ce000 rw-p 00003000 08:05 311301     /usr/lib/libXfixes.so.3.1.0
b56ce000-b56ed000 r-xp 00000000 08:05 311520     /usr/lib/libexpat.so.1.5.2
b56ed000-b56ef000 rw-p 0001e000 08:05 311520     /usr/lib/libexpat.so.1.5.2
b56ef000-b5706000 r-xp 00000000 08:05 312144     /usr/lib/libxcb.so.1.0.0
b5706000-b5707000 rw-p 00016000 08:05 312144     /usr/lib/libxcb.so.1.0.0
b5707000-b5708000 rw-p b5707000 00:00 0 
b5708000-b5709000 r-xp 00000000 08:05 312140     /usr/lib/libxcb-xlib.so.0.0.0
b5709000-b570a000 rw-p 00000000 08:05 312140     /usr/lib/libxcb-xlib.so.0.0.0
b570a000-b570c000 r-xp 00000000 08:05 311286     /usr/lib/libXau.so.6.0.0
b570c000-b570d000 rw-p 00001000 08:05 311286     /usr/lib/libXau.so.6.0.0
b570d000-b5722000 r-xp 00000000 08:05 311252     /usr/lib/libICE.so.6.3.0
b5722000-b5723000 rw-p 00014000 08:05 311252     /usr/lib/libICE.so.6.3.0
b5723000-b5725000 rw-p b5723000 00:00 0 
b5725000-b572c000 r-xp 00000000 08:05 311276     /usr/lib/libSM.so.6.0.0
b572c000-b572d000 rw-p 00006000 08:05 311276     /usr/lib/libSM.so.6.0.0
b572d000-b573e000 r-xp 00000000 08:05 311305     /usr/lib/libXft.so.2.1.2
b573e000-b573f000 rw-p 00010000 08:05 311305     /usr/lib/libXft.so.2.1.2
b573f000-b5740000 rw-p b573f000 00:00 0 
b5740000-b5748000 r-xp 00000000 08:05 311293     /usr/lib/libXcursor.so.1.0.2
b5748000-b5749000 rw-p 00007000 08:05 311293     /usr/lib/libXcursor.so.1.0.2
b5749000-b5750000 r-xp 00000000 08:05 311307     /usr/lib/libXi.so.6.0.0
b5750000-b5751000 rw-p 00006000 08:05 311307     /usr/lib/libXi.so.6.0.0
b5751000-b5773000 r-xp 00000000 08:05 311954     /usr/lib/libpng12.so.0.15.0
b5773000-b5774000 rw-p 00022000 08:05 311954     /usr/lib/libpng12.so.0.15.0
b5774000-b5793000 r-xp 00000000 08:05 311704     /usr/lib/libjpeg.so.62.0.0
b5793000-b5794000 rw-p 0001e000 08:05 311704     /usr/lib/libjpeg.so.62.0.0
b5794000-b57e1000 r-xp 00000000 08:05 311323     /usr/lib/libXt.so.6.0.0
b57e1000-b57e5000 rw-p 0004c000 08:05 311323     /usr/lib/libXt.so.6.0.0
b57e5000-b57fa000 r-xp 00000000 08:05 311385     /usr/lib/libaudio.so.2.4
b57fa000-b57fb000 rw-p 00015000 08:05 311385     /usr/lib/libaudio.so.2.4
b57fb000-b57fc000 rw-p b57fb000 00:00 0 
b57fc000-b5825000 r-xp 00000000 08:05 311556     /usr/lib/libfontconfig.so.1.3.0
b5825000-b5826000 rw-p 00029000 08:05 311556     /usr/lib/libfontconfig.so.1.3.0
b5826000-b582d000 r-xp 00000000 08:05 311319     /usr/lib/libXrender.so.1.3.0
b582d000-b582e000 rw-p 00007000 08:05 311319     /usr/lib/libXrender.so.1.3.0
b582e000-b5854000 r-xp 00000000 08:05 310471     /usr/lib/libpcre.so.3.12.1
b5854000-b5855000 rw-p 00026000 08:05 310471     /usr/lib/libpcre.so.3.12.1
b5855000-b5934000 r-xp 00000000 08:05 311543     /usr/lib/libfftw3f.so.3.1.2
b5934000-b593a000 rw-p 000df000 08:05 311543     /usr/lib/libfftw3f.so.3.1.2
b593a000-b593b000 rw-p b593a000 00:00 0 
b593b000-b5940000 r-xp 00000000 08:05 310646     /usr/lib/liblirc_client.so.0.2.0
b5940000-b5941000 rw-p 00004000 08:05 310646     /usr/lib/liblirc_client.so.0.2.0
b5941000-b59e5000 r-xp 00000000 08:05 312172     /usr/lib/libxvidcore.so.4.1
b59e5000-b59e6000 rw-p 000a3000 08:05 312172     /usr/lib/libxvidcore.so.4.1
b59e6000-b5a59000 rw-p b59e6000 00:00 0 
b5a59000-b5adf000 r-xp 00000000 08:05 312134     /usr/lib/libx264.so.57
b5adf000-b5ae0000 rw-p 00085000 08:05 312134     /usr/lib/libx264.so.57
b5ae0000-b5ae4000 rw-p b5ae0000 00:00 0 
b5ae4000-b5b1f000 r-xp 00000000 08:05 311513     /usr/lib/libfaad.so.0.0.0
b5b1f000-b5b22000 rw-p 0003a000 08:05 311513     /usr/lib/libfaad.so.0.0.0
b5b22000-b5b23000 rw-p b5b22000 00:00 0 
b5b23000-b5b31000 r-xp 00000000 08:05 311527     /usr/lib/libfaac.so.0.0.0
b5b31000-b5b34000 rw-p 0000d000 08:05 311527     /usr/lib/libfaac.so.0.0.0
b5b34000-b5c7d000 r-xp 00000000 08:05 189853     /lib/tls/i686/cmov/libc-2.7.so
b5c7d000-b5c7e000 r--p 00149000 08:05 189853     /lib/tls/i686/cmov/libc-2.7.so
b5c7e000-b5c80000 rw-p 0014a000 08:05 189853     /lib/tls/i686/cmov/libc-2.7.so
b5c80000-b5c83000 rw-p b5c80000 00:00 0 
b5c83000-b5c8d000 r-xp 00000000 08:05 171381     /lib/libgcc_s.so.1
b5c8d000-b5c8e000 rw-p 0000a000 08:05 171381     /lib/libgcc_s.so.1
b5c8e000-b5cb1000 r-xp 00000000 08:05 189857     /lib/tls/i686/cmov/libm-2.7.so
b5cb1000-b5cb3000 rw-p 00023000 08:05 189857     /lib/tls/i686/cmov/libm-2.7.so
b5cb3000-b5d9b000 r-xp 00000000 08:05 311534     /usr/lib/libstdc++.so.6.0.9
b5d9b000-b5d9e000 r--p 000e8000 08:05 311534     /usr/lib/libstdc++.so.6.0.9
b5d9e000-b5da0000 rw-p 000eb000 08:05 311534     /usr/lib/libstdc++.so.6.0.9
b5da0000-b5da7000 rw-p b5da0000 00:00 0 
b5da7000-b5dbb000 r-xp 00000000 08:05 189867     /lib/tls/i686/cmov/libpthread-2.7.so
b5dbb000-b5dbd000 rw-p 00013000 08:05 189867     /lib/tls/i686/cmov/libpthread-2.7.so
b5dbd000-b5dbf000 rw-p b5dbd000 00:00 0 
b5dbf000-b5ea3000 r-xp 00000000 08:05 311280     /usr/lib/libX11.so.6.2.0
b5ea3000-b5ea6000 rw-p 000e4000 08:05 311280     /usr/lib/libX11.so.6.2.0
b5ea6000-b5eb3000 r-xp 00000000 08:05 311299     /usr/lib/libXext.so.6.4.0
b5eb3000-b5eb4000 rw-p 0000d000 08:05 311299     /usr/lib/libXext.so.6.4.0
b5eb4000-b5ec9000 r-xp 00000000 08:05 311311     /usr/lib/libXmu.so.6.2.0
b5ec9000-b5eca000 rw-p 00015000 08:05 311311     /usr/lib/libXmu.so.6.2.0
b5eca000-b5f3e000 r-xp 00000000 08:05 311937     /usr/lib/libGL.so.1.2
b5f3e000-b5f40000 rw-p 00073000 08:05 311937     /usr/lib/libGL.so.1.2
b5f40000-b5f44000 rw-p b5f40000 00:00 0 
b5f44000-b5fc6000 r-xp 00000000 08:05 311245     /usr/lib/libGLU.so.1.3.070002
b5fc6000-b5fc7000 rw-p 00081000 08:05 311245     /usr/lib/libGLU.so.1.3.070002
b5fc7000-b5fc8000 rw-p b5fc7000 00:00 0 
b5fc8000-b679e000 r-xp 00000000 08:05 311979     /usr/lib/libqt-mt.so.3.3.8
b679e000-b67e4000 rw-p 007d5000 08:05 311979     /usr/lib/libqt-mt.so.3.3.8
b67e4000-b67e8000 rw-p b67e4000 00:00 0 
b67e8000-b67eb000 r-xp 00000000 08:05 311329     /usr/lib/libXvMC.so.1.0.0
b67eb000-b67ec000 rw-p 00002000 08:05 311329     /usr/lib/libXvMC.so.1.0.0
b67ec000-b67f0000 r-xp 00000000 08:05 311331     /usr/lib/libXvMCW.so.1.0.0
b67f0000-b67f1000 rw-p 00003000 08:05 311331     /usr/lib/libXvMCW.so.1.0.0
b67f1000-b67f6000 r-xp 00000000 08:05 311317     /usr/lib/libXrandr.so.2.1.0
b67f6000-b67f7000 rw-p 00005000 08:05 311317     /usr/lib/libXrandr.so.2.1.0
b67f7000-b67fb000 r-xp 00000000 08:05 311337     /usr/lib/libXxf86vm.so.1.0.0
b67fb000-b67fc000 rw-p 00003000 08:05 311337     /usr/lib/libXxf86vm.so.1.0.0
b67fc000-b6800000 r-xp 00000000 08:05 311327     /usr/lib/libXv.so.1.0.0
b6800000-b6801000 rw-p 00003000 08:05 311327     /usr/lib/libXv.so.1.0.0
b6801000-b6802000 rw-p b6801000 00:00 0 
b6802000-b6804000 r-xp 00000000 08:05 311309     /usr/lib/libXinerama.so.1.0.0
b6804000-b6805000 rw-p 00001000 08:05 311309     /usr/lib/libXinerama.so.1.0.0
b6805000-b6808000 r-xp 00000000 08:05 311998     /usr/lib/librom1394.so.0.3.0
b6808000-b6809000 rw-p 00002000 08:05 311998     /usr/lib/librom1394.so.0.3.0
b6809000-b680c000 r-xp 00000000 08:05 311399     /usr/lib/libavc1394.so.0.3.0
b680c000-b680d000 rw-p 00002000 08:05 311399     /usr/lib/libavc1394.so.0.3.0
b680d000-b6819000 r-xp 00000000 08:05 311689     /usr/lib/libiec61883.so.0.1.0
b6819000-b681a000 rw-p 0000b000 08:05 311689     /usr/lib/libiec61883.so.0.1.0
b681a000-b681f000 r-xp 00000000 08:05 311988     /usr/lib/libraw1394.so.8.2.0
b681f000-b6820000 rw-p 00004000 08:05 311988     /usr/lib/libraw1394.so.8.2.0
b6820000-b682f000 r-xp 00000000 08:05 311700     /usr/lib/libjack.so.0.0.28
b682f000-b6831000 rw-p 0000f000 08:05 311700     /usr/lib/libjack.so.0.0.28
b6831000-b683a000 rw-p b6831000 00:00 0 
b683a000-b68ea000 r-xp 00000000 08:05 310285     /usr/lib/libglib-2.0.so.0.1600.6
b68ea000-b68eb000 rw-p 000b0000 08:05 310285     /usr/lib/libglib-2.0.so.0.1600.6
b68eb000-b68f2000 r-xp 00000000 08:05 189869     /lib/tls/i686/cmov/librt-2.7.so
b68f2000-b68f4000 rw-p 00006000 08:05 189869     /lib/tls/i686/cmov/librt-2.7.so
b68f4000-b68f8000 r-xp 00000000 08:05 310668     /usr/lib/libgthread-2.0.so.0.1600.6
b68f8000-b68f9000 rw-p 00003000 08:05 310668     /usr/lib/libgthread-2.0.so.0.1600.6
b68f9000-b68fb000 r-xp 00000000 08:05 189856     /lib/tls/i686/cmov/libdl-2.7.so
b68fb000-b68fd000 rw-p 00001000 08:05 189856     /lib/tls/i686/cmov/libdl-2.7.so
b68fd000-b6900000 r-xp 00000000 08:05 310287     /usr/lib/libgmodule-2.0.so.0.1600.6
b6900000-b6901000 rw-p 00002000 08:05 310287     /usr/lib/libgmodule-2.0.so.0.1600.6
b6901000-b6906000 r-xp 00000000 08:05 311753     /usr/lib/libartsc.so.0.0.0
b6906000-b6907000 rw-p 00004000 08:05 311753     /usr/lib/libartsc.so.0.0.0
b6907000-b6908000 rw-p b6907000 00:00 0 
b6908000-b69c7000 r-xp 00000000 08:05 311377     /usr/lib/libasound.so.2.0.0
b69c7000-b69cb000 rw-p 000be000 08:05 311377     /usr/lib/libasound.so.2.0.0
b69cb000-b6a2d000 r-xp 00000000 08:05 311853     /usr/lib/libmp3lame.so.0.0.0
b6a2d000-b6a2f000 rw-p 00062000 08:05 311853     /usr/lib/libmp3lame.so.0.0.0
b6a2f000-b6a60000 rw-p b6a2f000 00:00 0 
b6a60000-b6a74000 r-xp 00000000 08:05 312174     /usr/lib/libz.so.1.2.3.3
b6a74000-b6a75000 rw-p 00013000 08:05 312174     /usr/lib/libz.so.1.2.3.3
b6a75000-b6adf000 r-xp 00000000 08:05 310280     /usr/lib/libfreetype.so.6.3.16
b6adf000-b6ae2000 rw-p 0006a000 08:05 310280     /usr/lib/libfreetype.so.6.3.16
b6ae2000-b6b6e000 r-xp 00000000 08:05 310635     /usr/lib/libmythui-0.21.so.0.21.0
b6b6e000-b6b71000 rw-p 0008b000 08:05 310635     /usr/lib/libmythui-0.21.so.0.21.0
b6b71000-b6e5f000 r-xp 00000000 08:05 310332     /usr/lib/libmyth-0.21.so.0.21.0
b6e5f000-b6e70000 rw-p 002ed000 08:05 310332     /usr/lib/libmyth-0.21.so.0.21.0
b6e70000-b6e72000 rw-p b6e70000 00:00 0 
b6e72000-b6f31000 r-xp 00000000 08:05 310633     /usr/lib/libmythlivemedia-0.21.so.0.21.0
b6f31000-b6f3b000 rw-p 000bf000 08:05 310633     /usr/lib/libmythlivemedia-0.21.so.0.21.0
b6f3b000-b6f49000 rw-p b6f3b000 00:00 0 
b6f49000-b6fe1000 r-xp 00000000 08:05 310644     /usr/lib/libmythupnp-0.21.so.0.21.0
b6fe1000-b6fe3000 rw-p 00098000 08:05 310644     /usr/lib/libmythupnp-0.21.so.0.21.0
b6fe3000-b7062000 r-xp 00000000 08:05 310639     /usr/lib/libmythfreemheg-0.21.so.0.21.0
b7062000-b7069000 rw-p 0007e000 08:05 310639     /usr/lib/libmythfreemheg-0.21.so.0.21.0
b7069000-b73ca000 r-xp 00000000 08:05 310643     /usr/lib/libmythavcodec-0.21.so.0.21.0
b73ca000-b73d8000 rw-p 00361000 08:05 310643     /usr/lib/libmythavcodec-0.21.so.0.21.0
b73d8000-b74d8000 rw-p b73d8000 00:00 0 
b74d8000-b74e1000 r-xp 00000000 08:05 310679     /usr/lib/libmythavutil-0.21.so.0.21.0
b74e1000-b74e2000 rw-p 00008000 08:05 310679     /usr/lib/libmythavutil-0.21.so.0.21.0
b74e2000-b74e5000 rw-p b74e2000 00:00 0 
b74e5000-b7566000 r-xp 00000000 08:05 310224     /usr/lib/libmythavformat-0.21.so.0.21.0
b7566000-b756d000 rw-p 00080000 08:05 310224     /usr/lib/libmythavformat-0.21.so.0.21.0
b756d000-b7571000 rw-p b756d000 00:00 0 
b7571000-b7f6c000 r-xp 00000000 08:05 310118     /usr/lib/libmythtv-0.21.so.0.21.0
b7f6c000-b7fa1000 rw-p 009fa000 08:05 310118     /usr/lib/libmythtv-0.21.so.0.21.0
b7fa1000-b7fa5000 rw-p b7fa1000 00:00 0 
b7fa5000-b7fa6000 r--p 00000000 08:05 345821     /usr/lib/locale/fi_FI.utf8/LC_PAPER
b7fa6000-b7fa7000 r--p 00000000 08:05 345822     /usr/lib/locale/fi_FI.utf8/LC_NAME
b7fa7000-b7fa8000 r--p 00000000 08:05 345823     /usr/lib/locale/fi_FI.utf8/LC_ADDRESS
b7fa8000-b7fa9000 r--p 00000000 08:05 345824     /usr/lib/locale/fi_FI.utf8/LC_TELEPHONE
b7fa9000-b7faa000 r--p 00000000 08:05 345825     /usr/lib/locale/fi_FI.utf8/LC_MEASUREMENT
b7faa000-b7fb1000 r--s 00000000 08:05 326785     /usr/lib/gconv/gconv-modules.cache
b7fb1000-b7fb2000 r--p 00000000 08:05 345826     /usr/lib/locale/fi_FI.utf8/LC_IDENTIFICATION
b7fb2000-b7fb4000 rw-p b7fb2000 00:00 0 
b7fb4000-b7fb5000 r-xp b7fb4000 00:00 0          [vdso]
b7fb5000-b7fcf000 r-xp 00000000 08:05 171903     /lib/ld-2.7.so
b7fcf000-b7fd1000 rw-p 00019000 08:05 171903     /lib/ld-2.7.so
bffb6000-bffca000 rwxp bffeb000 00:00 0          [stack]
bffca000-bffcb000 rw-p bffff000 00:00 0 
```

Then i checked sudo /etc/init.d/mythtv-backend status
and backend wasn't running..

First backend crash in four months.. Hope there is some Mythtv guru how can light something about crash.. 

Have to find out script which restart backend if crash happens.

---

### Post by ian dobson on 2008-10-20
Hi,

I can't say much about the crash, but here's a script I use to watch my backend:-

```

#!/bin/bash
##################################################
#
#  Check status of the SMP folding client and
#  restart it if it hasn't done anything for 15 minutes
#  (c) dobs
##################################################


while [ 1 == 1 ]
do
   chk=`ps -A |  grep "mythbackend"`
   if [ "$chk" == "" ]; then
      /etc/init.d/mythtv-backend stop
      sleep 5
      /etc/init.d/mythtv-backend start
      datum=`date`
      echo $datum  restarting mythtv-backend >> /var/log/myth-watch.log
   fi
   sleep 30
done

```

Regards
Ian Dobson

---

