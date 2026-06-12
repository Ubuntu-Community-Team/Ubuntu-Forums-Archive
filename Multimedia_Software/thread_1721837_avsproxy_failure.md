---
title: "avsproxy failure"
date: 2011-04-05
forum: Multimedia Software
---

### Post by kthardin on 2011-04-05
Reading through the many tutorials, all seem to agree that one can run avsproxy through wine (after the installation of avisynth) and then use avidemux to connect to it.  I continue to run into problems however.  This is the output of the error I'm receiving:

wine '/home/xxx/.wine/drive_c/Program Files/AviSynth 2.5/plugins/avsproxy.exe' '/media/xxx/test.avs'
AvsSocket Proxy, derivated from avs2yuv by  Loren Merritt Avs2YUV 0.24 ADM_1.2 
Loading Avisynth.dll 
Avisynth.dll loaded
Env created
Importing..
wine: Unhandled division by zero at address 0x40147e (thread 0030), starting debugger...
Unhandled exception: divide by zero in 32-bit code (0x0040147e).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0040147e ESP:0032f7f8 EBP:0032f860 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x0032f7f8:  951f6fe3 00403636 0041bb17 7b881ff4
0x0032f808:  00000000 00000000 00000000 00000000
0x0032f818:  00000000 00000000 0000bb80 00000002
0x0032f828:  0055c800 00000000 00000006 00000000
0x0032f838:  7b880073 0041bb17 0032f82c 100e0063
0x0032f848:  00138f98 00138f98 0032f7f8 0032f8c0
Backtrace:
=>0 0x0040147e in avsproxy (+0x147e) (0x0032f860)
  1 0x004017cd in avsproxy (+0x17cc) (0x0032f8cc)
  2 0x00200020 (0x00200020)
0x0040147e: divl        %edi,%eax
Modules:
Module  Address                 Debug info      Name (106 modules)
PE        3c0000-  3eb000       Deferred        ts
PE        3f0000-  3fc000       Deferred        mkunicode
PE        400000-  41a000       Export          avsproxy
PE        530000-  697000       Deferred        devil
PE        7b0000- 125d000       Deferred        ffms2
PE       1370000- 1393000       Deferred        ogm
PE      10000000-1017a000       Deferred        avisynth
PE      55900000-55961000       Deferred        msvcp60
ELF     7b800000-7b97b000       Deferred        kernel32<elf>
  \-PE  7b810000-7b97b000       \               kernel32
ELF     7bc00000-7bcb7000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bcb7000       \               ntdll
ELF     7bf00000-7bf04000       Deferred        <wine-loader>
ELF     7dad6000-7daf7000       Deferred        localspl<elf>
  \-PE  7dae0000-7daf7000       \               localspl
ELF     7daf7000-7db00000       Deferred        librt.so.1
ELF     7db00000-7db3c000       Deferred        libdbus-1.so.3
ELF     7db3c000-7db41000       Deferred        libgpg-error.so.0
ELF     7db41000-7db52000       Deferred        libtasn1.so.3
ELF     7db52000-7db66000       Deferred        libresolv.so.2
ELF     7db66000-7db6a000       Deferred        libkeyutils.so.1
ELF     7db6a000-7db72000       Deferred        libkrb5support.so.0
ELF     7db72000-7db96000       Deferred        libk5crypto.so.3
ELF     7db96000-7dc44000       Deferred        libkrb5.so.3
ELF     7dc44000-7dc54000       Deferred        libavahi-client.so.3
ELF     7dc54000-7dc60000       Deferred        libavahi-common.so.3
ELF     7dc60000-7dcd4000       Deferred        libgcrypt.so.11
ELF     7dcd4000-7dd6f000       Deferred        libgnutls.so.26
ELF     7dd6f000-7dd9e000       Deferred        libgssapi_krb5.so.2
ELF     7dd9e000-7dde8000       Deferred        libcups.so.2
ELF     7ddea000-7de05000       Deferred        spoolss<elf>
  \-PE  7ddf0000-7de05000       \               spoolss
ELF     7de35000-7de39000       Deferred        libcom_err.so.2
ELF     7de39000-7de70000       Deferred        winspool<elf>
  \-PE  7de40000-7de70000       \               winspool
ELF     7de70000-7e049000       Deferred        shell32<elf>
  \-PE  7de80000-7e049000       \               shell32
ELF     7e049000-7e107000       Deferred        comdlg32<elf>
  \-PE  7e050000-7e107000       \               comdlg32
ELF     7e107000-7e168000       Deferred        shlwapi<elf>
  \-PE  7e110000-7e168000       \               shlwapi
ELF     7e168000-7e1b0000       Deferred        dsound<elf>
  \-PE  7e170000-7e1b0000       \               dsound
ELF     7e1b0000-7e263000       Deferred        quartz<elf>
  \-PE  7e1c0000-7e263000       \               quartz
ELF     7e263000-7e34a000       Deferred        oleaut32<elf>
  \-PE  7e280000-7e34a000       \               oleaut32
ELF     7e360000-7e394000       Deferred        uxtheme<elf>
  \-PE  7e370000-7e394000       \               uxtheme
