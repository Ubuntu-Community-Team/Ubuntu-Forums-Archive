---
title: "XBMC crashing on startup"
date: 2010-05-14
forum: Multimedia Software
---

### Post by Igorpan on 2010-05-14
Hi,i'm using lucid and have ATI Radeon HD 4650 1GB graphics card. I installed ATI's drivers and XBMC used to work perfectly, but now after i disabled them and activated them again i have this problem:

> igor@igor-desktop:~$ xbmc
/usr/share/themes/MurrinaLoveGray/gtk-2.0/gtkrc:50: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server "&#65533;.\"
      after 137 requests (136 known processed) with 0 events remaining.

When i start it,i see very strange image,like hundreds of rectangles with parts of images from games,applications,even parts of my Windows desktop (which is on another partition). And after 2-3 seconds,it exits.

---

### Post by polishox on 2010-05-28
Hello,

I get the same error, but XBMC runs well.
just when I stop it I have 2 processes which runs more (xbmc, xbmc.bin) and I get this
in a terminal:

[PHP]polishox@athlon6000:~$ xbmc
ALSA lib pcm.c:7245:(snd_pcm_recover) underrun occured
ALSA lib pcm.c:7245:(snd_pcm_recover) underrun occured
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server "@&#65533;`"
      after 137 requests (136 known processed) with 0 events remaining.[/PHP]And when I run xbmc as root, I get this:
[PHP]root@athlon6000:~# xbmc
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server "&#65533;|{"
      after 176 requests (175 known processed) with 0 events remaining.
