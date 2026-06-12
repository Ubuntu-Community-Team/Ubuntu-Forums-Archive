---
title: "Unable to play WMA"
date: 2009-02-02
forum: Multimedia Software
---

### Post by Mizutsuki on 2009-02-02
Hello,
I have installed medibuntu, and win32codecs.
I am unable to playback WMA files.

Under totem I get this:
```
** (totem:13206): DEBUG: Init of Python module
** (totem:13206): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:13206): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:13206): DEBUG: Creating Python plugin instance
** (totem:13206): DEBUG: Init of Python module
** (totem:13206): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:13206): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:13206): DEBUG: Creating Python plugin instance

(totem:13206): GStreamer-CRITICAL **: Failed to deactivate pad typefind:sink, very bad

(totem:13206): GStreamer-CRITICAL **: 
Trying to dispose element decodebin0, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


(totem:13206): GStreamer-CRITICAL **: 
Trying to dispose element typefind, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.
```

Under mplayer I get this:
```
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.70GHz (Family: 6, Model: 13, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 01 halloween.wma.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Seek failed


Exiting... (End of file)
```

Under VLC I get this:
```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000378] main stream error: cannot pre fill buffer
```

under gxine I get this:
```
bind: No such file or directory
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/stella/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvb.channels_conf points to a non-existent location /home/stella/.xine/channels.conf
warning: configuration item media.dvd.raw_device points to a non-existent location /dev/rdvd
warning: configuration item media.dvd.css_cache_path points to a non-existent location /home/stella/.dvdcss/
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0
warning: configuration item media.video4linux.video_device points to a non-existent location /dev/video0
warning: configuration item media.wintv_pvr.device points to a non-existent location /dev/video0
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
ioctl(): Input/output error
ERROR: error reading Info sector (150)
xine-lib: warning: File is empty:: file:///home/stella/01%20halloween.wma
xine-lib: error: The xine engine failed to start.: The stream could not be opened.
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
system call fstat: Bad file descriptor
```

Sorry for including so many players, but the error messages seem nearly useless.

Is there a possibility this wma might be encrypted?  How could I find out?

Any other ideas about how I might get this playing?

Thank you.

---

### Post by redroad55 on 2009-02-02
In applications > system > administration > software sources >> in the updates tab is unsupported (backports) checked also under medibuntu in the third party tab is medibuntu present ? ..In the meantime I will check your post .. Post back with results..Best to you

---

### Post by Mizutsuki on 2009-02-02
> **redroad55 said:**
> In applications > system > administration > software sources >> in the updates tab is unsupported (backports) checked also under medibuntu in the third party tab is medibuntu present ? ..In the meantime I will check your post .. Post back with results..Best to you

Backports is not checked, medibuntu is checked, although medibuntu sources is not.

---

### Post by redroad55 on 2009-02-02
check unsupported and read this link [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")and I'll be back ..In the mean time post any results and or questions ..Best to you

---

### Post by mc4man on 2009-02-02
> Is there a possibility this wma might be encrypted

That's a possibility or there's some other problem with the file.

There's nothing in backports to resolve this

Mplayer is always your best bet in such instances, can play all wma files (excluding dma protected

The error message > Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Seek failed
is a generic mplayer error message in linux indicating a problem with the file.

Even if you didn't have w32codecs installed mplayer would at least recognize the .wma
Ex.
d> oug@doug-desktop:~$ mplayer 2.wma
MPlayer dev-SVN-r28349-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: The Song Remains the Same
 author: Led Zeppelin
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll
IMediaObject ERROR: 0x894e14d  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wma9dmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wmadmod.dll, /usr/lib/win32/wmadmod.dll, /usr/local/lib/win32/wmadmod.dll
IMediaObject ERROR: 0x894e14d  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmadmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x163.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video
Exiting... (End of file)


It's possible mediainfo will detect dma or other relevant info
The easiest for 8.10 would be to install from getdeb, there are 2 dependencies, either install them from right to left or dl all 3, put in a folder, cd to that folder and
```
sudo dpkg -i *.deb
```

[http://www.getdeb.net/search.php?keywords=mediainfo](http://www.getdeb.net/search.php?keywords=mediainfo)

---

### Post by Mizutsuki on 2009-02-02
Ok, I've figured out what's going on.  I made some error in the backup process and the files, as it turns out, are actually really all empty.  They contain zero bytes of data.  I'm horribly sorry for having wasted y'all's time.
Thank you

---

### Post by redroad55 on 2009-02-02
I'm glad you discovered your problem ..No worries..Best to you

---

