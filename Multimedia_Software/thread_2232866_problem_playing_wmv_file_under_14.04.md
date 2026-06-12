---
title: "problem playing wmv file under 14.04"
date: 2014-07-04
forum: Multimedia Software
---

### Post by darkhalo2 on 2014-07-04
I recently upgraded to 14.04 64bit from 11.04 64bit, found that I have issues playing some wmv files, which I had no problem under 11.04,or under Windows
In 14.04, I have installed 
codec related: ffmpeg, libav-tools, gstreamer0.10-ffmpeg, gstreamer0.10-nice,gstreamer0.10-plugins-bad,gstreamer0.10-plugins-base,gstreamer0.10-plugins-good,gstreamer0.10-plugins-ugly,gstreamer0.10-libav, ubuntu-restricted extra, and maybe some more

players: vlc,mplayer,smplayer,totem, xbmc

Symtoms: all of smplayers, totem, mplayer, vlc's GUI crashed right away; cvlc crashed, failed to load the file; mplayer players when using command line, however, it crashed when the mouse click elsewhere. when using ffplay / avplay to play those wmv files in command line, everything work, also, xbmc could play them.

Question: Is there anyway that I could fix so that vlc,mplayer etc could play those wmv file?

Here is the result from avconv
```
$ avconv -i TEST.wmv
ffmpeg version 2.2.git-7e8fdf0 Copyright (c) 2000-2014 the FFmpeg developers
  built on Jun 26 2014 14:30:02 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-x11grab --enable-libpulse --enable-libx264 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr
  libavutil      52. 90.101 / 52. 90.101
  libavcodec     55. 68.100 / 55. 68.100
  libavformat    55. 44.100 / 55. 44.100
  libavdevice    55. 13.101 / 55. 13.101
  libavfilter     4.  9.100 /  4.  9.100
  libavresample   1.  3.  0 /  1.  3.  0
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 19.100 /  0. 19.100
  libpostproc    52.  3.100 / 52.  3.100
Guessed Channel Layout for  Input Stream #0.1 : stereo
Input #0, asf, from 'TEST.wmv':
  Metadata:
    encoder         : Lavf55.40.100
  Duration: 01:59:55.80, start: 0.000000, bitrate: 1347 kb/s
    Stream #0:0: Video: wmv2 (WMV2 / 0x32564D57), yuv420p, 800x450, SAR 1:1 DAR 16:9, 24 fps, 24 tbr, 1k tbn, 1k tbc
    Stream #0:1: Audio: wmav2 (a[1][0][0] / 0x0161), 44100 Hz, 2 channels, fltp, 48 kb/s
```