*** glibc detected *** /usr/share/xbmc/xbmc.bin: corrupted double-linked list: 0x00000000017b7d60 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f306cf8c5b6]
/lib/libc.so.6(+0x77a61)[0x7f306cf8ca61]
/lib/libc.so.6(+0x7a460)[0x7f306cf8f460]
/lib/libc.so.6(cfree+0x73)[0x7f306cf92e53]
/usr/share/xbmc/xbmc.bin(_ZN15CGUIInfoManagerD1Ev+0x16d)[0x63231d]
/lib/libc.so.6(exit+0xe2)[0x7f306cf4e262]
/usr/lib/libX11.so.6(_XDefaultIOError+0x94)[0x7f306ca0e784]
/usr/lib/libX11.so.6(_XIOError+0x4e)[0x7f306ca0e7fe]
/usr/lib/libX11.so.6(+0x4a355)[0x7f306ca16355]
/usr/lib/libX11.so.6(_XReply+0x140)[0x7f306ca168f0]
/usr/lib/libX11.so.6(XSync+0x63)[0x7f306ca0a2c3]
/usr/lib/fglrx/libGL.so.1(+0x2ddb7)[0x7f3074e1fdb7]
/usr/lib/fglrx/dri/fglrx_dri.so(+0x15ab9ac)[0x7f30659e59ac]
/usr/lib/fglrx/dri/fglrx_dri.so(+0x15ac0c9)[0x7f30659e60c9]
/usr/lib/fglrx/libGL.so.1(+0x33d2d)[0x7f3074e25d2d]
/usr/lib/fglrx/libGL.so.1(+0x33d6a)[0x7f3074e25d6a]
/usr/lib/libX11.so.6(_XFreeExtData+0x15)[0x7f306c9f0295]
/usr/lib/libX11.so.6(_XFreeDisplayStructure+0x30d)[0x7f306c9fd87d]
/usr/lib/libX11.so.6(XCloseDisplay+0xdf)[0x7f306c9e8e7f]
/usr/lib/libSDL-1.2.so.0(+0x3d904)[0x7f306d800904]
/usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x42)[0x7f306d7f1da2]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x45)[0x7f306d7ca7e5]
/usr/lib/libSDL-1.2.so.0(SDL_Quit+0xe)[0x7f306d7ca87e]
/lib/libc.so.6(exit+0xe2)[0x7f306cf4e262]
/usr/share/xbmc/xbmc.bin(_ZN21CApplicationMessenger14ProcessMessageEP13ThreadMessage+0x8fb)[0x8bdabb]
/usr/share/xbmc/xbmc.bin(_ZN21CApplicationMessenger15ProcessMessagesEv+0xaa)[0x8c00aa]
/usr/share/xbmc/xbmc.bin(_ZN12CApplication7ProcessEv+0x42)[0x6c3ff2]
/usr/share/xbmc/xbmc.bin(_ZN16CXBApplicationEx3RunEv+0x3d)[0x8d667d]
/usr/share/xbmc/xbmc.bin(main+0x3da)[0x8d6e3a]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f306cf33c4d]
/usr/share/xbmc/xbmc.bin[0x5d2959]
======= Memory map: ========
00400000-00e96000 r-xp 00000000 08:02 1314762                            /usr/lib/xbmc/xbmc.bin
01096000-01099000 r--p 00a96000 08:02 1314762                            /usr/lib/xbmc/xbmc.bin
01099000-010d1000 rw-p 00a99000 08:02 1314762                            /usr/lib/xbmc/xbmc.bin
010d1000-0113f000 rw-p 00000000 00:00 0 
016f1000-02f9f000 rw-p 00000000 00:00 0                                  [heap]
7f3054000000-7f3054609000 rw-p 00000000 00:00 0 
7f3054609000-7f3058000000 ---p 00000000 00:00 0 
7f3058ffa000-7f3058ffb000 ---p 00000000 00:00 0 
7f3058ffb000-7f30597fb000 rw-p 00000000 00:00 0 
7f30597fb000-7f30597fc000 ---p 00000000 00:00 0 
7f30597fc000-7f3059ffc000 rw-p 00000000 00:00 0 
7f305c000000-7f305d368000 rw-p 00000000 00:00 0 
7f305d368000-7f3060000000 ---p 00000000 00:00 0 
7f3060020000-7f3060025000 r-xp 00000000 08:02 4555                       /lib/libnss_dns-2.11.1.so
7f3060025000-7f3060224000 ---p 00005000 08:02 4555                       /lib/libnss_dns-2.11.1.so
7f3060224000-7f3060225000 r--p 00004000 08:02 4555                       /lib/libnss_dns-2.11.1.so
7f3060225000-7f3060226000 rw-p 00005000 08:02 4555                       /lib/libnss_dns-2.11.1.so
7f3060226000-7f3060228000 r-xp 00000000 08:02 14369                      /lib/libnss_mdns4_minimal.so.2
7f3060228000-7f3060427000 ---p 00002000 08:02 14369                      /lib/libnss_mdns4_minimal.so.2
7f3060427000-7f3060428000 r--p 00001000 08:02 14369                      /lib/libnss_mdns4_minimal.so.2
7f3060428000-7f3060429000 rw-p 00002000 08:02 14369                      /lib/libnss_mdns4_minimal.so.2
7f306044d000-7f306064d000 rw-s d2a98000 00:05 4913                       /dev/ati/card0
7f306064d000-7f306064e000 ---p 00000000 00:00 0 
7f306064e000-7f3060e4e000 rw-p 00000000 00:00 0 
7f3060e4e000-7f3060e4f000 ---p 00000000 00:00 0 
7f3060e4f000-7f306164f000 rw-p 00000000 00:00 0 
7f306240d000-7f306241f000 r-xp 00000000 08:02 1972                       /usr/lib/libspeexdsp.so.1.5.0
7f306241f000-7f306261e000 ---p 00012000 08:02 1972                       /usr/lib/libspeexdsp.so.1.5.0
7f306261e000-7f306261f000 r--p 00011000 08:02 1972                       /usr/lib/libspeexdsp.so.1.5.0
7f306261f000-7f3062620000 rw-p 00012000 08:02 1972                       /usr/lib/libspeexdsp.so.1.5.0
7f3062622000-7f3062623000 ---p 00000000 00:00 0 
7f3062623000-7f3062633000 rw-p 00000000 00:00 0 
7f3062633000-7f3062634000 ---p 00000000 00:00 0 
7f3062634000-7f3062644000 rw-p 00000000 00:00 0 
7f3062644000-7f3062646000 r-xp 00000000 08:02 146065                     /usr/lib/alsa-lib/libasound_module_rate_speexrate.so
7f3062646000-7f3062845000 ---p 00002000 08:02 146065                     /usr/lib/alsa-lib/libasound_module_rate_speexrate.so
7f3062845000-7f3062846000 r--p 00001000 08:02 146065                     /usr/lib/alsa-lib/libasound_module_rate_speexrate.so
7f3062846000-7f3062847000 rw-p 00002000 08:02 146065                     /usr/lib/alsa-lib/libasound_module_rate_speexrate.so
7f306286b000-7f306286c000 ---p 00000000 00:00 0 
7f306286c000-7f306306c000 rw-p 00000000 00:00 0 
7f306317f000-7f306337f000 rw-s d2884000 00:05 4913                       /dev/ati/card0
7f3063385000-7f3063387000 r-xp 00000000 08:02 206535                     /usr/lib/gconv/ISO8859-1.so
7f3063387000-7f3063586000 ---p 00002000 08:02 206535                     /usr/lib/gconv/ISO8859-1.so
7f3063586000-7f3063587000 r--p 00001000 08:02 206535                     /usr/lib/gconv/ISO8859-1.so
7f3063587000-7f3063588000 rw-p 00002000 08:02 206535                     /usr/lib/gconv/ISO8859-1.so
7f3063588000-7f3063689000 rw-s 00320000 00:05 4913                       /dev/ati/card0
7f3063689000-7f306368b000 r-xp 00000000 08:02 193413                     /usr/lib/gconv/CP1252.so
7f306368b000-7f306388a000 ---p 00002000 08:02 193413                     /usr/lib/gconv/CP1252.so
7f306388a000-7f306388b000 r--p 00001000 08:02 193413                     /usr/lib/gconv/CP1252.so
7f306388b000-7f306388c000 rw-p 00002000 08:02 193413                     /usr/lib/gconv/CP1252.so
7f3063b27000-7f3063be2000 rw-p 00000000 00:00 0 
7f3063be2000-7f3063c10000 r-xp 00000000 08:02 1898                       /usr/lib/fglrx/libatiadlxx.so
7f3063c10000-7f3063d0f000 ---p 0002e000 08:02 1898                       /usr/lib/fglrx/libatiadlxx.so
7f3063d0f000-7f3063d16000 rw-p 0002d000 08:02 1898                       /usr/lib/fglrx/libatiadlxx.so
7f3063d3a000-7f306443a000 rw-s 00006000 00:05 4913                       /dev/ati/card0
7f306443a000-7f3065ce1000 r-xp 00000000 08:02 917781                     /usr/lib/fglrx/dri/fglrx_dri.so
7f3065ce1000-7f3065de1000 ---p 018a7000 08:02 917781                     /usr/lib/fglrx/dri/fglrx_dri.so
7f3065de1000-7f3065ee4000 rwxp 018a7000 08:02 917781                     /usr/lib/fglrx/dri/fglrx_dri.so
7f3065ee4000-7f3065fbd000 rwxp 00000000 00:00 0 
7f3065fbd000-7f3065fc9000 r-xp 00000000 08:02 4556                       /lib/libnss_files-2.11.1.so
7f3065fc9000-7f30661c8000 ---p 0000c000 08:02 4556                       /lib/libnss_files-2.11.1.so
7f30661c8000-7f30661c9000 r--p 0000b000 08:02 4556                       /lib/libnss_files-2.11.1.so
7f30661c9000-7f30661ca000 rw-p 0000c000 08:02 4556                       /lib/libnss_files-2.11.1.so
7f30661ca000-7f30661d4000 r-xp 00000000 08:02 4558                       /lib/libnss_nis-2.11.1.so
7f30661d4000-7f30663d3000 ---p 0000a000 08:02 4558                       /lib/libnss_nis-2.11.1.so
7f30663d3000-7f30663d4000 r--p 00009000 08:02 4558                       /lib/libnss_nis-2.11.1.so
7f30663d4000-7f30663d5000 rw-p 0000a000 08:02 4558                       /lib/libnss_nis-2.11.1.so
7f30663d5000-7f30663dd000 r-xp 00000000 08:02 4554                       /lib/libnss_compat-2.11.1.so
7f30663dd000-7f30665dc000 ---p 00008000 08:02 4554                       /lib/libnss_compat-2.11.1.so
7f30665dc000-7f30665dd000 r--p 00007000 08:02 4554                       /lib/libnss_compat-2.11.1.so
7f30665dd000-7f30665de000 rw-p 00008000 08:02 4554                       /lib/libnss_compat-2.11.1.so
7f30665de000-7f30665e3000 r-xp 00000000 08:02 5376                       /usr/lib/libXfixes.so.3.1.0
7f30665e3000-7f30667e2000 ---p 00005000 08:02 5376                       /usr/lib/libXfixes.so.3.1.0
7f30667e2000-7f30667e3000 r--p 00004000 08:02 5376                       /usr/lib/libXfixes.so.3.1.0
7f30667e3000-7f30667e4000 rw-p 00005000 08:02 5376                       /usr/lib/libXfixes.so.3.1.0
7f30667e4000-7f30667ed000 r-xp 00000000 08:02 5379                       /usr/lib/libXcursor.so.1.0.2
7f30667ed000-7f30669ec000 ---p 00009000 08:02 5379                       /usr/lib/libXcursor.so.1.0.2
7f30669ec000-7f30669ed000 r--p 00008000 08:02 5379                       /usr/lib/libXcursor.so.1.0.2
7f30669ed000-7f30669ee000 rw-p 00009000 08:02 5379                       /usr/lib/libXcursor.so.1.0.2
7f3066a5f000-7f3066a60000 ---p 00000000 00:00 0 
7f3066a60000-7f3066a70000 rw-p 00000000 00:00 0 
7f3066a70000-7f3066ab0000 rw-s 00010000 00:05 4913                       /dev/ati/card0
7f3066ab0000-7f3066ab1000 rw-s 00005000 00:05 4913                       /dev/ati/card0
7f3066ab1000-7f3066ac1000 rw-s fe8f0000 00:05 4913                       /dev/ati/card0
7f3066ac1000-7f3066ac3000 rw-s 0019d000 00:05 4913                       /dev/ati/card0
7f3066ac3000-7f3066ad3000 r--s 00000000 08:02 187338                     /usr/share/samba/valid.dat
7f3066ad3000-7f3066ad5000 r-xp 00000000 08:02 206443                     /usr/lib/gconv/IBM850.so
7f3066ad5000-7f3066cd4000 ---p 00002000 08:02 206443                     /usr/lib/gconv/IBM850.so
7f3066cd4000-7f3066cd5000 r--p 00001000 08:02 206443                     /usr/lib/gconv/IBM850.so
7f3066cd5000-7f3066cd6000 rw-p 00002000 08:02 206443                     /usr/lib/gconv/IBM850.so
7f3066cd6000-7f3066cd9000 r-xp 00000000 08:02 206730                     /usr/lib/gconv/UTF-16.so
7f3066cd9000-7f3066ed8000 ---p 00003000 08:02 206730                     /usr/lib/gconv/UTF-16.so
7f3066ed8000-7f3066ed9000 r--p 00002000 08:02 206730                     /usr/lib/gconv/UTF-16.so
7f3066ed9000-7f3066eda000 rw-p 00003000 08:02 206730                     /usr/lib/gconv/UTF-16.so
7f3066eda000-7f3066f19000 r--p 00000000 08:02 393461                     /usr/lib/locale/de_DE.utf8/LC_CTYPE
7f3066f19000-7f3066f1a000 r--p 00000000 08:02 395785                     /usr/lib/locale/de_DE.utf8/LC_NUMERIC
7f3066f1a000-7f3066f1b000 r--p 00000000 08:02 393906                     /usr/lib/locale/de_DE.utf8/LC_TIME
7f3066f1b000-7f3067039000 r--p 00000000 08:02 393907                     /usr/lib/locale/de_DE.utf8/LC_COLLATE/usr/bin/xbmc: Zeile 88:  3488 Aborted                 (Speicherabzug geschrieben) /usr/share/xbmc/xbmc.bin "$@"
Crash report available at /home/polishox/xbmc_crashlog-20100528_205420.log
root@athlon6000:~# [/PHP]The xbmc_crashlog:
[PHP]############## XBMC CRASH LOG ###############

