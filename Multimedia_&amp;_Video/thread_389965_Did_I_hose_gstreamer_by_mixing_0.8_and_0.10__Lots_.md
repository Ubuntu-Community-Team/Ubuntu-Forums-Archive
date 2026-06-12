---
title: "Did I hose gstreamer by mixing 0.8 and 0.10?  Lots of problems that may be related"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by RichardBronosky on 2007-03-21
I'm starting to realize that one of the biggest problems that we face as a community is the validity of documentation/suggestions/comments versus versions and distributions.  But, I'd want to get into that here.

1. Is it bad to mix GS 0.8 and GS 0.10 on Ubuntu Edgy?

I started by trying to rip a CD to MP3s to put on my wife's iPod.  I've tried EasyUbuntu.  I've added dozens of packages based on over a weeks worth of following forum/ml threads.  I followed the notes in the help file.  I've tried half a dozen different pipelines in sound juicer.  When I try to rip to MP3, the app (SJ or Rhythm Box) freezes and must be killed.

Now I find that I can't play MP4 videos either.

Here is what I get from trying an MP4

```
rbronosky@IT-f1-rbronosky-p:~/misc/Video$ gmplayer SANY0177.MP4 
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2400  @ 1.83GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing /home/rbronosky/misc/Video/SANY0177.MP4.
ISO: File Type Major Brand: ISO/IEC 14496-1 (MPEG-4 system) v2
Quicktime/MOV file format detected.
VIDEO:  [mp4v]  1280x720  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)

rbronosky@IT-f1-rbronosky-p:~/misc/Video$ mplayer SANY0177.MP4 
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2400  @ 1.83GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing SANY0177.MP4.
ISO: File Type Major Brand: ISO/IEC 14496-1 (MPEG-4 system) v2
Quicktime/MOV file format detected.
VIDEO:  [mp4v]  1280x720  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

```

