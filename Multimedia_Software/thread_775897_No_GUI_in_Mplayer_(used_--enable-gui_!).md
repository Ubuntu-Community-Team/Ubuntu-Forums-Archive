---
title: "No GUI in Mplayer (used --enable-gui !)"
date: 2008-04-30
forum: Multimedia Software
---

### Post by paziek on 2008-04-30
I have installed skin after compilation, but before installation.
Dunno if that matters.
Compiled under Hardy Heron, source downloaded yesterday from cvs.

This is ./configure output:
```
paziek@Lolita:~/src/mplayer$ ./configure --enable-gui --enable-largefiles --enable-menu --enable-pulse --prefix=/usr  --confdir=/etc/mplayer --enable-png --enable-jpeg
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.2.3, ok 
Checking for host cc ... cc 
Checking for cross compilation ... no 
Checking for CPU vendor ... AuthenticAMD (6:10:0) 
Checking for CPU type ...  AMD Athlon(tm) XP 2500+ 
Checking for kernel support of mmx ... yes 
Checking for kernel support of mmxext ... yes 
Checking for kernel support of 3dnow ... yes 
Checking for kernel support of 3dnowext ... yes 
Checking for kernel support of sse ... yes 
Checking for kernel support of cmov ... yes 
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... native 
Checking for extern symbol prefix ...  
Checking for assembler support of -pipe option ... yes 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as ) ... ok 
Checking for .align is a power of two ... no 
Checking for Linux kernel version ... 2.6.24-16-generic, ok 
Checking for -lposix ... no 
Checking for -lm ... yes 
Checking for langinfo ... yes 
Checking for language ... using en (man pages: en ) 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... __restrict 
Checking for __builtin_expect ... yes 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for llrint ... yes 
Checking for lrint ... yes 
Checking for lrintf ... yes 
Checking for round ... yes 
Checking for roundf ... yes 
Checking for mkstemp ... yes 
Checking for nanosleep ... yes 
Checking for socklib ... yes 
Checking for inet_pton() ... yes (using )
Checking for network ... yes 
Checking for inttypes.h (required) ... yes 
Checking for int_fastXY_t in inttypes.h ... yes 
Checking for word size ... 32 
Checking for malloc.h ... yes 
Checking for memalign() ... yes 
Checking for alloca.h ... yes 
Checking for byteswap.h ... yes 
Checking for mman.h ... yes 
Checking for dynamic loader ... yes 
Checking for dynamic a/v plugins support ... no 
Checking for pthread ... yes (using -lpthread)
Checking for w32threads ... no (using pthread instead)
Checking for rpath ... no 
Checking for iconv ... yes 
Checking for soundcard.h ... yes (sys/soundcard.h)
Checking for sys/dvdio.h ... no 
Checking for sys/cdio.h ... no 
Checking for linux/cdrom.h ... yes 
Checking for dvd.h ... no 
Checking for termcap ... yes (using -lncurses)
Checking for termios ... yes (sys/termios.h)
Checking for shm ... yes 
Checking for strsep() ... yes 
Checking for vsscanf() ... yes 
Checking for swab() ... yes 
Checking for POSIX select() ... yes 
Checking for gettimeofday() ... yes 
Checking for glob() ... yes 
Checking for setenv() ... yes 
Checking for sys/sysinfo.h ... yes 
Checking for pkg-config ... yes 
Checking for Samba support (libsmbclient) ... no 
Checking for tdfxfb ... no 
Checking for s3fb ... no 
Checking for tdfxvid ... no 
Checking for xvr100 ... no 
Checking for tga ... yes 
Checking for md5sum support ... yes 
Checking for bl ... no 
Checking for DirectFB ... yes (1.0.1)
Checking for X11 headers presence ... yes 
Checking for X11 ... yes 
Checking for Xss screensaver extensions ... no 
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes 
Checking for XvMC ... no 
Checking for Xinerama ... yes 
Checking for Xxf86vm ... yes 
Checking for XF86keysym ... yes 
Checking for DGA ... yes (using DGA 2.0)
Checking for 3dfx ... no 
Checking for OpenGL ... yes 
Checking for VIDIX ... yes (internal)
Checking for VIDIX PCI device name database ... yes 
Checking for /dev/mga_vid ... no 
Checking for xmga ... no 
Checking for GGI ... yes 
Checking for GGI extension: libggiwmh ... yes 
Checking for AA ... yes 
Checking for CACA ... yes 
Checking for SVGAlib ... yes 
Checking for FBDev ... yes 
Checking for DVB ... no 
Checking for DVB HEAD ... yes 
Checking for PNG support ... yes 
Checking for JPEG support ... yes 
Checking for PNM support ... yes 
Checking for GIF support ... yes 
Checking for broken giflib workaround ... disabled 
Checking for VESA support ... no 
Checking for SDL ... yes (using sdl-config)
Checking for NAS ... no 
Checking for DXR2 ... no 
Checking for DXR3/H+ ... no 
Checking for IVTV TV-Out (pre linux-2.6.24) ... no 
Checking for V4L2 MPEG Decoder ... yes 
Checking for OSS Audio ... yes 
Checking for aRts ... no 
Checking for EsounD ... no 
Checking for pulse ... yes 
Checking for JACK ... no 
Checking for OpenAL ... yes 
Checking for ALSA audio ... yes (using alsa 1.0.x and alsa/asoundlib.h)
Checking for Sun audio ... no 
Checking for VCD support ... yes 
Checking for dvdread ... yes (internal)
Checking for internal libdvdcss ... yes 
Checking for cdparanoia ... no 
Checking for libcdio ... no 
Checking for bitmap font support ... yes 
Checking for freetype >= 2.0.9 ... yes 
Checking for fontconfig ... yes 
Checking for SSA/*** support ... yes 
Checking for fribidi with charsets ... no 
Checking for ENCA ... yes 
Checking for zlib ... yes 
Checking for RTC ... yes 
Checking for liblzo2 support ... no 
Checking for mad support ... no 
Checking for Twolame ... yes 
Checking for Toolame ... no (disabled by twolame)
Checking for OggVorbis support ... yes (internal Tremor)
Checking for libspeex (version >= 1.1 required) ... no 
Checking for OggTheora support ... no 
Checking for internal mp3lib support ... yes 
Checking for internal liba52 support ... yes 
Checking for libdca support ... no 
Checking for internal libmpeg2 support ... yes 
Checking for libmpcdec (musepack, version >= 1.2.1 required) ... no 
Checking for FAAC (AAC encoder) support ... no (in libavcodec: ) 
Checking for FAAD2 (AAC) support ... yes (internal floating-point)
Checking for LADSPA plugin support ... no 
Checking for Win32 codecs ... yes (using /usr/lib/win32)
Checking for XAnim codecs ... yes (using /usr/lib/win32)
Checking for RealPlayer codecs ... yes (using /usr/lib/win32)
Checking for QuickTime codecs ... yes 
Checking for Nemesi Streaming Media libraries ... no 
Checking for LIVE555 Streaming Media libraries ... no 
Checking for FFmpeg libavutil ... yes (static)
Checking for FFmpeg libavcodec ... yes (static)
Checking for FFmpeg libavformat ... yes (static)
Checking for FFmpeg libpostproc ... yes (static)
Checking for libamr narrowband ... no 
Checking for libamr wideband ... no 
Checking for libdv-0.9.5+ ... yes 
Checking for XviD ... yes 
Checking for XviD two pass plugin ... yes 
Checking for x264 ... no (in libavcodec: no) 
Checking for libnut ... no 
Checking for zr ... no 
Checking for libmp3lame (for mencoder) ... yes 
Checking for mencoder ... yes 
Checking for fastmemcpy ... yes 
Checking for UnRAR executable ... yes 
Checking for TV interface ... yes 
Checking for DirectShow TV interface ... no 
Checking for Video 4 Linux TV interface ... yes 
Checking for Video 4 Linux 2 TV interface ... yes 
Checking for TV teletext interface ... yes 
Checking for Radio interface ... no 
Checking for Capture for Radio interface ... no 
Checking for Video 4 Linux 2 Radio interface ... no 
Checking for Video 4 Linux Radio interface ... no 
Checking for Video 4 Linux 2 MPEG PVR interface ... yes 
Checking for audio select() ... yes 
Checking for ftp ... yes 
Checking for vstream client ... no 
Checking for byte order ... little-endian 
Checking for OSD menu ... yes 
Checking for Subtitles sorting ... yes 
Checking for XMMS inputplugin support ... no 
Checking for inet6 ... yes 
Checking for gethostbyname2 ... yes 
Checking for GUI ... yes
Checking for XShape extension ... yes 
Checking for GTK+ version ... 2.12.9 
Checking for glib version ... 2.16.3 
Checking for automatic gdb attach ... no 
Checking for compiler support for noexecstack ... yes 
Checking for joystick ... no 
Checking for lirc ... no 
Checking for lircc ... no 
Checking for DVD support (libdvdnav) ... no 
Creating config.mak
Creating config.h

Config files successfully generated by ./configure --enable-gui --enable-largefiles --enable-menu --enable-pulse --prefix=/usr --confdir=/etc/mplayer --enable-png --enable-jpeg !

  Install prefix: /usr
  Data directory: /usr/share/mplayer
  Config direct.: /etc/mplayer

  Byte order: little-endian
  Optimizing for: native

  Languages:
    Messages/GUI: en
    Manual pages: en  

  Enabled optional drivers:
    Input: ftp pvr tv-teletext tv-v4l2 tv-v4l tv libdvdcss(internal) dvdread(internal) vcd dvb network 
    Codecs: xvid libdv libavcodec qtx real xanim win32 faad2 libmpeg2 liba52 mp3lib tremor(internal) twolame gif 
    Audio output: alsa openal pulse oss v4l2 sdl mpegpes(dvb) 
    Video output: v4l2 sdl gif89a pnm jpeg png mpegpes(dvb) fbdev svga caca aa ggi xvidix cvidix opengl dga xv x11 xover dfbmga directfb md5sum tga 
  Disabled optional drivers:
    Input: dvdnav vstream radio tv-dshow live555 nemesi cddb cdda smb 
    Codecs: x264 libamr_wb libamr_nb faac musepack libdca libtheora speex toolame libmad liblzo 
    Audio output: sun jack esd arts ivtv dxr2 nas 
    Video output: zr zr2 ivtv dxr3 dxr2 vesa xmga mga winvidix 3dfx xvmc bl xvr100 tdfx_vid s3fb tdfxfb 

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)

Check configure.log if you wonder why an autodetection failed (make sure
development headers/packages are installed).

NOTE: The --enable-* parameters unconditionally force options on, completely
skipping autodetection. This behavior is unlike what you may be used to from
autoconf-based configure scripts that can decide to override you. This greater
level of control comes at a price. You may have to provide the correct compiler
and linker flags yourself.
If you used one of these options (except --enable-gui and similar ones that
turn on internal features) and experience a compilation or linking failure,
make sure you have passed the necessary compiler/linker flags to configure.

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.

paziek@Lolita:~/src/mplayer$ # --- GUI stuff ---
paziek@Lolita:~/src/mplayer$ GUI_GTK = yes
bash: GUI_GTK: command not found
paziek@Lolita:~/src/mplayer$ GUI_WIN32 = 

```