Here is the reuslt from VLC
```
$ vlc -vvvVLC media player 2.1.5 Rincewind (revision 2.1.5+ppa1)
[0x16d9058] main libvlc debug: VLC media player - 2.1.5 Rincewind
[0x16d9058] main libvlc debug: Copyright © 1996-2014 the VideoLAN team
[0x16d9058] main libvlc debug: revision 2.1.5+ppa1
[0x16d9058] main libvlc debug: configured with ./configure  '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--localstatedir=/var' '--libdir=${prefix}/lib/x86_64-linux-gnu' '--libexecdir=${prefix}/lib/x86_64-linux-gnu' '--disable-dependency-tracking' '--build=x86_64-linux-gnu' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--libdir=/usr/lib' '--sysconfdir=/etc' '--with-binary-version=' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-chromaprint' '--enable-dbus' '--enable-dca' '--enable-dirac' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-fdkaac' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libfreerdp' '--enable-libmpeg2' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-oss' '--enable-pulse' '--enable-qt' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-sftp' '--enable-shout' '--enable-skins2' '--enable-smbclient' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-decklink' '--disable-dxva2' '--disable-gnomevfs' '--disable-goom' '--disable-libvnc' '--disable-opencv' '--disable-projectm' '--disable-quicksync' '--disable-sndio' '--disable-telx' '--disable-vsxu' '--disable-wasapi' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv1394' '--enable-linsys' '--enable-omxil' '--enable-udev' '--enable-libva' '--enable-v4l2' '--enable-crystalhd' '--enable-mmx' '--enable-sse' '--disable-neon' '--disable-altivec' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'build_alias=x86_64-linux-gnu'
[0x16d9058] main libvlc debug: searching plug-in modules
[0x16d9058] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x16d9058] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x16d9058] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x16d9058] main libvlc debug: plug-ins loaded: 427 modules
[0x16d9058] main libvlc debug: opening config file (/home/myhome/.config/vlc/vlcrc)
[0x16d9058] main libvlc debug: translation test: code is "C"
[0x16d9058] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 SSE4.2 FPU 
[0x1982258] main input debug: Creating an input for 'Media Library'
[0x1982258] main input debug: Input is a meta file: disabling unneeded options
[0x1982258] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x1982258] main input debug: `file/xspf-open:///home/myhome/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/myhome/.local/share/vlc/ml.xspf'
[0x1982258] main input debug: creating demux: access='file' demux='xspf-open' location='/home/myhome/.local/share/vlc/ml.xspf' file='/home/myhome/.local/share/vlc/ml.xspf'
[0x1922d68] main demux debug: looking for access_demux module matching "file": 20 candidates
[0x1922d68] main demux debug: no access_demux modules matched
[0x1982258] main input debug: creating access 'file' location='/home/myhome/.local/share/vlc/ml.xspf', path='/home/myhome/.local/share/vlc/ml.xspf'
[0x1922188] main access debug: looking for access module matching "file": 25 candidates
[0x1922188] filesystem access debug: opening file `/home/myhome/.local/share/vlc/ml.xspf'
[0x1922188] main access debug: using access module "filesystem"
[0x1a6d298] main stream debug: Using stream method for AStream*
[0x1a6d298] main stream debug: starting pre-buffering
[0x1a6d298] main stream debug: received first data after 0 ms
[0x1a6d298] main stream debug: pre-buffering done 296 bytes in 0s - 10706 KiB/s
[0x197ace8] main stream debug: looking for stream_filter module matching "any": 9 candidates
[0x197ace8] main stream debug: no stream_filter modules matched
[0x197ace8] main stream debug: looking for stream_filter module matching "record": 9 candidates
[0x197ace8] main stream debug: using stream_filter module "record"
[0x1982258] main input debug: creating demux: access='file' demux='xspf-open' location='/home/myhome/.local/share/vlc/ml.xspf' file='/home/myhome/.local/share/vlc/ml.xspf'
[0x1924878] main demux debug: looking for demux module matching "xspf-open": 63 candidates
[0x1924878] playlist demux debug: using XSPF playlist reader
[0x1924878] main demux debug: using demux module "playlist"
[0x19125d8] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x19125d8] lua demux meta debug: Trying Lua scripts in /home/myhome/.local/share/vlc/lua/meta/reader
[0x19125d8] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x19125d8] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x19125d8] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x19125d8] main demux meta debug: no meta reader modules matched
[0x1982258] main input debug: `file/xspf-open:///home/myhome/.local/share/vlc/ml.xspf' successfully opened
[0x17acbc8] main xml reader debug: looking for xml reader module matching "any": 1 candidates
[0x17acbc8] main xml reader debug: using xml reader module "xml"
[0x1924878] playlist demux debug: parsed 0 tracks successfully
[0x1982258] main input debug: EOF reached
[0x1924878] main demux debug: removing module "playlist"
[0x197ace8] main stream debug: removing module "record"
[0x1922188] main access debug: removing module "filesystem"
[0x1a60c78] main playlist debug: creating audio output
[0x17af928] main audio output debug: looking for audio output module matching "any": 6 candidates
[0x17af928] pulse audio output debug: using library version 4.0.0
[0x17af928] pulse audio output debug:  (compiled with version 4.0.0, protocol 28)
[0x17af928] pulse audio output debug: connected locally to unix:/run/user/1000/pulse/native as client #137
[0x17af928] pulse audio output debug: using protocol 28, server protocol 28
[0x17af928] main audio output debug: using audio output module "pulse"
[0x1a60c78] main playlist debug: keeping audio output
[0x197db48] main interface debug: looking for interface module matching "hotkeys,none": 19 candidates
[0x197db48] main interface debug: using interface module "hotkeys"
[0x197cff8] main interface debug: looking for interface module matching "globalhotkeys,none": 19 candidates
[0x17af928] pulse audio output debug: adding sink 0: alsa_output.pci-0000_00_1b.0.analog-stereo (Built-in Audio Analog Stereo)
[0x197cff8] main interface debug: using interface module "globalhotkeys"
[0x17af6d8] main interface debug: looking for interface module matching "dbus,none": 19 candidates
[0x17af6d8] dbus interface debug: listening on dbus as: org.mpris.MediaPlayer2.vlc.inmyhomece22402
[0x17af6d8] main interface debug: using interface module "dbus"
[0x16d9058] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x17afd18] main interface debug: looking for interface module matching "any": 19 candidates
[0x7fa078093898] main generic debug: looking for extension module matching "any": 1 candidates
[0x7fa078093898] lua generic debug: Opening Lua Extension module
[0x7fa078093898] lua generic debug: Trying Lua scripts in /home/myhome/.local/share/vlc/lua/extensions
[0x7fa078093898] lua generic debug: Trying Lua scripts in /usr/lib/vlc/lua/extensions
[0x7fa078093898] lua generic debug: Trying Lua playlist script /usr/lib/vlc/lua/extensions/VLSub.luac
[0x7fa078093898] lua generic debug: Scanning Lua script /usr/lib/vlc/lua/extensions/VLSub.luac
[0x7fa078093898] lua generic debug: Script /usr/lib/vlc/lua/extensions/VLSub.luac has the following capability flags: 0x5
[0x7fa078093898] lua generic debug: Trying Lua scripts in /usr/share/vlc/lua/extensions
[0x7fa078093898] main generic debug: using extension module "lua"
"sni-qt/22402" WARN  11:53:06.766 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
[0x17afd18] main interface debug: using interface module "qt4"
[0x1a60c78] main playlist debug: adding item `TEST.wmv' ( file:///media/disk2/TEST.wmv )
[0x17afd18] qt4 interface debug: Adding a new MRL to recent ones: file:///media/disk2/TEST.wmv
[0x1a60c78] main playlist debug: processing request item: TEST.wmv, node: null, skip: 0
[0x1a60c78] main playlist debug: rebuilding array of current - root Playlist
[0x1a60c78] main playlist debug: rebuild done - 1 items, index 0
[0x1a60c78] main playlist debug: starting playback of the new playlist item
[0x1a60c78] main playlist debug: resyncing on TEST.wmv
[0x1a60c78] main playlist debug: TEST.wmv is at 0
[0x1a60c78] main playlist debug: creating new input thread
[0x7fa0740009b8] main input debug: Creating an input for 'TEST.wmv'
[0x7fa0740009b8] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x7fa0740009b8] main input debug: `file:///media/disk2/TEST.wmv' gives access `file' demux `' path `/media/disk2/TEST.wmv'
[0x7fa0740009b8] main input debug: creating demux: access='file' demux='' location='/media/disk2/TEST.wmv' file='/media/disk2/TEST.wmv'
[0x7fa070000958] main input debug: Creating an input for 'TEST.wmv'
[0x7fa06c000e78] main demux debug: looking for access_demux module matching "file": 20 candidates
[0x7fa06c000e78] main demux debug: no access_demux modules matched
[0x7fa0740009b8] main input debug: creating access 'file' location='/media/disk2/TEST.wmv', path='/media/disk2/TEST.wmv'
[0x7fa06c0010c8] main access debug: looking for access module matching "file": 25 candidates
[0x7fa06c0010c8] filesystem access debug: opening file `/media/disk2/TEST.wmv'
[0x7fa06c0010c8] main access debug: using access module "filesystem"
[0x7fa06c001218] main stream debug: Using stream method for AStream*
[0x7fa06c001218] main stream debug: starting pre-buffering
[0x7fa06c001218] main stream debug: received first data after 0 ms
[0x7fa06c001218] main stream debug: pre-buffering done 1024 bytes in 0s - 76923 KiB/s
[0x7fa06cc01518] main stream debug: looking for stream_filter module matching "any": 9 candidates
[0x7fa06cc01518] main stream debug: no stream_filter modules matched
[0x7fa06cc01518] main stream debug: looking for stream_filter module matching "record": 9 candidates
[0x7fa06cc01518] main stream debug: using stream_filter module "record"
[0x7fa0740009b8] main input debug: creating demux: access='file' demux='' location='/media/disk2/TEST.wmv' file='/media/disk2/TEST.wmv'
[0x7fa06cc01768] main demux debug: looking for demux module matching "asf": 63 candidates
[0x7fa06cc01518] asf stream debug: + 'Unknown'
[0x7fa06cc01518] asf stream debug: |   + 'Header'
[0x7fa06cc01518] asf stream debug: |   |   + 'File Properties'
[0x7fa06cc01518] asf stream debug: |   |   + 'Header Extension'
[0x7fa06cc01518] asf stream debug: |   |   |   + 'Metadata'
[0x7fa06cc01518] asf stream debug: |   |   + 'Extended content description'
[0x7fa06cc01518] asf stream debug: |   |   + 'Stream Properties'
[0x7fa06cc01518] asf stream debug: |   |   + 'Stream Properties'
[0x7fa06cc01518] asf stream debug: |   |   + 'Codec List'
[0x7fa06cc01518] asf stream debug: |   + 'Data'
[0x7fa06cc01518] asf stream debug: |   + 'Simple Index'
[0x7fa06cc01768] asf demux debug: found 2 streams
[0x7fa06cc01768] asf demux debug: added new video stream(ID:1)
[0x7fa0740009b8] main input debug: selecting program id=0
[0x7fa06cc01768] asf demux debug: added new audio stream(codec:0x161,ID:2)
[0x7fa06cc01768] main demux debug: using demux module "asf"
[0x7fa0740009b8] main input debug: looking for a subtitle file in /media/disk2/
[0x7fa06cc144e8] main decoder debug: looking for decoder module matching "any": 39 candidates
[0x17afd18] qt4 interface debug: IM: Setting an input
[0x7fa06cc144e8] omxil decoder debug: fmt in:WMV2, out:     
[0x7fa06cc144e8] omxil decoder debug: found 0 matching components for role video_decoder.wmv2
[0x7fa06cc144e8] omxil decoder warning: couldn't find an omx component for codec WMV2
[0x1a60c78] main playlist debug: meta ok for (null), need to fetch art
[0x7fa070c18268] main demux meta debug: looking for meta fetcher module matching "any": 1 candidates
[0x7fa06cc144e8] avcodec decoder debug: trying to use direct rendering
[0x7fa06cc144e8] avcodec decoder debug: allowing 4 thread(s) for decoding
[0x7fa06cc144e8] avcodec decoder debug: avcodec codec (Windows Media Video 8) started
[0x7fa06cc144e8] main decoder debug: using decoder module "avcodec"
[0x7fa06cc89a48] main decoder debug: looking for decoder module matching "any": 39 candidates
[0x7fa06cc89a48] avcodec decoder debug: avcodec codec (Windows Media Audio 2) started
[0x7fa06cc89a48] main decoder debug: using decoder module "avcodec"
[0x7fa06ccb2b68] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x7fa070c18268] lua demux meta debug: Trying Lua scripts in /home/myhome/.local/share/vlc/lua/meta/fetcher
[0x7fa070c18268] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[0x7fa070c18268] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[0x7fa06ccb2b68] lua demux meta debug: Trying Lua scripts in /home/myhome/.local/share/vlc/lua/meta/reader
[0x7fa06ccb2b68] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x7fa06ccb2b68] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x7fa070c18268] main demux meta debug: using meta fetcher module "lua"
[0x7fa070c18268] main demux meta debug: removing module "lua"
[0x1a60c78] main playlist debug: searching art for TEST.wmv
[0x7fa070000aa8] main art finder debug: looking for art finder module matching "any": 2 candidates
[0x7fa06ccb2b68] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x7fa06ccb2b68] main demux meta debug: no meta reader modules matched
[0x7fa0740009b8] main input debug: `file:///media/disk2/TEST.wmv' successfully opened
[0x7fa0740009b8] main input debug: Buffering 0%
[0x7fa0740009b8] main input debug: Buffering 15%
[0x7fa0740009b8] main input debug: Buffering 15%
[0x7fa0740009b8] main input debug: Buffering 29%
[0x7fa0740009b8] main input debug: Buffering 30%
[0x7fa0740009b8] main input debug: Buffering 43%
[0x7fa0740009b8] main input debug: Buffering 46%
[0x7fa0740009b8] main input debug: Buffering 56%
[0x7fa0740009b8] main input debug: Buffering 61%
[0x7fa0740009b8] main input debug: Buffering 71%
[0x7fa0740009b8] main input debug: Buffering 61%
[0x7fa06cc89a48] avcodec decoder warning: Physical channel configuration not set : guessing
[0x1a60c78] main playlist debug: reusing audio output
[0x17af928] pulse audio output debug: using stereo channel map
[0x7fa0740009b8] main input debug: Stream buffering done (324 ms in 0 ms)
[0x7fa070000aa8] lua art finder debug: Trying Lua scripts in /home/myhome/.local/share/vlc/lua/meta/art
[0x7fa054001d48] main spu text debug: looking for text renderer module matching "any": 2 candidates
[0x7fa070000aa8] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[0x7fa070000aa8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[0x7fa054001d48] freetype spu text debug: Building font databases.
[0x7fa054001d48] freetype spu text debug: Took 0 microseconds
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x17af928] pulse audio output debug: changed buffer metrics: maxlength=4194304, tlength=42336, prebuf=0, minreq=14112
[0x17af928] pulse audio output debug: connected to sink alsa_output.pci-0000_00_1b.0.analog-stereo
[0x17af928] main audio output debug: output 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
[0x7fa05c004a18] main volume debug: looking for audio volume module matching "any": 2 candidates
[0x17af928] pulse audio output debug: base volume: 65536
[0x17af928] pulse audio output debug: changing sink 0: alsa_output.pci-0000_00_1b.0.analog-stereo (Built-in Audio Analog Stereo)
[0x7fa054001d48] freetype spu text debug: Using Serif Bold as font from file /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
[0x7fa05c004a18] main volume debug: using audio volume module "float_mixer"
[0x17af928] main audio output debug: input 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
[0x7fa05c006b78] main audio filter debug: looking for audio filter module matching "scaletempo": 14 candidates
[0x7fa05c006b78] scaletempo audio filter debug: format: 44100 rate, 2 nch, 4 bps, fl32
[0x7fa05c006b78] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0x7fa05c006b78] scaletempo audio filter debug: 1.000 scale, 1323.000 stride_in, 1323 stride_out, 1059 myhomeding, 264 overlap, 617 search, 2204 queue, fl32 mode
[0x7fa05c006b78] main audio filter debug: using audio filter module "scaletempo"
[0x17af928] main audio output debug: conversion: 'f32l'->'f32l' 44100 Hz->44100 Hz Stereo->Stereo
[0x17af928] main audio output debug: conversion pipeline complete
[0x17af928] main audio output debug: conversion: 'f32l'->'f32l' 44100 Hz->44100 Hz Stereo->Stereo
[0x17af928] main audio output debug: conversion pipeline complete
[0x7fa05c00dd48] main audio resampler debug: looking for audio resampler module matching "any": 3 candidates
[0x7fa070000aa8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[0x7fa05c00dd48] main audio resampler debug: using audio resampler module "samplerate"
Segmentation fault (core dumped)
```


Result from mplayer command line
```
$ mplayer TEST.wmv MPlayer SVN-r37220 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing TEST.wmv.
libavformat version 55.37.102 (internal)
ASF file format detected.
[asfheader] Video stream found, -vid 1
[asfheader] Audio stream found, -aid 2
VIDEO:  [WMV2]  800x450  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in /media/disk1/
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 55.60.103 (internal)
Selected video codec: [ffwmv2] vfm: ffmpeg (FFmpeg WMV2/WMV8)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, floatle, 48.0 kbit/1.70% (ratio: 6000->352800)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 44100Hz 2ch floatle (4 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [x11] 800x450 => 800x450 Planar YV12 
[swscaler @ 0x7fc8c02c15c0]bicubic scaler, from yuv420p to bgra using MMXEXT
[swscaler @ 0x7fc8c02c15c0]using unscaled yuv420p -> bgra special converter
A:   3.1 V:   3.2 A-V: -0.043 ct: -0.004   2/  2 ??% ??% ??,?% 0 0 
[VD_FFMPEG] DRI failure.
A:   5.4 V:   5.4 A-V:  0.000 ct: -0.045  54/ 54  4%  4%  0.5% 0 0 




MPlayer interrupted by signal 11 in module: key_events
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by monkeybrain20122 on 2014-07-04
A sample?

---

### Post by darkhalo2 on 2014-07-04
> **monkeybrain20122 said:**
> A sample?
most test files I used was too big, but here is one of the samples that I have problem playing as well, found it on another thread
[https://archive.org/download/WorkToFishtestwmv/test_wmv.wmv](https://archive.org/download/WorkToFishtestwmv/test_wmv.wmv)

---

### Post by monkeybrain20122 on 2014-07-04
No problem playing with vlc and mpv, but not with smplayer. The difference is that I compiled mpv and vlc myself against ffmpeg while mplayer is stock install from Ubuntu's repo which is built against libav. So maybe libav for some reasons cannot play these files.

Totem works as well but I might have upgraded it with some ppa.

---

### Post by darkhalo2 on 2014-07-04
I installed all of them from various repo. 
btw, did you compile vlc from source using the preferred method "[COLOR=#000000][FONT=monospace]sudo apt-get build-dep vlc" or using the "contrib" method? and how did your compile it against ffmpeg, did you compile ffmpeg as well?[/FONT][/COLOR]

---

### Post by sudodus on 2014-07-04
It works for me to play that video clip with mplayer2 in my production system (12.04.4 LTS 32-bits).

```
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8005->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))

```

Long ago I might have added something extra beyond ubuntu-restricted-extras (I don't remember), but I suggest that you

1. Try with 

```
sudo apt-get install ubuntu-restricted-extras
```

2. If you are running a 64-bit system, try a 32-bit system (without installing into an internal drive, but installing ubuntu-restricted-extras into this live system).

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

*Edit*: Or compile your own video player as *monkeybrain*

---

### Post by darkhalo2 on 2014-07-04
> **sudodus said:**
> It works for me to play that video clip with mplayer2 in my production system (12.04.4 LTS 32-bits).

```
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8005->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))

```

Long ago I might have added something extra beyond ubuntu-restricted-extras (I don't remember), but I suggest that you

1. Try with 

```
sudo apt-get install ubuntu-restricted-extras
```

2. If you are running a 64-bit system, try a 32-bit system (without installing into an internal drive, but installing ubuntu-restricted-extras into this live system).

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

*Edit*: Or compile your own video player as *monkeybrain*
already installed ubuntu-restricted-extras, and yes, I'm using 64 bit, will have to wait later to try using 32bit in my VM.

hmm, I found out more,I could actually play those video using smplayer without crashing, the problem is that before, I was using vdpau as output driver, and after I switched to xv as output dirver , it played, and even after I switched back to vdpau , smplayer no problem playing, other players still don't work.


ps:  mplayer was removed, and replaced with mplayer2

---

### Post by sudodus on 2014-07-04
Good that you have found a way to play wmv video clips :-)

---

### Post by monkeybrain20122 on 2014-07-04
> **darkhalo2 said:**
> I installed all of them from various repo. 
btw, did you compile vlc from source using the preferred method "[COLOR=#000000][FONT=monospace]sudo apt-get build-dep vlc" or using the "contrib" method? and how did your compile it against ffmpeg, did you compile ffmpeg as well?[/FONT][/COLOR]

I installed ffmpeg and all the -dev files from
[https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa)


apt-get build-dep will not work as it will install the libav-dev files from the repo, which you don't want if you build against ffmpeg rather than avconv. So I installed a list of dependencies following andrew.46's list as baseline
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949) 

Then install the -dev files for x264, libfdk-aac etc from repo. andrew.46 compiles these for vlc-git but the repo versions are up to date enough for vlc stable release
You can add others by looking at outputs of ./configure

Then 

Download vlc release tarball, extract, cd to it and run
```
export CPPFLAGS="-I/opt/ffmpeg/include"
export LDFLAGS="-L/opt/ffmpeg/lib"
export PKG_CONFIG_PATH="/opt/ffmeg/lib/pkgconfig"
./configure --prefix=/usr
make -j4
sudo checkinstall

```

Adjust make -j4 to make -jx where x is the number of threads use.

You can also compile ffmpeg like in andrew.46's guide, but I am lazy. :)

---

### Post by darkhalo2 on 2014-07-04
> **monkeybrain20122 said:**
> I installed ffmpeg with 
[https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa)
and also all the -dev files

apt-get build-dep will not work as it will install the libav-dev files, which you don't want if you build against ffmpeg. So I installed a list of dependencies following andrew.46's list as baseline
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949) 

Then install the -dev files for x264, libfdk-aac etc from repo. andrew.46 compiles these for vlc-git but the repo versions are up to date enough for vlc stable release
You can add others by looking at outputs of ./configure

Then 

Download vlc release tarball, extract, cd to it and run
```
export CPPFLAGS="-I/opt/ffmpeg/include"
export LDFLAGS="-L/opt/ffmpeg/lib"
export PKG_CONFIG_PATH="/opt/ffmeg/lib/pkgconfig"
./configure --prefix=/usr
make -j4
sudo checkinstall

```

Adjust make -j4 to make -jx where x is the number of threads use.

You can also compile ffmpeg like in andrew.46's guide, but I am lazy. :)

thanks, I'll give it a try. I built vlc using the "apt-get build-dep" method, no wonder it didn't work.

---

### Post by monkeybrain20122 on 2014-07-04
> **darkhalo2 said:**
> thanks, I'll give it a try. I built vlc using the "apt-get build-dep" method, no wonder it didn't work.

If avconv is the reason why it didn't work. :)

---

### Post by mc4man on 2014-07-04
May be better to post debugs from your sample  - 
Re: sample & that exact vlc version -  (hardware decoding disabled in vlc for this ex.
```

 vlc -vvv '/home/doug/Videos/test_wmv.wmv' 
VLC media player 2.1.5 Rincewind (revision 2.1.5+ppa1)
...clipped configure info
[0x1280118] main libvlc debug: searching plug-in modules
[0x1280118] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x1280118] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x1280118] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x1280118] main libvlc debug: plug-ins loaded: 427 modules
[0x1280118] main libvlc debug: opening config file (/home/doug/.config/vlc/vlcrc)
[0x1280118] main libvlc debug: translation test: code is "C"
[0x1280118] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 SSE4.2 AVX AVX FPU 
[0x14887d8] main input debug: Creating an input for 'Media Library'
[0x14887d8] main input debug: Input is a meta file: disabling unneeded options
[0x14887d8] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x14887d8] main input debug: `file/xspf-open:///home/doug/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/doug/.local/share/vlc/ml.xspf'
[0x14887d8] main input debug: creating demux: access='file' demux='xspf-open' location='/home/doug/.local/share/vlc/ml.xspf' file='/home/doug/.local/share/vlc/ml.xspf'
[0x129d7e8] main demux debug: looking for access_demux module matching "file": 20 candidates
[0x129d7e8] main demux debug: no access_demux modules matched
[0x14887d8] main input debug: creating access 'file' location='/home/doug/.local/share/vlc/ml.xspf', path='/home/doug/.local/share/vlc/ml.xspf'
[0x1348bc8] main access debug: looking for access module matching "file": 25 candidates
[0x1348bc8] filesystem access debug: opening file `/home/doug/.local/share/vlc/ml.xspf'
[0x1348bc8] main access debug: using access module "filesystem"
[0x13498d8] main stream debug: Using stream method for AStream*
[0x13498d8] main stream debug: starting pre-buffering
[0x13498d8] main stream debug: received first data after 0 ms
[0x13498d8] main stream debug: pre-buffering done 296 bytes in 0s - 18066 KiB/s
[0x1349b38] main stream debug: looking for stream_filter module matching "any": 9 candidates
[0x1349b38] main stream debug: no stream_filter modules matched
[0x1349b38] main stream debug: looking for stream_filter module matching "record": 9 candidates
[0x1349b38] main stream debug: using stream_filter module "record"
[0x14887d8] main input debug: creating demux: access='file' demux='xspf-open' location='/home/doug/.local/share/vlc/ml.xspf' file='/home/doug/.local/share/vlc/ml.xspf'
[0x134c458] main demux debug: looking for demux module matching "xspf-open": 63 candidates
[0x134c458] playlist demux debug: using XSPF playlist reader
[0x134c458] main demux debug: using demux module "playlist"
[0x134c6e8] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x134c6e8] lua demux meta debug: Trying Lua scripts in /home/doug/.local/share/vlc/lua/meta/reader
[0x134c6e8] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x134c6e8] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x134c6e8] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x134c6e8] main demux meta debug: no meta reader modules matched
[0x14887d8] main input debug: `file/xspf-open:///home/doug/.local/share/vlc/ml.xspf' successfully opened
[0x13585d8] main xml reader debug: looking for xml reader module matching "any": 1 candidates
[0x13585d8] main xml reader debug: using xml reader module "xml"
[0x134c458] playlist demux debug: parsed 0 tracks successfully
[0x14887d8] main input debug: EOF reached
[0x134c458] main demux debug: removing module "playlist"
[0x1349b38] main stream debug: removing module "record"
[0x1348bc8] main access debug: removing module "filesystem"
[0x1294138] main playlist debug: creating audio output
[0x13498d8] main audio output debug: looking for audio output module matching "any": 6 candidates
[0x13498d8] pulse audio output debug: using library version 4.0.0
[0x13498d8] pulse audio output debug:  (compiled with version 4.0.0, protocol 28)
[0x13498d8] pulse audio output debug: connected locally to unix:/run/user/1000/pulse/native as client #16
[0x13498d8] pulse audio output debug: using protocol 28, server protocol 28
[0x13498d8] main audio output debug: using audio output module "pulse"
[0x1294138] main playlist debug: keeping audio output
[0x1294138] main playlist debug: adding item `test_wmv.wmv' ( file:///home/doug/Videos/test_wmv.wmv )
[0x13498d8] pulse audio output debug: adding sink 0: alsa_output.pci-0000_00_03.0.hdmi-stereo (Built-in Audio Digital Stereo (HDMI))
[0x13498d8] pulse audio output debug: adding sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Built-in Audio Analog Stereo)
[0x7f93ec000958] main input debug: Creating an input for 'test_wmv.wmv'
[0x129aa18] main interface debug: looking for interface module matching "hotkeys,none": 19 candidates
[0x129aa18] main interface debug: using interface module "hotkeys"
[0x12abb68] main interface debug: looking for interface module matching "globalhotkeys,none": 19 candidates
[0x12abb68] main interface debug: using interface module "globalhotkeys"
[0x1358018] main interface debug: looking for interface module matching "dbus,none": 19 candidates
[0x1358018] dbus interface debug: listening on dbus as: org.mpris.MediaPlayer2.vlc.instance4921
[0x1358018] main interface debug: using interface module "dbus"
[0x1280118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x12b5ae8] main interface debug: looking for interface module matching "any": 19 candidates
[0x1358018] dbus interface debug: Getting All properties
[0x1294138] main playlist debug: meta ok for (null), need to fetch art
[0x7f93dc000958] main demux meta debug: looking for meta fetcher module matching "any": 1 candidates
[0x1358018] dbus interface debug: Getting All properties
[0x7f93dc000958] lua demux meta debug: Trying Lua scripts in /home/doug/.local/share/vlc/lua/meta/fetcher
[0x7f93dc000958] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[0x7f93dc000958] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[0x7f93dc000958] main demux meta debug: using meta fetcher module "lua"
[0x7f93dc000958] main demux meta debug: removing module "lua"
[0x1294138] main playlist debug: searching art for test_wmv.wmv
[0x7f93dc000958] main art finder debug: looking for art finder module matching "any": 2 candidates
[0x7f93dc000958] lua art finder debug: Trying Lua scripts in /home/doug/.local/share/vlc/lua/meta/art
[0x7f93dc000958] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[0x7f93dc000958] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[0x7f93dc000958] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[0x7f93dc000958] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[0x7f93dc000958] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[0x7f93dc000958] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[0x7f93dc000958] main art finder debug: no art finder modules matched
[0x1294138] main playlist debug: art not found for test_wmv.wmv
[0x1358018] dbus interface debug: Getting All properties
[0x7f93e43de488] main generic debug: looking for extension module matching "any": 1 candidates
[0x7f93e43de488] lua generic debug: Opening Lua Extension module
[0x7f93e43de488] lua generic debug: Trying Lua scripts in /home/doug/.local/share/vlc/lua/extensions
[0x7f93e43de488] lua generic debug: Trying Lua scripts in /usr/lib/vlc/lua/extensions
[0x7f93e43de488] lua generic debug: Trying Lua playlist script /usr/lib/vlc/lua/extensions/VLSub.luac
[0x7f93e43de488] lua generic debug: Scanning Lua script /usr/lib/vlc/lua/extensions/VLSub.luac
[0x7f93e43de488] lua generic debug: Script /usr/lib/vlc/lua/extensions/VLSub.luac has the following capability flags: 0x5
[0x7f93e43de488] lua generic debug: Trying Lua scripts in /usr/share/vlc/lua/extensions
[0x7f93e43de488] main generic debug: using extension module "lua"
[0x7f93e44868e8] main probe debug: looking for services probe module matching "any": 10 candidates
[0x7f93e44868e8] main probe debug: no services probe modules matched
[0x12b5ae8] qt4 interface debug: Sorting by column -1, order 0
[0x12b5ae8] qt4 interface debug: Sorting by column -1, order 0
[0x12b5ae8] qt4 interface debug: Sorting by column -1, order 0
[0x12b5ae8] main interface debug: using interface module "qt4"
[0x1294138] main playlist debug: processing request item: null, node: Playlist, skip: 0
[0x1294138] main playlist debug: rebuilding array of current - root Playlist
[0x1294138] main playlist debug: rebuild done - 1 items, index -1
[0x1294138] main playlist debug: starting playback of the new playlist item
[0x1294138] main playlist debug: resyncing on test_wmv.wmv
[0x1294138] main playlist debug: test_wmv.wmv is at 0
[0x1294138] main playlist debug: creating new input thread
[0x7f93c40009b8] main input debug: Creating an input for 'test_wmv.wmv'
[0x7f93c40009b8] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x7f93c40009b8] main input debug: `file:///home/doug/Videos/test_wmv.wmv' gives access `file' demux `' path `/home/doug/Videos/test_wmv.wmv'
[0x7f93c40009b8] main input debug: creating demux: access='file' demux='' location='/home/doug/Videos/test_wmv.wmv' file='/home/doug/Videos/test_wmv.wmv'
[0x7f93bc000e78] main demux debug: looking for access_demux module matching "file": 20 candidates
[0x7f93bc000e78] main demux debug: no access_demux modules matched
[0x7f93c40009b8] main input debug: creating access 'file' location='/home/doug/Videos/test_wmv.wmv', path='/home/doug/Videos/test_wmv.wmv'
[0x7f93bc0010c8] main access debug: looking for access module matching "file": 25 candidates
[0x7f93bc0010c8] filesystem access debug: opening file `/home/doug/Videos/test_wmv.wmv'
[0x7f93bc0010c8] main access debug: using access module "filesystem"
[0x7f93bc001218] main stream debug: Using stream method for AStream*
[0x7f93bc001218] main stream debug: starting pre-buffering
[0x7f93bc001218] main stream debug: received first data after 0 ms
[0x7f93bc001218] main stream debug: pre-buffering done 1024 bytes in 0s - 111111 KiB/s
[0x7f93bcc01518] main stream debug: looking for stream_filter module matching "any": 9 candidates
[0x7f93bcc01518] main stream debug: no stream_filter modules matched
[0x7f93bcc01518] main stream debug: looking for stream_filter module matching "record": 9 candidates
[0x7f93bcc01518] main stream debug: using stream_filter module "record"
[0x7f93c40009b8] main input debug: creating demux: access='file' demux='' location='/home/doug/Videos/test_wmv.wmv' file='/home/doug/Videos/test_wmv.wmv'
[0x7f93bcc01788] main demux debug: looking for demux module matching "asf": 63 candidates
[0x7f93bcc01518] asf stream warning: unknown asf object (not loaded): 0xd9aade20-0x7c17-0x4f9c-0xbc288555dd98e2a2
[0x7f93bcc01518] asf stream debug: + 'Unknown'
[0x7f93bcc01518] asf stream debug: |   + 'Header'
[0x7f93bcc01518] asf stream debug: |   |   + 'Extended content description'
[0x7f93bcc01518] asf stream debug: |   |   + 'Content Description'
[0x7f93bcc01518] asf stream debug: |   |   + 'File Properties'
[0x7f93bcc01518] asf stream debug: |   |   + 'Header Extension'
[0x7f93bcc01518] asf stream debug: |   |   |   + 'Language List'
[0x7f93bcc01518] asf stream debug: |   |   |   + 'Unknown'
[0x7f93bcc01518] asf stream debug: |   |   |   + 'Metadata'
[0x7f93bcc01518] asf stream debug: |   |   |   + 'Padding'
[0x7f93bcc01518] asf stream debug: |   |   |   + 'Extended Stream Properties'
[0x7f93bcc01518] asf stream debug: |   |   |   + 'Extended Stream Properties'
[0x7f93bcc01518] asf stream debug: |   |   |   + 'Unknown'
[0x7f93bcc01518] asf stream debug: |   |   + 'Codec List'
[0x7f93bcc01518] asf stream debug: |   |   + 'Stream Properties'
[0x7f93bcc01518] asf stream debug: |   |   + 'Stream Properties'
[0x7f93bcc01518] asf stream debug: |   |   + 'Stream Bitrate Properties'
[0x7f93bcc01518] asf stream debug: |   + 'Data'
[0x7f93bcc01788] asf demux debug: found 2 streams
[0x7f93bcc01788] asf demux debug: added new audio stream(codec:0x161,ID:1)
[0x7f93c40009b8] main input debug: selecting program id=0
[0x7f93bcc01788] asf demux debug: added new video stream(ID:2)
[0x7f93bcc01788] main demux debug: using demux module "asf"
[0x7f93c40009b8] main input debug: looking for a subtitle file in /home/doug/Videos/
[0x7f93bcc09638] main decoder debug: looking for decoder module matching "any": 39 candidates
[0x12b5ae8] qt4 interface debug: IM: Setting an input
[0x7f93bcc09638] avcodec decoder debug: avcodec codec (Windows Media Audio 2) started
[0x7f93bcc09638] main decoder debug: using decoder module "avcodec"
[0x7f93bcc58848] main decoder debug: looking for decoder module matching "any": 39 candidates
[0x7f93bcc58848] avcodec decoder debug: trying to use direct rendering
[0x7f93bcc58848] avcodec decoder debug: allowing 4 thread(s) for decoding
[0x7f93bcc58848] avcodec decoder debug: avcodec codec (Windows Media Video 9) started
[0x7f93bcc58848] main decoder debug: using decoder module "avcodec"
[0x7f93bcc5e708] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x7f93bcc5e708] lua demux meta debug: Trying Lua scripts in /home/doug/.local/share/vlc/lua/meta/reader
[0x7f93bcc5e708] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x7f93bcc5e708] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x7f93bcc5e708] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x7f93bcc5e708] main demux meta debug: no meta reader modules matched
[0x7f93c40009b8] main input debug: `file:///home/doug/Videos/test_wmv.wmv' successfully opened
[0x7f93c40009b8] main input debug: Buffering 0%
[0x7f93c40009b8] main input debug: Buffering 11%
[0x7f93b4025f48] main spu text debug: looking for text renderer module matching "any": 2 candidates
[0x7f93c40009b8] main input debug: Buffering 22%
[0x7f93c40009b8] main input debug: Buffering 22%
[0x7f93c40009b8] main input debug: Buffering 66%
[0x7f93c40009b8] main input debug: Buffering 99%
[0x7f93c40009b8] main input debug: Stream buffering done (433 ms in 2 ms)
[0x7f93b4025f48] freetype spu text debug: Building font databases.
[0x7f93b4025f48] freetype spu text debug: Took 0 microseconds
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f93b4025f48] freetype spu text debug: Using Serif Bold as font from file /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
[0x7f93b4025f48] freetype spu text debug: using fontsize: 2
[0x7f93b4025f48] main spu text debug: using text renderer module "freetype"
[0x7f93b402d8c8] main scale debug: looking for video filter2 module matching "any": 55 candidates
[0x7f93b402d8c8] swscale scale debug: 32x32 chroma: YUVA -> 16x16 chroma: RGBA with scaling using Bicubic (good quality)
[0x7f93b402d8c8] main scale debug: using video filter2 module "swscale"
[0x7f93b4045968] main scale debug: looking for video filter2 module matching "any": 55 candidates
[0x7f93b4045968] yuvp scale debug: YUVP to YUVA converter
[0x7f93b4045968] main scale debug: using video filter2 module "yuvp"
[0x7f93b4024878] main video output debug: Deinterlacing available
[0x7f93b4024878] main video output debug: deinterlace 0, mode blend, is_needed 0
[0x7f93b4024878] main video output debug: Opening vout display wrapper
[0x7f93ac001248] main vout display debug: looking for vout display module matching "any": 12 candidates
[0x7f93ac0040a8] main window debug: looking for vout window xid module matching "qt4,any": 4 candidates
[0x7f93ac0040a8] qt4 window debug: requesting video window...
[0x12b5ae8] qt4 interface debug: Video was requested 0, 0
[0x7f93ac0040a8] main window debug: using vout window xid module "qt4"
[0x7f93ac0042f8] main inhibit debug: looking for inhibit module matching "any": 2 candidates
[0x7f93ac0042f8] dbus_screensaver inhibit debug: found service org.freedesktop.ScreenSaver
[0x7f93ac0042f8] main inhibit debug: using inhibit module "dbus_screensaver"
[0x7f93ac001248] xcb_xv vout display debug: connected to X11.0 server
[0x7f93ac001248] xcb_xv vout display debug:  vendor : The X.Org Foundation
[0x7f93ac001248] xcb_xv vout display debug:  version: 11501000
[0x7f93ac001248] xcb_xv vout display debug: using screen 0xbc
[0x7f93ac001248] xcb_xv vout display debug: using XVideo extension v2.2
[0x7f93ac001248] xcb_xv vout display debug: using adaptor Intel(R) Textured Video
[0x7f93ac001248] xcb_xv vout display debug: using port 105
[0x7f93ac001248] xcb_xv vout display debug: using image format 0x30323449
[0x7f93ac001248] xcb_xv vout display debug: using X11 visual ID 0x40 (depth: 24)
[0x7f93ac001248] xcb_xv vout display debug: using X11 window 0x04c00000
[0x7f93ac001248] xcb_xv vout display debug: using X11 graphic context 0x04c00002
[0x7f93ac001248] main vout display debug: VoutDisplayEvent 'fullscreen' 0
[0x7f93ac001248] main vout display debug: VoutDisplayEvent 'resize' 489x240 window
[0x7f93ac001248] main vout display debug: using vout display module "xcb_xv"
[0x7f93b4024878] main video output debug: original format sz 320x240, of (0,0), vsz 320x240, 4cc I420, sar 1:1, msk r0x0 g0x0 b0x0
[0x7f93b4025f48] main spu text debug: removing module "freetype"
[0x7f93b4025f48] main spu text debug: looking for text renderer module matching "any": 2 candidates
[0x7f93b4025f48] freetype spu text debug: Building font databases.
[0x7f93b4025f48] freetype spu text debug: Took 0 microseconds
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f93b4025f48] freetype spu text debug: Using Serif Bold as font from file /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
[0x7f93b4025f48] freetype spu text debug: using fontsize: 2
[0x7f93b4025f48] main spu text debug: using text renderer module "freetype"
[0x7f93bcc58848] avcodec decoder warning: disabling direct rendering
[0x7f93ac001248] xcb_xv vout display debug: display is visible
[0x7f93ac001248] main vout display error: Failed to resize display
[0x7f93bcc58848] main decoder debug: End of video preroll
[0x7f93bcc58848] main decoder debug: Received first picture
[0x7f93ac00f888] main blend debug: looking for video blending module matching "any": 1 candidates
[0x7f93ac00f888] main blend debug: using video blending module "blend"
[0x7f93ac001248] xcb_xv vout display debug: display is visible
[0x7f93ac001248] main vout display debug: VoutDisplayEvent 'resize' 320x240 window
[0x7f93ac001248] main vout display debug: VoutDisplayEvent 'resize' 489x240 window
[0x7f93ac001248] xcb_xv vout display debug: display is visible
[0x7f93c40009b8] main input debug: Decoder buffering done in 101 ms
[0x7f93b4024878] main video output debug: picture might be displayed late (missing 10 ms)
[0x7f93ac001248] main vout display debug: auto hiding mouse cursor
[0x7f93c40009b8] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0x7f93c40009b8] main input error: ES_OUT_RESET_PCR called
[0x7f93bcc09638] avcodec decoder warning: Physical channel configuration not set : guessing
[0x1294138] main playlist debug: reusing audio output
[0x13498d8] pulse audio output debug: using stereo channel map
[0x13498d8] pulse audio output debug: changed buffer metrics: maxlength=4194304, tlength=42336, prebuf=0, minreq=14112
[0x13498d8] pulse audio output debug: connected to sink alsa_output.pci-0000_00_1b.0.analog-stereo
[0x13498d8] main audio output debug: output 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
[0x7f93cc003948] main volume debug: looking for audio volume module matching "any": 2 candidates
[0x7f93cc003948] main volume debug: using audio volume module "float_mixer"
[0x13498d8] main audio output debug: input 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
[0x7f93cc003c58] main audio filter debug: looking for audio filter module matching "scaletempo": 14 candidates
[0x7f93cc003c58] scaletempo audio filter debug: format: 44100 rate, 2 nch, 4 bps, fl32
[0x7f93cc003c58] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0x7f93cc003c58] scaletempo audio filter debug: 1.000 scale, 1323.000 stride_in, 1323 stride_out, 1059 standing, 264 overlap, 617 search, 2204 queue, fl32 mode
[0x7f93cc003c58] main audio filter debug: using audio filter module "scaletempo"
[0x13498d8] main audio output debug: conversion: 'f32l'->'f32l' 44100 Hz->44100 Hz Stereo->Stereo
[0x13498d8] main audio output debug: conversion pipeline complete
[0x13498d8] main audio output debug: conversion: 'f32l'->'f32l' 44100 Hz->44100 Hz Stereo->Stereo
[0x13498d8] main audio output debug: conversion pipeline complete
[0x7f93cc01ce18] main audio resampler debug: looking for audio resampler module matching "any": 3 candidates
[0x13498d8] pulse audio output debug: base volume: 65536
[0x13498d8] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Built-in Audio Analog Stereo)
[0x7f93cc01ce18] main audio resampler debug: using audio resampler module "samplerate"
[0x7f93c40009b8] main input debug: Buffering 0%
[wmv3 @ 0x7f93bcc59120] warning: first frame is no keyframe
[0x7f93c40009b8] main input debug: Buffering 30%
[0x7f93c40009b8] main input debug: Buffering 83%
[0x7f93c40009b8] main input debug: Stream buffering done (383 ms in 0 ms)
[0x7f93bcc09638] main decoder debug: End of audio preroll
[0x7f93bcc58848] main decoder debug: End of video preroll
[0x7f93bcc58848] main decoder debug: Received first picture
[0x7f93c40009b8] main input debug: Decoder buffering done in 4 ms
[0x13498d8] pulse audio output debug: cannot synchronize start
[0x13498d8] pulse audio output warning: starting late (-16574 us)
[0x13498d8] pulse audio output debug: started
[0x13498d8] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Built-in Audio Analog Stereo)
<playing fine>
```

Same mplayer, using -vo xv - 
```
mplayer -V -vo xv '/home/doug/Videos/test_wmv.wmv' 
MPlayer SVN-r37220 (C) 2000-2012 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz (Family: 6, Model: 60, Stepping: 3)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSE3: 1 SSSE3: 1 SSE4: 1 SSE4.2: 1 AVX: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/doug/.mplayer/codecs.conf'
Reading optional codecs config file /home/doug/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/doug/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --enable-xmga --enable-mga --enable-joystick --enable-libopencore_amrnb --enable-libopencore_amrwb --disable-decoder=amrnb --language=all --disable-libdvdcss-internal --disable-mencoder --enable-radio --enable-radio-capture --extra-libs=-ldl -lvorbisenc -lvorbis --enable-xvmc --with-xvmclib=XvMCW --disable-gui --enable-runtime-cpudetection
CommandLine: '-V' '-vo' 'xv' '/home/doug/Videos/test_wmv.wmv'
Using nanosleep() timing
get_path('input.conf') -> '/home/doug/.mplayer/input.conf'
Parsing input config file /home/doug/.mplayer/input.conf
Input config file /home/doug/.mplayer/input.conf parsed: 1 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('test_wmv.wmv.conf') -> '/home/doug/.mplayer/test_wmv.wmv.conf'

