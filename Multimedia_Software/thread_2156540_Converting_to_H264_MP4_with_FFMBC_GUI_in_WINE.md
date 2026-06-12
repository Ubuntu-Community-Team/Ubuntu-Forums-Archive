---
title: "Converting to H264 MP4 with FFMBC GUI in WINE"
date: 2013-06-22
forum: Multimedia Software
---

### Post by shaunthesheep on 2013-06-22
I am testing a Windows GUI for ffmbc called [Eyeframe Converter]("https://eyeframeconverter.wordpress.com/") in WINE on Ubuntu Studio 12.04. It is being developed by the Lightworks community to convert to Lightworks-friendly intermediate and proxy formats and also to delivery formats. It seems to be quite stable. It converts to various formats without problem (MJPEG, WebM, DVD). There is a problem with converting to H264 formats in MP4 containers.

An example is the following:

```
ffmbc.exe -i "<SourceFileName>" -f mp4 -vcodec libx264 -level 41 -refs 2 -coder 1 -subq 6 -me_range 21 -b 5120k -bt 8192k -bufsize 15000k -maxrate 16000k -g 300 -threads 8 -acodec aac -strict experimental -ar 48000 -ab 384k -y "<OutputPath><OutputFileName>.mp4"
proxy
ffmbc.exe -i "<SourceFileName>" -vf scale=iw/2:-1 -vcodec libx264 -qscale 5 -qmin 1 -vtag mp2v -acodec aac -strict experimental -ar 48000 -ab 384k -threads 8 -y "<OutputPath><OutputFileName>.mp4"

```

It throws up the  error below. Can anyone shed any light on what might be the problem?