Mplayer works great, but I >need< gui, as I often watch with subtitles and its a pain in the *** adding them via CLI.
Any idea why theres no gmplayer binary?

---

### Post by cor2y on 2008-04-30
Where did you extract the skins?
They mayl have to be symlinked from where you installed them to where mplayer can see them or manually moved there.
Check /etc/mplayer/mplayer.conf to see where mplayer looks for the skins

---

### Post by paziek on 2008-04-30
Nothing there.
Only config file is in my profile, and its empty anyway.
Searched for all other locations where mplayer could be, and all those folders where empty /mplayer

I don't think so that its skin isse as you can add more skins after installation, so they aren't compiled into the mplayer.

But, just in case I have skin in my profile and in /usr/local/share/mplayer/Skin
Those are both copies of extracted Blue skin.


I think that they have [dropped gui support]("http://ubuntuforums.org/showthread.php?t=558538&page=22#post4706755") as in gmplayer..

---

### Post by cor2y on 2008-04-30
No i don't think so i compiled and installed mplayer in hardy and have skin support.
I see your problem according to ./configure the prefix place where mplayer is installed is /usr/bin and not the default of /usr/local/bin so your skins should be in /usr/share/mplayer/skins you can either move the skin folder to there or create a symlink.
But remember its /usr/share/mplayer/skins not /usr/share/mplayer/Skin