Playing /home/doug/Videos/test_wmv.wmv.
get_path('sub/') -> '/home/doug/.mplayer/sub/'
[file] File size is 2207388 bytes
STREAM: [file] /home/doug/Videos/test_wmv.wmv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
libavformat version 55.37.102 (internal)
Configuration: --enable-gpl --enable-postproc
LAVF_check: ASF (Advanced / Active Streaming Format)
Checking for YUV4MPEG2
ASF file format detected.
stream type: guid_audio_stream
stream concealment: guid_audio_conceal_interleave
type: 28 bytes,  stream: 8 bytes  ID: 1
unk1: 0  unk2: 217FCD8
FILEPOS=0x1479
==> Found audio stream: 1
[asfheader] Audio stream found, -aid 1
======= WAVE Format =======
Format Tag: 353 (0x161)
Channels: 2
Samplerate: 44100
avg byte/sec: 8005
Block align: 1487
bits/sample: 16
cbSize: 10
Unknown extra header dump: [0] [88] [0] [0] [f] [0] [79] [2e] [0] [0] 
==========================================================================
ASF: audio scrambling: 1 x 1 x 1487
stream type: guid_video_stream
stream concealment: unknown guid 0057fb20-555b-cf11-a8fd00805f5c442b
type: 55 bytes,  stream: 0 bytes  ID: 2
unk1: 0  unk2: 0
FILEPOS=0x14EB
==> Found video stream: 2
[asfheader] Video stream found, -vid 2
======= VIDEO Format ======
  biSize 44
  biWidth 320
  biHeight 240
  biPlanes 1
  biBitCount 24
  biCompression 861293911='WMV3'
  biSizeImage 0