################ SYSTEM INFO ################
 Date: Fr 28. Mai 21:11:55 CEST 2010
 XBMC Options: 
 Arch: x86_64
 Kernel: Linux 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010
 Release: 
    Distributor ID:    Ubuntu
    Description:    Ubuntu 10.04 LTS
    Release:    10.04
    Codename:    lucid
############## END SYSTEM INFO ##############

############### STACK TRACE #################
=====>  Core file: /home/polishox/core
        ========================================= 
[New Thread 3821]
[New Thread 3831]
Core was generated by `/usr/share/xbmc/xbmc.bin'.
Program terminated with signal 6, Aborted.
#0  0x00007f59f2011a75 in raise () from /lib/libc.so.6

Thread 2 (Thread 3831):
#0  0x00007f59f20b7f53 in poll () from /lib/libc.so.6
#1  0x00007f59f98744da in ?? () from /usr/lib/libavahi-common.so.3
#2  0x00007f59f987302e in avahi_simple_poll_run ()
   from /usr/lib/libavahi-common.so.3
#3  0x00007f59f98737ad in avahi_simple_poll_iterate ()
   from /usr/lib/libavahi-common.so.3
#4  0x00007f59f98737dd in avahi_simple_poll_loop ()
   from /usr/lib/libavahi-common.so.3
#5  0x00007f59f987432c in ?? () from /usr/lib/libavahi-common.so.3
#6  0x00007f59f6f799ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f59f20c46cd in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 1 (Thread 3821):
#0  0x00007f59f2011a75 in raise () from /lib/libc.so.6
#1  0x00007f59f20155c0 in abort () from /lib/libc.so.6
#2  0x00007f59f204b4fb in ?? () from /lib/libc.so.6
#3  0x00007f59f20555b6 in ?? () from /lib/libc.so.6
#4  0x00007f59f2055a61 in ?? () from /lib/libc.so.6
#5  0x00007f59f2058460 in ?? () from /lib/libc.so.6
#6  0x00007f59f205be53 in free () from /lib/libc.so.6
#7  0x0000000000632274 in CGUIInfoManager::~CGUIInfoManager() ()
#8  0x00007f59f2017262 in exit () from /lib/libc.so.6
#9  0x00007f59f1ad7784 in _XDefaultIOError () from /usr/lib/libX11.so.6
#10 0x00007f59f1ad77fe in _XIOError () from /usr/lib/libX11.so.6
#11 0x00007f59f1adf355 in ?? () from /usr/lib/libX11.so.6
#12 0x00007f59f1adf8f0 in _XReply () from /usr/lib/libX11.so.6
#13 0x00007f59f1ad32c3 in XSync () from /usr/lib/libX11.so.6
#14 0x00007f59f9ee8db7 in ?? () from /usr/lib/fglrx/libGL.so.1
#15 0x00007f59eaaae9ac in ?? () from /usr/lib64/dri/fglrx_dri.so
#16 0x00007f59eaaaf0c9 in ?? () from /usr/lib64/dri/fglrx_dri.so
#17 0x00007f59f9eeed2d in ?? () from /usr/lib/fglrx/libGL.so.1
#18 0x00007f59f9eeed6a in ?? () from /usr/lib/fglrx/libGL.so.1
#19 0x00007f59f1ab9295 in _XFreeExtData () from /usr/lib/libX11.so.6
#20 0x00007f59f1ac687d in _XFreeDisplayStructure () from /usr/lib/libX11.so.6
#21 0x00007f59f1ab1e7f in XCloseDisplay () from /usr/lib/libX11.so.6
#22 0x00007f59f28c9904 in ?? () from /usr/lib/libSDL-1.2.so.0
#23 0x00007f59f28bada2 in SDL_VideoQuit () from /usr/lib/libSDL-1.2.so.0
#24 0x00007f59f28937e5 in SDL_QuitSubSystem () from /usr/lib/libSDL-1.2.so.0
#25 0x00007f59f289387e in SDL_Quit () from /usr/lib/libSDL-1.2.so.0
#26 0x00007f59f2017262 in exit () from /lib/libc.so.6
#27 0x00000000008bdabb in CApplicationMessenger::ProcessMessage(ThreadMessage*)
    ()
#28 0x00000000008c00aa in CApplicationMessenger::ProcessMessages() ()
#29 0x00000000006c3ff2 in CApplication::Process() ()
#30 0x00000000008d667d in CXBApplicationEx::Run() ()
#31 0x00000000008d6e3a in main ()
############# END STACK TRACE ###############

################# LOG FILE ##################

21:11:17 T:140024189491232 M:3001655296  NOTICE: -----------------------------------------------------------------------
21:11:17 T:140024189491232 M:3001655296  NOTICE: Starting XBMC, Platform: GNU/Linux.  Built on May 23 2010 (SVN:26018)
21:11:17 T:140024189491232 M:3001655296  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
21:11:17 T:140024189491232 M:3001655296  NOTICE: special://masterprofile/ is mapped to: /home/polishox/.xbmc/userdata
21:11:17 T:140024189491232 M:3001655296  NOTICE: special://home/ is mapped to: /home/polishox/.xbmc
21:11:17 T:140024189491232 M:3001655296  NOTICE: special://temp/ is mapped to: /home/polishox/.xbmc/temp
21:11:17 T:140024189491232 M:3001655296  NOTICE: The executable running is: /usr/lib/xbmc/xbmc.bin
21:11:17 T:140024189491232 M:3001655296  NOTICE: Log File is located: /home/polishox/.xbmc/temp/xbmc.log
21:11:17 T:140024189491232 M:3001655296  NOTICE: -----------------------------------------------------------------------
21:11:18 T:140024189491232 M:3001266176  NOTICE: Setup SDL
21:11:19 T:140024189491232 M:3000385536  NOTICE: Enabled Joystick: Microsoft X-Box 360 pad
21:11:19 T:140024189491232 M:3000385536  NOTICE: load settings...
21:11:19 T:140024189491232 M:3000385536  NOTICE: special://profile/ is mapped to: special://masterprofile/
21:11:19 T:140024189491232 M:3000385536  NOTICE: loading special://masterprofile/guisettings.xml
21:11:19 T:140024189491232 M:3000385536  NOTICE: Getting hardware information now...
21:11:19 T:140024189491232 M:3000385536  NOTICE: Checking resolution 12
21:11:19 T:140024189491232 M:3000385536  NOTICE: Loading player core factory settings from special://xbmc/system/playercorefactory.xml.
21:11:19 T:140024189491232 M:3000385536  NOTICE: Loaded playercorefactory configuration
21:11:19 T:140024189491232 M:3000385536  NOTICE: Loading player core factory settings from special://masterprofile/playercorefactory.xml.
21:11:19 T:140024189491232 M:3000385536  NOTICE: special://masterprofile/playercorefactory.xml does not exist. Skipping.
21:11:19 T:140024189491232 M:3000385536  NOTICE: No advancedsettings.xml to load (special://masterprofile/advancedsettings.xml)
21:11:19 T:140024189491232 M:3000385536  NOTICE: Default DVD Player: dvdplayer
21:11:19 T:140024189491232 M:3000385536  NOTICE: Default Video Player: dvdplayer
21:11:19 T:140024189491232 M:3000385536  NOTICE: Default Audio Player: paplayer
21:11:19 T:140024189491232 M:3000385536  NOTICE: special://masterprofile/sources.xml
21:11:19 T:140024189491232 M:2987147264  NOTICE: Using fbConfig[0]
21:11:20 T:140024189491232 M:2985115648  NOTICE: GL_VENDOR = ATI Technologies Inc.
21:11:20 T:140024189491232 M:2985115648  NOTICE: GL_RENDERER = ATI Radeon HD 4800 Series
21:11:20 T:140024189491232 M:2985115648  NOTICE: GL_VERSION = 3.2.9756 Compatibility Profile Context
21:11:20 T:140024189491232 M:2985115648  NOTICE: GL_EXTENSIONS = GL_AMDX_name_gen_delete GL_AMDX_vertex_shader_tessellator GL_AMD_conservative_depth GL_AMD_draw_buffers_blend GL_AMD_performance_monitor GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_AMD_texture_cube_map_array GL_AMD_texture_texture4 GL_AMD_vertex_shader_tessellator GL_ARB_color_buffer_float GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_seamless_cube_map GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_snorm GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_buffer GL_EXT_copy_texture GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_buffer_object_rgb32 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_explicit_multisample GL_NV_primitive_restart GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays GL_WIN_swap_hint WGL_EXT_swap_control
21:11:20 T:140024189491232 M:2985115648   ERROR: GLX: Same window as before, refreshing context
21:11:20 T:140024189491232 M:2984304640  NOTICE: UDisks: Added /media/500GB
21:11:20 T:140024189491232 M:2984304640  NOTICE: UDisks: Added /media/win7_x64
21:11:20 T:140024189491232 M:2984304640  NOTICE: start dvd mediatype detection
21:11:20 T:140024189491232 M:2984177664  NOTICE: initializing playlistplayer
21:11:20 T:140024189491232 M:2984177664  NOTICE: DONE initializing playlistplayer
21:11:20 T:140024189491232 M:2984177664  NOTICE: load default skin:[PM3.HD]
21:11:20 T:140024189491232 M:2980155392   ERROR: DBus: Error org.freedesktop.DBus.Error.ServiceUnknown - The name org.freedesktop.UPower was not provided by any .service files
21:11:20 T:140024189491232 M:2980155392   ERROR: DBus: Error org.freedesktop.DBus.Error.ServiceUnknown - The name org.freedesktop.UPower was not provided by any .service files
21:11:20 T:140024189491232 M:2980155392  NOTICE: initialize done
21:11:20 T:140024189491232 M:2980155392  NOTICE: Running the application...
21:11:20 T:140024189491232 M:2974261248  NOTICE: Webserver: Starting...
21:11:20 T:140024111744784 M:2974261248  NOTICE: Webserver: Started
21:11:20 T:140024189491232 M:2973609984  NOTICE: starting upnp server
21:11:20 T:140024189491232 M:2973483008  NOTICE: starting upnp renderer
21:11:20 T:140024189491232 M:2973315072  NOTICE: ES: Starting event server
21:11:20 T:140024189491232 M:2973315072  NOTICE: DS: Starting dbus server
21:11:20 T:140023970125584 M:2972274688  NOTICE: ES: Starting UDP Event server on 127.0.0.1:9777
21:11:20 T:140023970125584 M:2972274688  NOTICE: UDP: Listening on port 9777
21:11:20 T:140024189491232 M:2972401664   ERROR:  DS: Failed to connect to the D-Bus session daemon: /bin/dbus-launch terminated abnormally without any error message
21:11:20 T:140024189491232 M:2972401664  NOTICE: starting zeroconf publishing
21:11:20 T:140024103405328 M:2967957504  NOTICE: -->Python Interpreter Initialized<--
21:11:28 T:140024189491232 M:2953388032  NOTICE: DVDPlayer: Opening: /home/polishox/Desktop/372.avi
21:11:28 T:140024189491232 M:2953388032 WARNING: CDVDMessageQueue(player)::Put MSGQ_NOT_INITIALIZED
21:11:28 T:140023942850320 M:2953388032  NOTICE: Creating InputStream
21:11:28 T:140023942850320 M:2953388032  NOTICE: Creating Demuxer
21:11:28 T:140023942850320 M:2952536064  NOTICE: Opening video stream: 0 source: 256
21:11:28 T:140023942850320 M:2952536064  NOTICE: Creating video codec with codec id: 13
21:11:28 T:140023942850320 M:2952560640  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
21:11:28 T:140023942850320 M:2952433664  NOTICE: Creating video thread
21:11:28 T:140023942850320 M:2952433664  NOTICE: Opening audio stream: 1 source: 256
21:11:28 T:140023942850320 M:2952433664  NOTICE: Finding audio codec for: 86017
21:11:28 T:140023899916048 M:2952433664  NOTICE: running thread: video_thread
21:11:28 T:140023942850320 M:2952433664  NOTICE: Creating audio thread
21:11:28 T:140023891523344 M:2952433664  NOTICE: running thread: CDVDPlayerAudio::Process()
21:11:28 T:140023891523344 M:2952458240  NOTICE: Creating audio device with codec id: 86017, channels: 2, sample rate: 48000, no pass-through
21:11:28 T:140023899916048 M:2952081408  NOTICE:  fps: 25.000000, pwidth: 640, pheight: 352, dwidth: 640, dheight: 352
21:11:28 T:140023899916048 M:2952081408  NOTICE: Display resolution DESKTOP : 1280x1024 @ 85.02 - Full Screen (12)
21:11:28 T:140024189491232 M:2946826240  NOTICE: Using GL_TEXTURE_2D
21:11:28 T:140024189491232 M:2946826240  NOTICE: GL: Selecting Single Pass YUV 2 RGB shader
21:11:29 T:140024189491232 M:2942414848  NOTICE: GL: NPOT texture support detected
21:11:36 T:140024189491232 M:2941816832   ERROR: Keymapping error: no such action 'runscript()' defined
21:11:37 T:140024189491232 M:2941825024   ERROR: Keymapping error: no such action 'runscript()' defined
21:11:43 T:140024189491232 M:2941493248  NOTICE: CDVDPlayer::CloseFile()
21:11:43 T:140024189491232 M:2941493248  NOTICE: DVDPlayer: waiting for threads to exit
21:11:43 T:140023942850320 M:2941493248  NOTICE: CDVDPlayer::OnExit()
21:11:43 T:140023942850320 M:2941493248  NOTICE: DVDPlayer: closing audio stream
21:11:43 T:140023942850320 M:2941493248  NOTICE: Closing audio stream
21:11:43 T:140023942850320 M:2941493248  NOTICE: Waiting for audio thread to exit
21:11:43 T:140023891523344 M:2941493248   ERROR: AddPackets - failed to add leftover bytes to render
21:11:43 T:140023891523344 M:2941493248  NOTICE: thread end: CDVDPlayerAudio::OnExit()
21:11:43 T:140023942850320 M:2941493248  NOTICE: Closing audio device
21:11:43 T:140023942850320 M:2941493248  NOTICE: Deleting audio codec
21:11:43 T:140023942850320 M:2941493248  NOTICE: DVDPlayer: closing video stream
21:11:43 T:140023942850320 M:2941493248  NOTICE: Closing video stream
21:11:43 T:140023942850320 M:2941493248  NOTICE: waiting for video thread to exit
21:11:43 T:140023899916048 M:2941493248  NOTICE: thread end: video_thread
21:11:43 T:140023942850320 M:2941493248  NOTICE: deleting video codec
21:11:43 T:140023942850320 M:2941493248  NOTICE: CDVDPlayer::OnExit() deleting demuxer
21:11:43 T:140023942850320 M:2941493248  NOTICE: CDVDPlayer::OnExit() deleting input stream
21:11:43 T:140024189491232 M:2941493248  NOTICE: DVDPlayer: finished waiting
21:11:43 T:140024189491232 M:2941882368  NOTICE: CDVDPlayer::CloseFile()
21:11:43 T:140024189491232 M:2941882368 WARNING: CDVDMessageQueue(player)::Put MSGQ_NOT_INITIALIZED
21:11:43 T:140024189491232 M:2941882368  NOTICE: DVDPlayer: waiting for threads to exit
21:11:43 T:140024189491232 M:2941882368  NOTICE: DVDPlayer: finished waiting
21:11:53 T:140024189491232 M:2927710208  NOTICE: Storing total System Uptime
21:11:53 T:140024189491232 M:2927710208  NOTICE: Saving settings
21:11:53 T:140024189491232 M:2927710208  NOTICE: stop all
21:11:53 T:140024189491232 M:2927710208  NOTICE: Webserver: Stopping...
21:11:53 T:140024189491232 M:2927710208  NOTICE: ES: Stopping event server
21:11:53 T:140024189491232 M:2927710208  NOTICE: stopping upnp
21:11:53 T:140023970125584 M:2927710208  NOTICE: ES: UDP Event server stopped
21:11:54 T:140024189491232 M:2927710208  NOTICE: stopping zeroconf publishing
21:11:54 T:140024189491232 M:2927775744  NOTICE: Webserver: Stopped...
21:11:54 T:140024189491232 M:2927775744  NOTICE: stop dvd detect media
21:11:54 T:140024189491232 M:2927775744  NOTICE: stop sap announcement listener
21:11:54 T:140024189491232 M:2927775744  NOTICE: clean cached files!
21:11:54 T:140024189491232 M:2927775744  NOTICE: unload skin
21:11:54 T:140024189491232 M:2927775744  NOTICE: stop python
21:11:54 T:140024189491232 M:2927775744  NOTICE: stopped
21:11:54 T:140024189491232 M:2927775744  NOTICE: destroy
21:11:54 T:140024189491232 M:2927775744  NOTICE: unload sections


############### END LOG FILE ################

############ END XBMC CRASH LOG #############
[/PHP]All this would´nt be so bad because xbmc is running well, but if I have  a XBMC-session I can´t go back to kdm because of the two processes  wich runs more.

My system: lucid lynx x64 with KDE and fluxbox.

Thanks and sorry for my bad  english.

---