---

### Post by paziek on 2008-04-30
Okay, thanks for the help.
Found some different GUI SMplayer - and its even better. Already compiled and installed.
Again, thank you for you time as it seem, I might have wasted it in vain :x

---

### Post by rvm4000 on 2008-04-30
In the last days, the mplayer developers are making changes in the makefiles and sometimes things break. I think one of the latest is that the symlink gmplayer -> mplayer is not created in the installation.

It will probably fixed soon, if not fixed yet.

---

### Post by andrew.46 on 2008-05-07
Hi,

 Saw my post quoted:

> **paziek said:**
>  I think that they have [dropped gui support]("http://ubuntuforums.org/showthread.php?t=558538&page=22#post4706755") as in gmplayer..

 Support for the gmplayer still continues while at the same time the grumbling of the developers about its inclusion continue :-) Personally I believe that guis such as smplayer are a better option. And as the program's developer mentioned here I believe the creation of the symlink is broken at the moment and a few other things while some major changes are being made.

    Andrew

---

### Post by andrew.46 on 2008-05-15
Hi,

The problem with the installation of gmplayer has been solved in [Revision 26754]("http://svn.mplayerhq.hu/mplayer?view=rev&revision=26754"). I hope you notice the identity of the person who submitted this patch :).

     Andrew

---