Here is a list of the gstreamer related stuff I have installed:
```
rbronosky@IT-f1-rbronosky-p:~/misc/Video$ apt-cache --installed search gstreamer
gnome-media - GNOME media utilities
gstreamer0.10-alsa - GStreamer plugin for ALSA
gstreamer0.10-doc - GStreamer core documentation and manuals
gstreamer0.10-esd - GStreamer plugin for ESD
gstreamer0.10-gnomevfs - GStreamer plugin for GnomeVFS
gstreamer0.10-plugins-base - GStreamer plugins from the "base" set
gstreamer0.10-plugins-base-apps - GStreamer helper programs from the "base" set
gstreamer0.10-plugins-base-dbg - GStreamer plugins from the "base" set
gstreamer0.10-plugins-base-doc - GStreamer documentation for plugins from the "base" set
gstreamer0.10-plugins-good - GStreamer plugins from the "good" set
gstreamer0.10-plugins-good-dbg - GStreamer plugins from the "good" set
gstreamer0.10-plugins-good-doc - GStreamer documentation for plugins from the "good" set
gstreamer0.10-tools - Tools for use with GStreamer
gstreamer0.10-x - GStreamer plugins for X11 and Pango
juk - music organizer and player for KDE
libgstreamer-plugins-base0.10-0 - GStreamer libraries from the "base" set
libgstreamer-plugins-base0.10-dev - GStreamer development files for libraries from the "base" set
libgstreamer0.10-0 - Core GStreamer libraries and elements
libgstreamer0.10-0-dbg - Core GStreamer libraries and elements
libgstreamer0.10-dev - GStreamer core development files
python-gst0.10 - generic media-playing framework (Python bindings)
serpentine - an application for mastering audio CD
goobox - CD player and ripper for GNOME
gstreamer-editor - GStreamer Pipeline Editor and other GUI tools
gstreamer-tools - Tools for use with GStreamer
gstreamer0.10-ffmpeg - FFmpeg plugin for GStreamer
gstreamer0.10-fluendo-mp3 - Fluendo mp3 decoder GStreamer plugin
gstreamer0.10-fluendo-mpegdemux - Fluendo GStreamer plugin for MPEG2 demuxing
gstreamer0.10-gl - GStreamer plugin for OpenGL output
gstreamer0.10-gnonlin - non-linear editing module for GStreamer
gstreamer0.10-gnonlin-dev - development files of the non-linear editing module for GStreamer
gstreamer0.10-plugins-bad - GStreamer plugins from the "bad" set
gstreamer0.10-plugins-bad-dbg - GStreamer plugins from the "bad" set
gstreamer0.10-plugins-bad-doc - GStreamer documentation for plugins from the "bad" set
gstreamer0.10-plugins-farsight - plugins for Gstreamer for Audio/Video conferencing
gstreamer0.10-plugins-ugly - GStreamer plugins from the "ugly" set
gstreamer0.10-plugins-ugly-dbg - GStreamer plugins from the "ugly" set
gstreamer0.10-plugins-ugly-doc - GStreamer documentation for plugins from the "ugly" set
gstreamer0.10-sdl - GStreamer plugin for SDL output
gstreamer0.8-a52dec - ATSC A/52 audio decoder plugin for GStreamer
gstreamer0.8-aa - AA-lib plugin for GStreamer
gstreamer0.8-alsa - ALSA plugin for GStreamer
gstreamer0.8-artsd - aRtsd plugin for GStreamer
gstreamer0.8-audiofile - AudioFile plugin for GStreamer
gstreamer0.8-caca - Colour AsCii Art library plugin for GStreamer
gstreamer0.8-cdio - low-level CD-ROM reading and control plugin for GStreamer
gstreamer0.8-cdparanoia - cdparanoia plugin for GStreamer
gstreamer0.8-doc - GStreamer documentation
gstreamer0.8-dv - DV plugin for GStreamer
gstreamer0.8-dvd - DVD plugin for GStreamer
gstreamer0.8-esd - Enlightened Sound Daemon plugin for GStreamer
gstreamer0.8-festival - Festival speech synthesis plugin for GStreamer
gstreamer0.8-ffmpeg - FFmpeg plugin for GStreamer
gstreamer0.8-flac - FLAC plugin for GStreamer
gstreamer0.8-gnomevfs - Gnome VFS plugin for GStreamer
gstreamer0.8-gsm - GSM plugin for GStreamer
gstreamer0.8-gtk - Gtk/Gdk plugin for GStreamer
gstreamer0.8-hermes - colorspace conversion plugin for GStreamer based on hermes
gstreamer0.8-jpeg - JPEG plugin for GStreamer
gstreamer0.8-mad - MAD MPEG audio decoder plugin for GStreamer
gstreamer0.8-mikmod - MikMod decoder plugin for GStreamer
gstreamer0.8-misc - Collection of various GStreamer plugins
gstreamer0.8-mms - mms plugin for GStreamer
gstreamer0.8-mpeg2dec - MPEG1 and MPEG2 video decoder plugin for GStreamer
gstreamer0.8-musepack - Musepack (MPC) audio decoder plugin for GStreamer
gstreamer0.8-oss - OSS plugin for GStreamer
gstreamer0.8-plugin-apps - Simple GStreamer applications
gstreamer0.8-plugins - All GStreamer plugins
gstreamer0.8-sdl - SDL videosink plugin for GStreamer
gstreamer0.8-sid - C64 SID decoder plugin for GStreamer
gstreamer0.8-speex - Speex plugin for GStreamer
gstreamer0.8-swfdec - SWF (Macromedia Flash) decoder plugin for GStreamer
gstreamer0.8-theora - Theora plugin for GStreamer
gstreamer0.8-tools - Tools for use with GStreamer
gstreamer0.8-vorbis - Vorbis plugin for GStreamer
gstreamer0.8-x - X videosink plugin for GStreamer
libglib-cil - CLI binding for the GLib utility library
libgstreamer-gconf0.8-0 - GConf support for GStreamer
libgstreamer-gconf0.8-dev - Development files for GConf support for GStreamer
libgstreamer-perl - Perl interface to the gstreamer media processing framework
libgstreamer-plugins0.8-0 - Various GStreamer libraries and library plugins
libgstreamer-plugins0.8-dev - Development files for various GStreamer library and library plugins
libgstreamer0.8-0 - Core GStreamer libraries, plugins, and utilities
libgstreamer0.8-dev - GStreamer development libraries and headers
libgstreamer0.8-ruby - GStreamer 0.8 bindings for the Ruby language
libgtksourceview1-ruby - GTKSourceView bindings for the Ruby language
pitivi - non-linear audio/video editor using GStreamer
python-gst - generic media-playing framework (Python bindings)
swf-player - Mozilla plugin for SWF files (Macromedia Flash)
tap-plugins - Tom's Audio Processing LADSPA plugins
telepathy-stream-engine - stream handler for the Telepathy framework
thoggen - DVD backup utility based on GStreamer and Gtk+
gstreamer0.10-plugins-bad-multiverse - GStreamer plugins from the "bad" set (Multiverse Variant)
gstreamer0.10-plugins-bad-multiverse-dbg - GStreamer plugins from the "ugly" set (Multiverse Variant)
gstreamer0.10-plugins-ugly-multiverse - GStreamer plugins from the "ugly" set (Multiverse Variant)
gstreamer0.10-plugins-ugly-multiverse-dbg - GStreamer plugins from the "ugly" set (Multiverse Variant)
gstreamer0.8-dirac - Dirac decoder plugin for GStreamer
gstreamer0.8-faac - AAC encodingplugin for GStreamer
gstreamer0.8-faad - AAC decoding plugin for GStreamer
gstreamer0.8-lame - LAME encoder plugin for GStreamer
gstreamer0.8-pitfdll - DLL/QTX loader plugin for GStreamer
gstreamer0.8-plugins-multiverse - All Multiverse GStreamer plugins
gstreamer0.8-xvid - XVID encoder plugin for GStreamer
openoffice.org - OpenOffice.org Office suite version 2.0
totem-gstreamer - A simple media player for the Gnome desktop based on gstreamer
totem-mozilla - Totem Mozilla plugin
soundconverter - convert sound files to other formats
gstreamer0.10-pitfdll - Win32 DLL plugin for GStreamer

```

---

### Post by nlvivar on 2007-04-14
I am having the same problems. I have removed all the gstreamer0.8s with aptitude. My problem may even be worse, since my system now hangs when I try to use sound juicer to play+rip audio CDs.

Thanks. -Noel

---