Unknown extra header dump: [4e] [79] [1a] [1] 
===========================
ASF: packets: 344  flags: 2  max_packet_size: 6400  min_packet_size: 6400  max_bitrate: 521498  preroll: 4000

 Title: 
 Author: 
 Copyright: 
 Comment: 

============ ASF Stream group == START ===
 stream count=[0x2][2]
   stream id=[0x1][1]
   max bitrate=[0x100c5][65733]
   stream id=[0x2][2]
   max bitrate=[0x6f455][455765]
============ ASF Stream group == END ===
Found movie at 0x157A - 0x21AD7A
ASF: 1 audio and 1 video streams found
Auto-selected ASF video ID = 2
ASF: Searching for audio stream (id:-1).
Auto-selected ASF audio ID = 1
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  448.0 kbps (54.7 kbyte/s)
[V] filefmt:6  fourcc:0x33564D57  size:320x240  fps:1000.000  ftime:=0.0010
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
Load subtitles in /home/doug/Videos/
get_path('sub/') -> '/home/doug/.mplayer/sub/'
X11 opening display: :0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1920x1080 with depth 24 and 32 bpp (":0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 16384x16384
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 55.60.103 (internal)
Configuration: --enable-gpl --enable-postproc
[VD_FFMPEG] Trying pixfmt=0.
[ffmpeg] aspect_ratio: 0.000000
[VD_FFMPEG] Trying pixfmt=0.
[ffmpeg] aspect_ratio: 0.000000
[wmv3 @ 0x7f19acc63d00]Header: 4E791A01
[wmv3 @ 0x7f19acc63d00]Profile 1:
frmrtq_postproc=7, bitrtq_postproc=7
LoopFilter=1, MultiRes=0, FastUVMC=0, Extended MV=0
Rangered=0, VSTransform=1, Overlap=1, SyncMarker=0
DQuant=1, Quantizer mode=0, Max B frames=0
INFO: libavcodec init OK!
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 1536000 + 131072 = 1667072 bytes for output buffer.
FFmpeg's libavcodec audio codec
INFO: libavcodec "wmav2" init OK!
AUDIO: 44100 Hz, 2 ch, floatle, 64.0 kbit/2.27% (ratio: 8005->352800)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
Building audio filter chain for 44100Hz/2ch/floatle -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/floatle
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/floatle -> 44100Hz/2ch/floatle...
[dummy] Was reinitialized: 44100Hz/2ch/floatle
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Starting playback...
Increasing filtered audio buffer size from 0 to 92288

avg. framerate: 30 fps             
[VD_FFMPEG] Trying pixfmt=0.
[ffmpeg] aspect_ratio: 0.000000
[ffmpeg] aspect_ratio: 0.000000
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (320x240->320x240,flags=0,'MPlayer',0x32315659)
VO: [xv] 320x240 => 320x240 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 105 for hw scaling
*** [vo] Allocating mp_image_t, 320x256x12bpp YUV planar, 122880 bytes
Unicode font: 5361 glyphs.
Unicode font: 5361 glyphs.
A:   4.0 V:   4.0 A-V: -0.029 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
<playing fine>
```

May be worthwhile to set up a new user account & try there.
What is this about in your vlc debug, if you know? -
omxil decoder

---

### Post by monkeybrain20122 on 2014-07-04
hardware decoding (VAAPI) was on for vlc and mpv when I checked the sample.
mplayer uses VDPAU (libvdpau-va-gl), that could be the reason why it doesn't work.

Edited: switch vlc output to vdpau, still works.

---