```

Unhandled exception: page fault on read access to 0x1449a000 in 32-bit code (0x00917f18). Register dump:  CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b  EIP:00917f18 ESP:017ee870 EBP:040471bc EFLAGS:00210216(  R- --  I   -A-P- )  EAX:00000020 EBX:00000008 ECX:143ca2e0 EDX:0000002d  ESI:14499fe0 EDI:00d0a780 Stack dump: 0x017ee870:  00000000 00000000 00000000 3fd00000 0x017ee880:  00000000 99094fda 40ed4002 4146bc80 0x017ee890:  00000000 00000000 41880000 4200a248 0x017ee8a0:  00000000 e0ced400 418c3fff 3f915b00 0x017ee8b0:  3fe0ced4 99094fda 401c4002 c0a4c500 0x017ee8c0:  00000000 a9934d00 40fb4009 41009aa0 000c: sel=0067 base=00000000 limit=00000000 16-bit r-x Backtrace: =>0 0x00917f18 in ffmbc (+0x517f18) (0x040471bc) 0x00917f18: flds    0x0(%esi,%ebx,4) Modules: Module    Address            Debug info    Name (77 modules) PE      400000- 15ea000    Export          ffmbc ELF    7b800000-7ba15000    Deferred        kernel32<elf>   \-PE    7b810000-7ba15000    \               kernel32 ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>   \-PE    7bc10000-7bcc3000    \               ntdll ELF    7bf00000-7bf04000    Deferred        <wine-loader> ELF    7de73000-7dea7000    Deferred        uxtheme<elf>   \-PE    7de80000-7dea7000    \               uxtheme ELF    7dea7000-7dead000    Deferred        libxfixes.so.3 ELF    7dead000-7deb8000    Deferred        libxcursor.so.1 ELF    7e074000-7e09e000    Deferred        libexpat.so.1 ELF    7e09e000-7e0d2000    Deferred        libfontconfig.so.1 ELF    7e0d2000-7e0e2000    Deferred        libxi.so.6 ELF    7e0e2000-7e0e6000    Deferred        libxcomposite.so.1 ELF    7e0e6000-7e0ef000    Deferred        libxrandr.so.2 ELF    7e0ef000-7e0f9000    Deferred        libxrender.so.1 ELF    7e0f9000-7e0ff000    Deferred        libxxf86vm.so.1 ELF    7e0ff000-7e103000    Deferred        libxinerama.so.1 ELF    7e103000-7e125000    Deferred        imm32<elf>   \-PE    7e110000-7e125000    \               imm32 ELF    7e125000-7e12c000    Deferred        libxdmcp.so.6 ELF    7e12c000-7e130000    Deferred        libxau.so.6 ELF    7e130000-7e151000    Deferred        libxcb.so.1 ELF    7e151000-7e157000    Deferred        libuuid.so.1 ELF    7e157000-7e171000    Deferred        libice.so.6 ELF    7e171000-7e2a5000    Deferred        libx11.so.6 ELF    7e2a5000-7e2b7000    Deferred        libxext.so.6 ELF    7e2b7000-7e2c0000    Deferred        libsm.so.6 ELF    7e2c0000-7e353000    Deferred        winex11<elf>   \-PE    7e2d0000-7e353000    \               winex11 ELF    7e353000-7e369000    Deferred        libz.so.1 ELF    7e369000-7e403000    Deferred        libfreetype.so.6 ELF    7e41b000-7e44d000    Deferred        ws2_32<elf>   \-PE    7e420000-7e44d000    \               ws2_32 ELF    7e44d000-7e4b7000    Deferred        shlwapi<elf>   \-PE    7e460000-7e4b7000    \               shlwapi ELF    7e4b7000-7e6c8000    Deferred        shell32<elf>   \-PE    7e4c0000-7e6c8000    \               shell32 ELF    7e6c8000-7e6dc000    Deferred        psapi<elf>   \-PE    7e6d0000-7e6dc000    \               psapi ELF    7e6dc000-7e769000    Deferred        msvcrt<elf>   \-PE    7e6f0000-7e769000    \               msvcrt ELF    7e769000-7e861000    Deferred        comctl32<elf>   \-PE    7e770000-7e861000    \               comctl32 ELF    7e861000-7e88c000    Deferred        msvfw32<elf>   \-PE    7e870000-7e88c000    \               msvfw32 ELF    7e88c000-7e901000    Deferred        rpcrt4<elf>   \-PE    7e8a0000-7e901000    \               rpcrt4 ELF    7e901000-7ea09000    Deferred        ole32<elf>   \-PE    7e920000-7ea09000    \               ole32 ELF    7ea09000-7ea22000    Deferred        version<elf>   \-PE    7ea10000-7ea22000    \               version ELF    7ea22000-7ea82000    Deferred        advapi32<elf>   \-PE    7ea30000-7ea82000    \               advapi32 ELF    7ea82000-7eb3f000    Deferred        gdi32<elf>   \-PE    7ea90000-7eb3f000    \               gdi32 ELF    7eb3f000-7ec7f000    Deferred        user32<elf>   \-PE    7eb50000-7ec7f000    \               user32 ELF    7ec7f000-7ed2c000    Deferred        winmm<elf>   \-PE    7ec90000-7ed2c000    \               winmm ELF    7ed2c000-7ed54000    Deferred        msacm32<elf>   \-PE    7ed30000-7ed54000    \               msacm32 ELF    7ed54000-7ed95000    Deferred        avifil32<elf>   \-PE    7ed60000-7ed95000    \               avifil32 ELF    7ed95000-7eda2000    Deferred        libnss_files.so.2 ELF    7eda2000-7edbc000    Deferred        libnsl.so.1 ELF    7efbc000-7efe8000    Deferred        libm.so.6 ELF    7efeb000-7f000000    Deferred        avicap32<elf>   \-PE    7eff0000-7f000000    \               avicap32 ELF    f7438000-f743d000    Deferred        libdl.so.2 ELF    f743d000-f75e6000    Deferred        libc.so.6 ELF    f75e7000-f7602000    Deferred        libpthread.so.0 ELF    f7603000-f760f000    Deferred        libnss_nis.so.2 ELF    f760f000-f7618000    Deferred        libnss_compat.so.2 ELF    f761a000-f775c000    Dwarf           libwine.so.1 ELF    f775e000-f7780000    Deferred        ld-linux.so.2 ELF    f7780000-f7781000    Deferred        [vdso].so Threads: process  tid      prio (all id:s are in hex) 0000000e services.exe     0000001f    0     0000001e    0     00000015    0     00000010    0     0000000f    0 00000012 winedevice.exe     0000001c    0     00000019    0     00000014    0     00000013    0 0000001a plugplay.exe     00000020    0     0000001d    0     0000001b    0 00000034 explorer.exe     00000035    0 00000036 EyeFrame.exe     00000040    0     0000003a    0     00000039    0     00000037    0 0000003e (D) C:\Program Files (x86)\EyeFrame Converter\ffmbc.exe     0000002a    0     00000028   -2     00000029   -2     00000018   -2     00000017   -2     00000009   -2     0000000d   -2     0000000b    0     00000047    0     00000046    0     00000045    0     00000044    0     00000043    0     00000042    0     00000041    0     0000003f    0 <== System information:     Wine build: wine-1.4     Platform: i386 (WOW64)     Host system: Linux     Host version: 3.2.0-48-lowlatency 
```

---

### Post by Merrattic on 2013-06-22
Have you tried a much simpler conversion command to see if that works to h264? 
If so you could slowly build til you find the option causing the problem. 
Can you convert with the same command under linux?

---

### Post by shaunthesheep on 2013-06-22
Thanks for the advice. I will give it a whirl. Thing is that at least two other Ubuntu testers (one using Ubuntu 12.04) are able to do the conversion without error. Does the error message give any indication why my machine is throwing up the error?

---

### Post by FakeOutdoorsman on 2013-06-22
Did you come up with these commands, or are they presets or something from the GUI?

---

### Post by Merrattic on 2013-06-22
Well I just tried it out on my machine with the same profile, running Wine on 12.04 Xubuntu, and it ran the conversion fine (albeit it turned a 17mb file into a 157mb file !). So given others are having success too it must be something with your PC/Wine configuration causing the problem or an issue with your input file?

@FODM - the profiles and command lines are built into the program.

---