ELF     7e394000-7e39e000       Deferred        libxcursor.so.1
ELF     7e39e000-7e3a4000       Deferred        libxfixes.so.3
ELF     7e3a4000-7e3a8000       Deferred        libxcomposite.so.1
ELF     7e3a8000-7e3b0000       Deferred        libxrandr.so.2
ELF     7e3b0000-7e3ba000       Deferred        libxrender.so.1
ELF     7e3ba000-7e3c0000       Deferred        libxxf86vm.so.1
ELF     7e3c0000-7e3c4000       Deferred        libxinerama.so.1
ELF     7e3c4000-7e3e5000       Deferred        imm32<elf>
  \-PE  7e3d0000-7e3e5000       \               imm32
ELF     7e3e5000-7e3eb000       Deferred        libxdmcp.so.6
ELF     7e3eb000-7e405000       Deferred        libxcb.so.1
ELF     7e405000-7e40a000       Deferred        libuuid.so.1
ELF     7e40a000-7e527000       Deferred        libx11.so.6
ELF     7e527000-7e537000       Deferred        libxext.so.6
ELF     7e537000-7e550000       Deferred        libice.so.6
ELF     7e550000-7e559000       Deferred        libsm.so.6
ELF     7e576000-7e618000       Deferred        winex11<elf>
  \-PE  7e580000-7e618000       \               winex11
ELF     7e649000-7e670000       Deferred        libexpat.so.1
ELF     7e670000-7e6a0000       Deferred        libfontconfig.so.1
ELF     7e6a0000-7e6a4000       Deferred        libxau.so.6
ELF     7e6bd000-7e734000       Deferred        libfreetype.so.6
ELF     7e751000-7e7d2000       Deferred        msvcrt<elf>
  \-PE  7e760000-7e7d2000       \               msvcrt
ELF     7e7d2000-7e845000       Deferred        rpcrt4<elf>
  \-PE  7e7e0000-7e845000       \               rpcrt4
ELF     7e845000-7e943000       Deferred        ole32<elf>
  \-PE  7e860000-7e943000       \               ole32
ELF     7e943000-7ea2d000       Deferred        comctl32<elf>
  \-PE  7e950000-7ea2d000       \               comctl32
ELF     7ea2d000-7ea54000       Deferred        msvfw32<elf>
  \-PE  7ea30000-7ea54000       \               msvfw32
ELF     7ea54000-7eadf000       Deferred        gdi32<elf>
  \-PE  7ea60000-7eadf000       \               gdi32
ELF     7eadf000-7ec0f000       Deferred        user32<elf>
  \-PE  7eaf0000-7ec0f000       \               user32
ELF     7ec0f000-7eca4000       Deferred        winmm<elf>
  \-PE  7ec20000-7eca4000       \               winmm
ELF     7eca4000-7eccb000       Deferred        msacm32<elf>
  \-PE  7ecb0000-7eccb000       \               msacm32
ELF     7eccb000-7ed08000       Deferred        avifil32<elf>
  \-PE  7ecd0000-7ed08000       \               avifil32
ELF     7ed08000-7ed62000       Deferred        advapi32<elf>
  \-PE  7ed10000-7ed62000       \               advapi32
ELF     7ed62000-7ed8f000       Deferred        ws2_32<elf>
  \-PE  7ed70000-7ed8f000       \               ws2_32
ELF     7ef8f000-7ef9b000       Deferred        libnss_files.so.2
ELF     7ef9b000-7efa6000       Deferred        libnss_nis.so.2
ELF     7efa6000-7efbd000       Deferred        libnsl.so.1
ELF     7efbd000-7efe3000       Deferred        libm.so.6
ELF     7efe4000-7eff9000       Deferred        libz.so.1
ELF     f7432000-f7436000       Deferred        libdl.so.2
ELF     f7436000-f7591000       Deferred        libc.so.6
ELF     f7592000-f75ab000       Deferred        libpthread.so.0
ELF     f75c0000-f75c8000       Deferred        libnss_compat.so.2
ELF     f75c8000-f7708000       Deferred        libwine.so.1
ELF     f770a000-f7728000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
        0000001c    0
        00000010    0
        0000000f    0
00000019 winedevice.exe
        0000001e    0
        0000001d    0
        0000001b    0
        0000001a    0
0000001f explorer.exe
        00000020    0
00000021 avsproxy_0eb51789.exe
        00000028    0
        00000027    0
        00000026    0
        00000025    0
0000000b avsproxy_45699f83.exe
        00000042    0
        00000016    0
        0000002a    0
        00000044    0
00000009 (D) C:\Program Files\AviSynth 2.5\plugins\avsproxy.exe
        00000035    0
        00000034    0
        00000024    0
        00000017    0
        00000030    0 <==
Backtrace:
=>0 0x0040147e in avsproxy (+0x147e) (0x0032f860)
  1 0x004017cd in avsproxy (+0x17cc) (0x0032f8cc)
  2 0x00200020 (0x00200020)

The avs file looks very similar to this:

loadplugin("C:\Program Files\AviSynth 2.5\plugins\ffms2.dll")
ffvideosource("Z:\00000.MTS")
ffaudiosource("Z:\00000.MTS")

Any ideas?

---

