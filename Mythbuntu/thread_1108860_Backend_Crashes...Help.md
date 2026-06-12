---
title: "Backend Crashes...Help"
date: 2009-03-28
forum: Mythbuntu
---

### Post by nrune on 2009-03-28
My backend keeps crashing, help.  

Mythbackend.log
```
2009-03-28 04:00:25.856 RingBuf(/var/lib/mythtv/recordings/1269_20090328040000.mpg) Error: Invalid file descriptor in 'safe_read()'
*** glibc detected *** /usr/bin/mythbackend: malloc(): memory corruption (fast): 0xaba9fd39 ***
2009-03-28 04:01:08.548 New DB connection, total: 2
2009-03-28 04:01:09.524 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb5ab8962]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x8d)[0xb5ab9cad]
/usr/lib/libstdc++.so.6(_Znwj+0x27)[0xb5c84447]
/usr/lib/libqt-mt.so.3(_ZN8QVariantC1Ev+0x1f)[0xb62868df]
/usr/lib/libqt-mt.so.3(_ZN8QMapNodeI7QString5ParamEC1ERKS0_+0x28)[0xb64dbe2c]
/usr/lib/libqt-mt.so.3(_ZN11QMapPrivateI7QString5ParamE6insertEP12QMapNodeBaseS4_RKS0_+0x30)[0xb64dbeae]
/usr/lib/libqt-mt.so.3(_ZN11QMapPrivateI7QString5ParamE12insertSingleERKS0_+0xe6)[0xb64dc0b2]
/usr/lib/libqt-mt.so.3(_ZN4QMapI7QString5ParamE6insertERKS0_RKS1_b+0x4c)[0xb64dc170]
/usr/lib/libqt-mt.so.3(_ZN4QMapI7QString5ParamEixERKS0_+0xbd)[0xb64dc27f]
/usr/lib/libqt-mt.so.3(_ZN13QSqlExtension9bindValueERK7QStringRK8QVariantN4QSql13ParameterTypeE+0xab)[0xb64ecdb9]
/usr/lib/libqt-mt.so.3(_ZN9QSqlQuery9bindValueERK7QStringRK8QVariantN4QSql13ParameterTypeE+0x7a)[0xb64d8b92]
/usr/lib/libqt-mt.so.3(_ZN9QSqlQuery9bindValueERK7QStringRK8QVariant+0x33)[0xb64d8bcb]
/usr/lib/libmythtv-0.21.so.0(_ZN11ProgramInfo11MarkAsInUseEb7QString+0x644)[0xb7617e04]
======= Memory map: ========
08048000-08159000 r-xp 00000000 03:01 6857269    /usr/bin/mythbackend
08159000-0815a000 rw-p 00111000 03:01 6857269    /usr/bin/mythbackend
0815a000-08a76000 rw-p 0815a000 00:00 0          [heap]
a78fa000-a78fb000 ---p a78fa000 00:00 0 
a78fb000-a80fb000 rwxp a78fb000 00:00 0 
a80fb000-a80fc000 ---p a80fb000 00:00 0 
a80fc000-a88fc000 rwxp a80fc000 00:00 0 
a88fc000-a88fd000 ---p a88fc000 00:00 0 
a88fd000-a90fd000 rwxp a88fd000 00:00 0 
a90fd000-a90fe000 ---p a90fd000 00:00 0 
a90fe000-a98fe000 rwxp a90fe000 00:00 0 
a98fe000-a98ff000 ---p a98fe000 00:00 0 
a98ff000-aa0ff000 rwxp a98ff000 00:00 0 
aa300000-aa3ff000 rw-p aa300000 00:00 0 
aa3ff000-aa400000 ---p aa3ff000 00:00 0 
aa5fe000-aa5ff000 ---p aa5fe000 00:00 0 
aa5ff000-aadff000 rwxp aa5ff000 00:00 0 
aadff000-aae00000 ---p aadff000 00:00 0 
aae00000-ab600000 rwxp aae00000 00:00 0 
ab600000-ab6fd000 rw-p ab600000 00:00 0 
ab6fd000-ab700000 ---p ab6fd000 00:00 0 
ab700000-ab7ea000 rw-p ab700000 00:00 0 
ab7ea000-ab800000 ---p ab7ea000 00:00 0 
ab800000-aba00000 rw-p ab800000 00:00 0 
aba00000-abc00000 rw-p aba00000 00:00 0 
abc00000-abd00000 rw-p abc00000 00:00 0 
ac005000-ac006000 ---p ac005000 00:00 0 
ac006000-ac806000 rwxp ac006000 00:00 0 
acb04000-ace06000 rw-p acb04000 00:00 0 
ad007000-ad008000 ---p ad007000 00:00 0 
ad008000-ad808000 rwxp ad008000 00:00 0 
ad808000-ad809000 ---p ad808000 00:00 0 
ad809000-ae009000 rwxp ad809000 00:00 0 
ae009000-ae00a000 ---p ae009000 00:00 0 
ae00a000-ae80a000 rwxp ae00a000 00:00 0 
ae80a000-ae80b000 ---p ae80a000 00:00 0 
ae80b000-af00b000 rwxp ae80b000 00:00 0 
af00b000-af00c000 ---p af00b000 00:00 0 
af00c000-af80c000 rwxp af00c000 00:00 0 
af80c000-af80d000 ---p af80c000 00:00 0 
af80d000-b000d000 rwxp af80d000 00:00 0 
b000d000-b000e000 ---p b000d000 00:00 0 
b000e000-b080e000 rwxp b000e000 00:00 0 
b080e000-b080f000 ---p b080e000 00:00 0 
b080f000-b100f000 rwxp b080f000 00:00 0 
b100f000-b1010000 ---p b100f000 00:00 0 
b1010000-b1810000 rwxp b1010000 00:00 0 
b1810000-b1811000 ---p b1810000 00:00 0 
b1811000-b2011000 rwxp b1811000 00:00 0 
b2011000-b2012000 ---p b2011000 00:00 0 
b2012000-b2812000 rwxp b2012000 00:00 0 
b2812000-b2813000 ---p b2812000 00:00 0 
b2813000-b3013000 rwxp b2813000 00:00 0 
b3013000-b3014000 ---p b3013000 00:00 0 
b3014000-b3814000 rwxp b3014000 00:00 0 
b3814000-b3815000 ---p b3814000 00:00 0 
b3815000-b4015000 rwxp b3815000 00:00 0 
b4015000-b4016000 ---p b4015000 00:00 0 
b4016000-b4816000 rwxp b4016000 00:00 0 
b4816000-b481f000 r-xp 00000000 03:01 3335188    /lib/tls/i686/cmov/libnss_files-2.7.so
b481f000-b4821000 rw-p 00008000 03:01 3335188    /lib/tls/i686/cmov/libnss_files-2.7.so
b4821000-b4835000 r-xp 00000000 03:01 3335185    /lib/tls/i686/cmov/libnsl-2.7.so
b4835000-b4837000 rw-p 00013000 03:01 3335185    /lib/tls/i686/cmov/libnsl-2.7.so
b4837000-b4839000 rw-p b4837000 00:00 0 
b4839000-b4842000 r-xp 00000000 03:01 3335181    /lib/tls/i686/cmov/libcrypt-2.7.so
b4842000-b4844000 rw-p 00008000 03:01 3335181    /lib/tls/i686/cmov/libcrypt-2.7.so
b4844000-b486b000 rw-p b4844000 00:00 0 
b486b000-b4a07000 r-xp 00000000 03:01 6857139    /usr/lib/libmysqlclient.so.15.0.0
b4a07000-b4a4a000 rw-p 0019b000 03:01 6857139    /usr/lib/libmysqlclient.so.15.0.0
b4a4a000-b4a4b000 rw-p b4a4a000 00:00 0 
b4a5d000-b4ac4000 rw-p b4a5d000 00:00 0 
b4ac4000-b4ac8000 r-xp 00000000 03:01 6857922    /usr/lib/libXdmcp.so.6.0.0
b4ac8000-b4ac9000 rw-p 00003000 03:01 6857922    /usr/lib/libXdmcp.so.6.0.0
b4ac9000-b4aca000 rw-p b4ac9000 00:00 0 
b4aca000-b4ace000 r-xp 00000000 03:01 6857926    /usr/lib/libXfixes.so.3.1.0
b4ace000-b4acf000 rw-p 00003000 03:01 6857926    /usr/lib/libXfixes.so.3.1.0
b4acf000-b4aee000 r-xp 00000000 03:01 6858145    /usr/lib/libexpat.so.1.5.2
b4aee000-b4af0000 rw-p 0001e000 03:01 6858145    /usr/lib/libexpat.so.1.5.2
b4af0000-b4b07000 r-xp 00000000 03:01 6858776    /usr/lib/libxcb.so.1.0.0
b4b07000-b4b08000 rw-p 00016000 03:01 6858776    /usr/lib/libxcb.so.1.0.0
b4b08000-b4b09000 r-xp 00000000 03:01 6858772    /usr/lib/libxcb-xlib.so.0.0.0
b4b09000-b4b0a000 rw-p 00000000 03:01 6858772    /usr/lib/libxcb-xlib.so.0.0.0
b4b0a000-b4b0c000 r-xp 00000000 03:01 6857911    /usr/lib/libXau.so.6.0.0
b4b0c000-b4b0d000 rw-p 00001000 03:01 6857911    /usr/lib/libXau.so.6.0.0
b4b0d000-b4b0e000 rw-p b4b0d000 00:00 0 
b4b0e000-b4b0f000 r-xp 00000000 03:01 344740     /usr/lib/libnvidia-tls.so.169.12
b4b0f000-b4b10000 rw-p 00000000 03:01 344740     /usr/lib/libnvidia-tls.so.169.12
b4b10000-b55e4000 r-xp 00000000 03:01 344738     /usr/lib/libGLcore.so.169.12
b55e4000-b5620000 rwxp 00ad3000 03:01 344738     /usr/lib/libGLcore.so.169.12
b5620000-b5625000 rwxp b5620000 00:00 0 
b5625000-b563a000 r-xp 00000000 03:01 6857877    /usr/lib/libICE.so.6.3.0
b563a000-b563b000 rw-p 00014000 03:01 6857877    /usr/lib/libICE.so.6.3.0
b563b000-b563d000 rw-p b563b000 00:00 0 
b563d000-b5644000 r-xp 00000000 03:01 6857901    /usr/lib/libSM.so.6.0.0
b5644000-b5645000 rw-p 00006000 03:01 6857901    /usr/lib/libSM.so.6.0.0
b5645000-b5656000 r-xp 00000000 03:01 6857930    /usr/lib/libXft.so.2.1.2
b5656000-b5657000 rw-p 00010000 03:01 6857930    /usr/lib/libXft.so.2.1.2
b5657000-b5658000 rw-p b5657000 00:00 0 
b5658000-b5660000 r-xp 00000000 03:01 6857918    /usr/lib/libXcursor.so.1.0.2
b5660000-b5661000 rw-p 00007000 03:01 6857918    /usr/lib/libXcursor.so.1.0.2
b5661000-b5668000 r-xp 00000000 03:01 6857932    /usr/lib/libXi.so.6.0.0
b5668000-b5669000 rw-p 00006000 03:01 6857932    /usr/lib/libXi.so.6.0.0
b5669000-b568b000 r-xp 00000000 03:01 6858510    /usr/lib/libpng12.so.0.15.0
b568b000-b568c000 rw-p 00022000 03:01 6858510    /usr/lib/libpng12.so.0.15.0
b568c000-b56ab000 r-xp 00000000 03:01 6858329    /usr/lib/libjpeg.so.62.0.0
b56ab000-b56ac000 rw-p 0001e000 03:01 6858329    /usr/lib/libjpeg.so.62.0.0
b56ac000-b56f9000 r-xp 00000000 03:01 6857948    /usr/lib/libXt.so.6.0.0
b56f9000-b56fd000 rw-p 0004c000 03:01 6857948    /usr/lib/libXt.so.6.0.0
b56fd000-b5712000 r-xp 00000000 03:01 6858010    /usr/lib/libaudio.so.2.4
b5712000-b5713000 rw-p 00015000 03:01 6858010    /usr/lib/libaudio.so.2.4
b5713000-b5714000 rw-p b5713000 00:00 0 
b5714000-b573d000 r-xp 00000000 03:01 6858181    /usr/lib/libfontconfig.so.1.3.0
b573d000-b573e000 rw-p 00029000 03:01 6858181    /usr/lib/libfontconfig.so.1.3.0
b573e000-b5745000 r-xp 00000000 03:01 6857944    /usr/lib/libXrender.so.1.3.0
b5745000-b5746000 rw-p 00007000 03:01 6857944    /usr/lib/libXrender.so.1.3.0
b5746000-b576c000 r-xp 00000000 03:01 6857984    /usr/lib/libpcre.so.3.12.1
b576c000-b576d000 rw-p 00026000 03:01 6857984    /usr/lib/libpcre.so.3.12.1
b576d000-b584c000 r-xp 00000000 03:01 6858168    /usr/lib/libfftw3f.so.3.1.2
b584c000-b5852000 rw-p 000df000 03:01 6858168    /usr/lib/libfftw3f.so.3.1.2
b5852000-b5853000 rw-p b5852000 00:00 0 
b5853000-b5858000 r-xp 00000000 03:01 6858445    /usr/lib/liblirc_client.so.0.2.0
b5858000-b5859000 rw-p 00004000 03:01 6858445    /usr/lib/liblirc_client.so.0.2.0
b5859000-b58fd000 r-xp 00000000 03:01 6858804    /usr/lib/libxvidcore.so.4.1
b58fd000-b58fe000 rw-p 000a3000 03:01 6858804    /usr/lib/libxvidcore.so.4.1
b58fe000-b5971000 rw-p b58fe000 00:00 0 
b5971000-b59f7000 r-xp 00000000 03:01 6858766    /usr/lib/libx264.so.57
b59f7000-b59f8000 rw-p 00085000 03:01 6858766    /usr/lib/libx264.so.57
b59f8000-b59fc000 rw-p b59f8000 00:00 0 
b59fc000-b5a37000 r-xp 00000000 03:01 6859301    /usr/lib/libfaad.so.0.0.0
b5a37000-b5a3a000 rw-p 0003a000 03:01 6859301    /usr/lib/libfaad.so.0.0.0
b5a3a000-b5a3b000 rw-p b5a3a000 00:00 0 
b5a3b000-b5a49000 r-xp 00000000 03:01 6858152    /usr/lib/libfaac.so.0.0.0
b5a49000-b5a4c000 rw-p 0000d000 03:01 6858152    /usr/lib/libfaac.so.0.0.0
b5a4c000-b5b95000 r-xp 00000000 03:01 3335179    /lib/tls/i686/cmov/libc-2.7.so
b5b95000-b5b96000 r--p 00149000 03:01 3335179    /lib/tls/i686/cmov/libc-2.7.so
b5b96000-b5b98000 rw-p 0014a000 03:01 3335179    /lib/tls/i686/cmov/libc-2.7.so
b5b98000-b5b9b000 rw-p b5b98000 00:00 0 
b5b9b000-b5ba5000 r-xp 00000000 03:01 3317847    /lib/libgcc_s.so.1
b5ba5000-b5ba6000 rw-p 0000a000 03:01 3317847    /lib/libgcc_s.so.1
b5ba6000-b5bc9000 r-xp 00000000 03:01 3335183    /lib/tls/i686/cmov/libm-2.7.so
b5bc9000-b5bcb000 rw-p 00023000 03:01 3335183    /lib/tls/i686/cmov/libm-2.7.so
b5bcb000-b5cb3000 r-xp 00000000 03:01 6857137    /usr/lib/libstdc++.so.6.0.9
b5cb3000-b5cb6000 r--p 000e8000 03:01 6857137    /usr/lib/libstdc++.so.6.0.9
b5cb6000-b5cb8000 rw-p 000eb000 03:01 6857137    /usr/lib/libstdc++.so.6.0.9
b5cb8000-b5cbf000 rw-p b5cb8000 00:00 0 
b5cbf000-b5cd3000 r-xp 00000000 03:01 3335193    /lib/tls/i686/cmov/libpthread-2.7.so
b5cd3000-b5cd5000 rw-p 00013000 03:01 3335193    /lib/tls/i686/cmov/libpthread-2.7.so
b5cd5000-b5cd7000 rw-p b5cd5000 00:00 0 
b5cd7000-b5dbb000 r-xp 00000000 03:01 6857905    /usr/lib/libX11.so.6.2.0
b5dbb000-b5dbe000 rw-p 000e4000 03:01 6857905    /usr/lib/libX11.so.6.2.0
b5dbe000-b5dcb000 r-xp 00000000 03:01 6857924    /usr/lib/libXext.so.6.4.0
b5dcb000-b5dcc000 rw-p 0000d000 03:01 6857924    /usr/lib/libXext.so.6.4.0
b5dcc000-b5de1000 r-xp 00000000 03:01 6857936    /usr/lib/libXmu.so.6.2.0
b5de1000-b5de2000 rw-p 00015000 03:01 6857936    /usr/lib/libXmu.so.6.2.0
b5de2000-b5e6a000 r-xp 00000000 03:01 344737     /usr/lib/libGL.so.169.12
b5e6a000-b5e85000 rwxp 00087000 03:01 344737     /usr/lib/libGL.so.169.12
b5e85000-b5e86000 rwxp b5e85000 00:00 0 
b5e86000-b5f08000 r-xp 00000000 03:01 6857870    /usr/lib/libGLU.so.1.3.070002
b5f08000-b5f09000 rw-p 00081000 03:01 6857870    /usr/lib/libGLU.so.1.3.070002
b5f09000-b5f0a000 rw-p b5f09000 00:00 0 
b5f0a000-b66e0000 r-xp 00000000 03:01 6858609    /usr/lib/libqt-mt.so.3.3.8
b66e0000-b6726000 rw-p 007d5000 03:01 6858609    /usr/lib/libqt-mt.so.3.3.8
b6726000-b672a000 rw-p b6726000 00:00 0 
b672a000-b672d000 r-xp 00000000 03:01 6857954    /usr/lib/libXvMC.so.1.0.0
b672d000-b672e000 rw-p 00002000 03:01 6857954    /usr/lib/libXvMC.so.1.0.0
b672e000-b6732000 r-xp 00000000 03:01 6857956    /usr/lib/libXvMCW.so.1.0.0
b6732000-b6733000 rw-p 00003000 03:01 6857956    /usr/lib/libXvMCW.so.1.0.0
b6733000-b6738000 r-xp 00000000 03:01 6857942    /usr/lib/libXrandr.so.2.1.0
b6738000-b6739000 rw-p 00005000 03:01 6857942    /usr/lib/libXrandr.so.2.1.0
b6739000-b673d000 r-xp 00000000 03:01 6857962    /usr/lib/libXxf86vm.so.1.0.0
b673d000-b673e000 rw-p 00003000 03:01 6857962    /usr/lib/libXxf86vm.so.1.0.0
b673e000-b6742000 r-xp 00000000 03:01 6857952    /usr/lib/libXv.so.1.0.0
b6742000-b6743000 rw-p 00003000 03:01 6857952    /usr/lib/libXv.so.1.0.0
b6743000-b6744000 rw-p b6743000 00:00 0 
b6744000-b6746000 r-xp 00000000 03:01 6857934    /usr/lib/libXinerama.so.1.0.0
b6746000-b6747000 rw-p 00001000 03:01 6857934    /usr/lib/libXinerama.so.1.0.0
b6747000-b674a000 r-xp 00000000 03:01 6858628    /usr/lib/librom1394.so.0.3.0
b674a000-b674b000 rw-p 00002000 03:01 6858628    /usr/lib/librom1394.so.0.3.0
b674b000-b674e000 r-xp 00000000 03:01 6858024    /usr/lib/libavc1394.so.0.3.0
b674e000-b674f000 rw-p 00002000 03:01 6858024    /usr/lib/libavc1394.so.0.3.0
b674f000-b675b000 r-xp 00000000 03:01 6858314    /usr/lib/libiec61883.so.0.1.0
b675b000-b675c000 rw-p 0000b000 03:01 6858314    /usr/lib/libiec61883.so.0.1.0
b675c000-b6761000 r-xp 00000000 03:01 6858618    /usr/lib/libraw1394.so.8.2.0
b6761000-b6762000 rw-p 00004000 03:01 6858618    /usr/lib/libraw1394.so.8.2.0
b6762000-b6771000 r-xp 00000000 03:01 6858325    /usr/lib/libjack.so.0.0.28
b6771000-b6773000 rw-p 0000f000 03:01 6858325    /usr/lib/libjack.so.0.0.28
b6773000-b677c000 rw-p b6773000 00:00 0 
b677c000-b682c000 r-xp 00000000 03:01 6858606    /usr/lib/libglib-2.0.so.0.1600.6
b682c000-b682d000 rw-p 000b0000 03:01 6858606    /usr/lib/libglib-2.0.so.0.1600.6
b682d000-b6834000 r-xp 00000000 03:01 3335195    /lib/tls/i686/cmov/librt-2.7.so
b6834000-b6836000 rw-p 00006000 03:01 3335195    /lib/tls/i686/cmov/librt-2.7.so
b6836000-b683a000 r-xp 00000000 03:01 6858645    /usr/lib/libgthread-2.0.so.0.1600.6
b683a000-b683b000 rw-p 00003000 03:01 6858645    /usr/lib/libgthread-2.0.so.0.1600.6
b683b000-b683d000 r-xp 00000000 03:01 3335182    /lib/tls/i686/cmov/libdl-2.7.so
b683d000-b683f000 rw-p 00001000 03:01 3335182    /lib/tls/i686/cmov/libdl-2.7.so
b683f000-b6842000 r-xp 00000000 03:01 6858641    /usr/lib/libgmodule-2.0.so.0.1600.6
b6842000-b6843000 rw-p 00002000 03:01 6858641    /usr/lib/libgmodule-2.0.so.0.1600.6
b6843000-b6848000 r-xp 00000000 03:01 6858266    /usr/lib/libartsc.so.0.0.0
b6848000-b6849000 rw-p 00004000 03:01 6858266    /usr/lib/libartsc.so.0.0.0
b6849000-b684a000 rw-p b6849000 00:00 0 
b684a000-b6909000 r-xp 00000000 03:01 6858002    /usr/lib/libasound.so.2.0.0
b6909000-b690d000 rw-p 000be000 03:01 6858002    /usr/lib/libasound.so.2.0.0
b690d000-b696f000 r-xp 00000000 03:01 6858478    /usr/lib/libmp3lame.so.0.0.0
b696f000-b6971000 rw-p 00062000 03:01 6858478    /usr/lib/libmp3lame.so.0.0.0
b6971000-b69a2000 rw-p b6971000 00:00 0 
b69a2000-b69b6000 r-xp 00000000 03:01 6858806    /usr/lib/libz.so.1.2.3.3
b69b6000-b69b7000 rw-p 00013000 03:01 6858806    /usr/lib/libz.so.1.2.3.3
b69b7000-b6a21000 r-xp 00000000 03:01 6859496    /usr/lib/libfreetype.so.6.3.16
b6a21000-b6a24000 rw-p 0006a000 03:01 6859496    /usr/lib/libfreetype.so.6.3.16
b6a24000-b6ab0000 r-xp 00000000 03:01 6857263    /usr/lib/libmythui-0.21.so.0.21.0
b6ab0000-b6ab3000 rw-p 0008b000 03:01 6857263    /usr/lib/libmythui-0.21.so.0.21.0
b6ab3000-b6da1000 r-xp 00000000 03:01 6856830    /usr/lib/libmyth-0.21.so.0.21.0
b6da1000-b6db2000 rw-p 002ed000 03:01 6856830    /usr/lib/libmyth-0.21.so.0.21.0
b6db2000-b6db4000 rw-p b6db2000 00:00 0 
b6db4000-b6e73000 r-xp 00000000 03:01 6857258    /usr/lib/libmythlivemedia-0.21.so.0.21.0
b6e73000-b6e7d000 rw-p 000bf000 03:01 6857258    /usr/lib/libmythlivemedia-0.21.so.0.21.0
b6e7d000-b6e8b000 rw-p b6e7d000 00:00 0 
b6e8b000-b6f23000 r-xp 00000000 03:01 6857267    /usr/lib/libmythupnp-0.21.so.0.21.0
b6f23000-b6f25000 rw-p 00098000 03:01 6857267    /usr/lib/libmythupnp-0.21.so.0.21.0
b6f25000-b6fa4000 r-xp 00000000 03:01 6857257    /usr/lib/libmythfreemheg-0.21.so.0.21.0
b6fa4000-b6fab000 rw-p 0007e000 03:01 6857257    /usr/lib/libmythfreemheg-0.21.so.0.21.0
b6fab000-b730c000 r-xp 00000000 03:01 6857095    /usr/lib/libmythavcodec-0.21.so.0.21.0
b730c000-b731a000 rw-p 00361000 03:01 6857095    /usr/lib/libmythavcodec-0.21.so.0.21.0
b731a000-b741a000 rw-p b731a000 00:00 0 
b741a000-b7423000 r-xp 00000000 03:01 6857255    /usr/lib/libmythavutil-0.21.so.0.21.0
b7423000-b7424000 rw-p 00008000 03:01 6857255    /usr/lib/libmythavutil-0.21.so.0.21.0
b7424000-b7427000 rw-p b7424000 00:00 0 
b7427000-b74a8000 r-xp 00000000 03:01 6857251    /usr/lib/libmythavformat-0.21.so.0.21.0
b74a8000-b74af000 rw-p 00080000 03:01 6857251    /usr/lib/libmythavformat-0.21.so.0.21.0
b74af000-b74b3000 rw-p b74af000 00:00 0 
b74b3000-b7eac000 r-xp 00000000 03:01 6857259    /usr/lib/libmythtv-0.21.so.0.21.0
b7eac000-b7ee1000 rw-p 009f8000 03:01 6857259    /usr/lib/libmythtv-0.21.so.0.21.0
b7ee1000-b7ee5000 rw-p b7ee1000 00:00 0 
b7ee6000-b7ef3000 r-xp 00000000 03:01 6905867    /usr/lib/qt3/plugins/sqldrivers/libqsqlmysql.so
b7ef3000-b7ef4000 rw-p 0000c000 03:01 6905867    /usr/lib/qt3/plugins/sqldrivers/libqsqlmysql.so
b7ef4000-b7ef5000 rw-p b7ef4000 00:00 0 
b7ef5000-b7ef7000 rwxp 00000000 00:0e 969        /dev/zero
b7ef7000-b7ef9000 rw-p b7ef7000 00:00 0 
b7ef9000-b7efa000 r-xp b7ef9000 00:00 0          [vdso]
b7efa000-b7f14000 r-xp 00000000 03:01 3317772    /lib/ld-2.7.so
b7f14000-b7f16000 rw-p 00019000 03:01 3317772    /lib/ld-2.7.so
bfda0000-bfdb5000 rwxp bffeb000 00:00 0          [stack]
2009-03-28 04:01:10.126 TFW, Error: Write() -- IOBOUND end
2009-03-28 04:01:09.724 Connected to database 'mythconverg' at host: 192.168.1.138
2009-03-28 04:01:10.126 TFW, Error: Write() -- IOBOUND end
2009-03-28 04:01:10.132 Current Schema Version: 1214
2009-03-28 04:01:13.030 AFD: Opened codec 0x829e350, id(MPEG2VIDEO) type(Video)
2009-03-28 04:01:13.039 AFD: codec MP2 has 2 channels
2009-03-28 04:01:13.040 AFD: Opened codec 0x829e7c0, id(MP2) type(Audio)
2009-03-28 04:01:14.782 Preview: Grabbed preview '/var/lib/mythtv/recordings/1269_20090328030001.mpg' 720x480@64s
```

---

### Post by iponeverything on 2009-03-28
check/repair the database . 


Stop the backend then run:
mysqlcheck --check -u mythtv -pmythtv mythconverg
mysqlcheck --repair -u mythtv -pmythtv mythconverg

---

