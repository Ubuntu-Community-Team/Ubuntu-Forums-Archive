---
title: "Problems running Jeskola Buzz in Wine."
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by Skully on 2006-06-29
Help with this would really be appreciated.  
I get this when I try to run the program...

*****@ubuntu:~$ cd buzz
*****@ubuntu:~/buzz$ cd Buzz
*****@ubuntu:~/buzz/Buzz$ wine buzz
fixme:ole:ITypeInfo_fnRelease destroy child objects 
fixme:ole:CoRegisterMessageFilter stub
wine: Unhandled page fault on read access to 0x0000e129 at address 0x4244cb (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x0000e129 in 32-bit code (0x004244cb).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:004244cb ESP:7fb9f978 EBP:7e6eac20 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7e6eac68 ECX:0000e125 EDX:7ffdd208
 ESI:7e706738 EDI:7df20000
Stack dump:
0x7fb9f978:  7df20000 7e6d73b8 004da818 ffffffff
0x7fb9f988:  00000000 7e7053e8 7e6fee00 7e705438
0x7fb9f998:  7e7053e8 7e7053e8 7e705348 7fda8070
0x7fb9f9a8:  7e705348 00000000 7e6f1950 7e7053e8
0x7fb9f9b8:  00000000 7e6eac68 7e6f1900 7e6eac68
0x7fb9f9c8:  00000000 7e706710 00000001 7e6eac68
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x004244cb in buzz (+0x244cb) (0x004244cb)
  2 0x7e6f3b90 (0x7e6f3b90)
  3 0x00000000 (0x00000000)
0x004244cb: movl        0x4(%ecx),%edx
Modules:
Module  Address                 Debug info      Name (102 modules)
PE      0x00400000-0061a000     Export          buzz
PE      0x10000000-10044000     Deferred        auxbus
PE      0x5f400000-5f4f2000     Deferred        mfc42
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7df20000-7df29000     Deferred        btdsys peerenv
PE      0x7df30000-7df8c000     Deferred        umwcore
PE      0x7e0b0000-7e0c3000     Deferred        machines
PE      0x7e3a0000-7e3a9000     Deferred        wo_waveout
PE      0x7e3b0000-7e3b6000     Deferred        wo_silent
PE      0x7e3c0000-7e3cf000     Deferred        wo_eaxout
ELF     0x7e3d7000-7e420000     Deferred        dsound<elf>
  \-PE  0x7e3e0000-7e420000     \               dsound
PE      0x7e420000-7e429000     Deferred        wo_directx
PE      0x7e660000-7e694000     Deferred        wo_asio
PE      0x7e6a0000-7e6a7000     Deferred        asiocfg
PE      0x7e6b0000-7e6c3000     Deferred        envelope
ELF     0x7e7eb000-7e800000     Deferred        midimap<elf>
  \-PE  0x7e7f0000-7e800000     \               midimap
ELF     0x7e93a000-7e952000     Deferred        msacm32<elf>
  \-PE  0x7e940000-7e952000     \               msacm32
ELF     0x7e952000-7ea07000     Deferred        libasound.so.2
ELF     0x7ea07000-7ea30000     Deferred        winealsa<elf>
  \-PE  0x7ea10000-7ea30000     \               winealsa
ELF     0x7ed71000-7edbd000     Deferred        libgcrypt.so.11
ELF     0x7edbd000-7edcd000     Deferred        libtasn1.so.2
ELF     0x7edcd000-7edfa000     Deferred        libcrypt.so.1
ELF     0x7edfa000-7ee63000     Deferred        libgnutls.so.12
ELF     0x7ee63000-7ee90000     Deferred        libcups.so.2
ELF     0x7eeeb000-7eeef000     Deferred        libgpg-error.so.0
ELF     0x7eefc000-7ef2d000     Deferred        uxtheme<elf>
  \-PE  0x7ef00000-7ef2d000     \               uxtheme
ELF     0x7ef2d000-7ef36000     Deferred        libxcursor.so.1
ELF     0x7ef36000-7ef52000     Deferred        imm32<elf>
  \-PE  0x7ef40000-7ef52000     \               imm32
ELF     0x7ef52000-7ef5a000     Deferred        libxrender.so.1
ELF     0x7ef5a000-7efc0000     Deferred        libgl.so.1
ELF     0x7efc0000-7f0a6000     Deferred        libx11.so.6
ELF     0x7f0a6000-7f0b3000     Deferred        libxext.so.6
ELF     0x7f0b3000-7f0cb000     Deferred        libice.so.6
ELF     0x7f0cb000-7f14e000     Deferred        winex11<elf>
  \-PE  0x7f0e0000-7f14e000     \               winex11
ELF     0x7f14e000-7f16d000     Deferred        libexpat.so.1
ELF     0x7f16d000-7f19b000     Deferred        libfontconfig.so.1
ELF     0x7f19b000-7f1af000     Deferred        libz.so.1
ELF     0x7f1af000-7f218000     Deferred        libfreetype.so.6
ELF     0x7f218000-7f2a0000     Deferred        winmm<elf>
  \-PE  0x7f220000-7f2a0000     \               winmm
PE      0x7f2a0000-7f2b1000     Deferred        sampleio
ELF     0x7f2b4000-7f345000     Deferred        oleaut32<elf>
  \-PE  0x7f2c0000-7f345000     \               oleaut32
ELF     0x7f345000-7f359000     Deferred        olepro32<elf>
  \-PE  0x7f350000-7f359000     \               olepro32
ELF     0x7f359000-7f373000     Deferred        oledlg<elf>
  \-PE  0x7f360000-7f373000     \               oledlg
ELF     0x7f373000-7f3a2000     Deferred        winspool<elf>
  \-PE  0x7f380000-7f3a2000     \               winspool
ELF     0x7f3a2000-7f464000     Deferred        comctl32<elf>
  \-PE  0x7f3b0000-7f464000     \               comctl32
ELF     0x7f464000-7f483000     Deferred        iphlpapi<elf>
  \-PE  0x7f470000-7f483000     \               iphlpapi
ELF     0x7f483000-7f4d0000     Deferred        rpcrt4<elf>
  \-PE  0x7f490000-7f4d0000     \               rpcrt4
ELF     0x7f4d0000-7f55f000     Deferred        ole32<elf>
  \-PE  0x7f4e0000-7f55f000     \               ole32
ELF     0x7f55f000-7f5b5000     Deferred        shlwapi<elf>
  \-PE  0x7f570000-7f5b5000     \               shlwapi
ELF     0x7f5b5000-7f68c000     Deferred        shell32<elf>
  \-PE  0x7f5d0000-7f68c000     \               shell32
ELF     0x7f68c000-7f727000     Deferred        comdlg32<elf>
  \-PE  0x7f690000-7f727000     \               comdlg32
ELF     0x7f7fc000-7f8ad000     Deferred        gdi32<elf>
  \-PE  0x7f810000-7f8ad000     \               gdi32
ELF     0x7f8ad000-7f9df000     Deferred        user32<elf>
  \-PE  0x7f8d0000-7f9df000     \               user32
ELF     0x7f9df000-7fa40000     Deferred        msvcrt<elf>
  \-PE  0x7f9f0000-7fa40000     \               msvcrt
PE      0x7fa40000-7fa4a000     Deferred        dsplib
ELF     0x7fa4f000-7fa90000     Deferred        advapi32<elf>
  \-PE  0x7fa60000-7fa90000     \               advapi32
ELF     0x7fba0000-7fba4000     Deferred        libxfixes.so.3
ELF     0x7fba4000-7fbab000     Deferred        libdrm.so.2
ELF     0x7fbab000-7fbb0000     Deferred        libxxf86vm.so.1
ELF     0x7fbb2000-7fbbc000     Deferred        libgcc_s.so.1
ELF     0x7fbef000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe00000-7fe03000     Deferred        libxrandr.so.2
ELF     0x7fe03000-7fe0d000     Deferred        libnss_files.so.2
ELF     0x7fe0d000-7fe16000     Deferred        libnss_nis.so.2
ELF     0x7fe16000-7fe2b000     Deferred        libnsl.so.1
ELF     0x7fe2b000-7fe34000     Deferred        libnss_compat.so.2
ELF     0x7fe34000-7fe37000     Deferred        libxau.so.6
ELF     0x7fe37000-7fe3c000     Deferred        libxxf86dga.so.1
ELF     0x7fe3c000-7fe44000     Deferred        libsm.so.6
ELF     0x7fe48000-7fe6a000     Deferred        libm.so.6
ELF     0x7fe6a000-7ff62000     Deferred        libwine_unicode.so.1
ELF     0x7ff62000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff70000-7ffe0000     \               ntdll
ELF     0xb7df8000-b7dfb000     Deferred        libdl.so.2
ELF     0xb7dfb000-b7f2a000     Deferred        libc.so.6
ELF     0xb7f2a000-b7f3c000     Deferred        libpthread.so.0
ELF     0xb7f4c000-b7f66000     Deferred        libwine.so.1
ELF     0xb7f69000-b7f7f000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\buzz\Buzz\buzz.exe
        0000000d    1
        0000000c   15
        00000009    0 <==
*****@ubuntu:~/buzz/Buzz$

Thanks.

---

### Post by Skully on 2006-06-30
Nevermind, i'm an idiot.  Problem fixed.  My fake c: drive wasn't showing up for some crazy reason, and I had some files in the wrong place.  Haha, this program actually runs faster now and crashes less than it ever did in real Windows! Awesome.

---

