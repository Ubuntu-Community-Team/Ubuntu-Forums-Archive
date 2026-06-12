---
title: "Videos keep crashing"
date: 2009-02-20
forum: Multimedia Software
---

### Post by kidux on 2009-02-20
I've got VLC installed, along with Totem. I've also installed the gstreamer plugins. Every time I try to play a video, be it wmv, avi, or mpg, both VLC and Totem crash. Here's the output from the terminal:
```
keith@7of9:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84
keith@7of9:~$ totem
** (totem:16449): DEBUG: Init of Python module
** (totem:16449): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:16449): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:16449): DEBUG: Creating Python plugin instance
** (totem:16449): DEBUG: Init of Python module
** (totem:16449): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:16449): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:16449): DEBUG: Creating Python plugin instance
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 52 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
keith@7of9:~$
```

---

### Post by Dies on 2009-02-20
If you're running Compiz or "Desktop Effects" turn them off then try again.

If not, then please post your specs, especially graphics hardware and driver in use.

---

### Post by kidux on 2009-02-20
> **Dies said:**
> If you're running Compiz or "Desktop Effects" turn them off then try again.

If not, then please post your specs, especially graphics hardware and driver in use.
That did it, but now I need to figure out what the problem is with the desktop effects.

Toshiba Satellite specs:
AMD dual core 2.8Ghz
2GB Ram
ATI Radeon 512MB (I know, I hate ATI)
Ubuntu 8.10

---

### Post by Dies on 2009-02-20
You didn't mention what driver you're using...

That card *should* be able to handle Compiz and quite a few vids going at the same time just fine. 

Are you using the ATI driver?

and if so are there any options in xorg.conf.

---

### Post by kidux on 2009-02-20
I'm a moron, lol! I thought I had the proprietary driver installed, but it wasn't. I enabled it, and videos play now, but the videos sort of "flash" during playback, like the refresh rate is off or something. It's set at 60mhz, and I can't change it. Here's my xorg.conf:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

---

### Post by Dies on 2009-02-20
Run in a terminal

```
gstreamer-properties
```

in the window that opens up click on the video tab, then under default output in the plugin combo box test the different options.

If you're lucky you'll find one that will work fine, probably the (No Xv) one. Yeah, that kind of sucks but still at least your videos will play fine with Compiz enabled.

---

### Post by kidux on 2009-02-20
Thanks man, that did it!

---

