---
title: "Sound and MCE Remote Problems after install"
date: 2009-02-13
forum: Mythbuntu
---

### Post by Silvermage on 2009-02-13
Hi everyone!

I have some problems with my Mythbuntu installation. I've installed it on my older box and plugged into a generic 32' LCD with DVI HDMI cable.

First of all hardware:
```

AMD 2000 XP+
1 GB Ram
160 GB IDE HD
Creative SoundBlaster Audigy LS
MCE Remote (Philips eHome with colored buttons at the bottom)
Creative SBS Analog 5.1 Speaker set. (Sorry I cannot remember the model number.)
32' Generic LCD TV (HD Ready)
nVidia GeForce FX 5500

```

```

Ubuntu Version: Intrepid
mythtv-common:  Installed: 0.21.0+fixes18722-0ubuntu1

```

My problems are;
**1-** I cannot get the 5.1 sound while using xine/vlc/mplayer. I also have the same problem while running them from desktop, but I hear the sound correctly when running:
```

speaker-test -Dplug:surround51 -t wav -c6

```

mplayer command used in MythTv is:
```

mplayer -ao esd,jack,alsa,oss, -framedrop -fs -zoom -channels 6 -quiet -vo xv  -subcp latin5 %s -subfont-text-scale 3 -aspect 16:9

```

Also, SPDIF is muted in alsamixer.

**2-** My MCE Remote works ok, but I cannot use the Volume Keys while using the Music Player. When I press them, Volume Bar goes up and down, but has no effect on volume. Volume keys are working for mplayer.


```

root@mythbuntu:~# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

conf file for MCE Remote is default:
/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

But I've made an addition as below (For using the PC shutdown)

```

root@mythbuntu:~# cat ~/.lircrc
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa
include ~/.lirc/ms_special_config

root@mythbuntu:~# cat  ~/.lirc/ms_special_config
begin
        button = Power
        prog = irexec
        repeat = 0
        config = sudo /sbin/shutdown -h now
end

```

**3- **Using this DVD Player command:
```

xterm -geometry 1x1-0-0 -e xine -phfq -D --no-splash -s DVD

```
After exiting xine, MythTv frontend disappears and does not come back. I had a problem with Xine once and found that command somewhere that I can not remember.


I'm adding some logs and common commands below. If you need more logs, kindly please let me know. Any help is welcome. Thanks already.


mythfrontend.log - snippet
```

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2000+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.

Playing /var/lib/mythtv/videos/Dizi/Devekusu Kabare/Deliler2/DK.Deliler.1.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  512x384  12bpp  25.000 fps  1119.5 kbps (136.7 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
[AO ESD] esd_open_sound failed: Connection timed out
[JACK] cannot open server
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 512 x 384 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 512x384 => 682x384 Planar YV12  [fs] [zoom]

GNOME screensaver enabled

Exiting... (Quit)
2009-02-13 21:48:31.548 XMLParse::LoadTheme using /usr/share/mythtv/themes/default-wide/music-ui.xml
2009-02-13 21:48:32.962 Opening audio device '/dev/dsp'. ch 6(2) sr 44100
2009-02-13 21:48:32.962 Opening OSS audio device '/dev/dsp'.
Unable to open mixer: 'ALSA:default'
2009-02-13 22:27:04.240 XMLParse::LoadTheme using /usr/share/mythtv/themes/default-wide/video-ui.xml
MythThemedDialog.o: something is requesting a screen update of zero size. A widget probably has not done a calculateScreeArea(). Will redraw the whole screen (inefficient!).
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2000+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.

Playing /var/lib/mythtv/videos/Anime/Dragon Ball/DBZ/2-01 DBZ Saiyan Saga [RS.com]/dbz001.rmvb.
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  320x240  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: DBZ - 001 The Arrival of Raditz
 author: (DBZ-Media.nl-encodes) ~ Anakin
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Selected video codec: [rv3040] vfm: realvid (Linux RealPlayer 10 RV30/40 decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4005->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
[AO ESD] esd_open_sound failed: Connection timed out
[JACK] cannot open server
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar I420)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 426x240 Planar I420  [fs] [zoom]
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[Mixer] No hardware mixing, inserting volume filter.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
[AO_ALSA] Unable to find simple control 'PCM',0.
GNOME screensaver enabled

Exiting... (Quit)

```


lspci output

```

root@mythbuntu:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0d.0 Ethernet controller: 3Com Corporation 3CSOHO100B-TX 910-A01 [tulip] (rev 31)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

```

---

