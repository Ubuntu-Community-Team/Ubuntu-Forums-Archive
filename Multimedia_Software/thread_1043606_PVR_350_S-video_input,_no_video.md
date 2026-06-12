---
title: "PVR 350 S-video input, no video"
date: 2009-01-18
forum: Multimedia Software
---

### Post by morgcon on 2009-01-18
Ubuntu 8.10, Nvidia 8500GT, 180.11 drivers, VLC 0.9.4

I am trying to recieve signal from skydigibox via S input on a Hauppauge pvr350. VLC is the programme i using, although using mplayer the problem persists. VLC plays everything i throw it, no problem. :) Using pvr function and changing to correct pins for s-input i can get audio but no video just a black screen. I think maybe a overlay problem ? But i've spent the best part of today searching here and google for a remedy and think I'm blinkered :( If anyone has got some pointers i'd be thankful. Below is the output of VLV -vvv debug.

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc debug: checking builtin modules
[00000001] main libvlc debug: checking plugin modules
[00000001] main libvlc debug: loading plugins cache file /home/pbates/.cache/vlc/plugins-04041e.dat
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main libvlc debug: module bank initialized, found 272 modules
[00000001] main libvlc debug: opening config file (/home/pbates/.config/vlc/vlcrc)
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000370] main interaction debug: thread 3082410896 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000372] main input debug: Creating an input for 'Media Library'
[00000372] main input debug: Input is a meta file: disabling unneeded options
[00000372] main input debug: `file/xspf-open:///home/pbates/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/pbates/.local/share/vlc/ml.xspf'
[00000372] main input debug: creating access 'file' path='/home/pbates/.local/share/vlc/ml.xspf'
[00000373] main access debug: looking for access module: 3 candidates
[00000373] access_mmap access debug: opening file /home/pbates/.local/share/vlc/ml.xspf
[00000373] main access debug: using access module "access_mmap"
[00000373] main access debug: TIMER module_Need() : 0.523 ms - Total 0.523 ms / 1 intvls (Avg 0.523 ms)
[00000377] main stream debug: Using AStream*Block
[00000377] main stream debug: pre buffering
[00000377] main stream debug: received first data for our buffer
[00000373] access_mmap access debug: at end of memory mapped file
[00000372] main input debug: creating demux: access='file' demux='xspf-open' path='/home/pbates/.local/share/vlc/ml.xspf'
[00000378] main demux debug: looking for demux module: 1 candidate
[00000378] playlist demux debug: using XSPF playlist reader
[00000378] main demux debug: using demux module "playlist"
[00000378] main demux debug: TIMER module_Need() : 0.342 ms - Total 0.342 ms / 1 intvls (Avg 0.342 ms)
[00000372] main input debug: `file/xspf-open:///home/pbates/.local/share/vlc/ml.xspf' successfully opened
[00000393] main xml debug: looking for xml module: 2 candidates
[00000393] main xml debug: using xml module "xml"
[00000393] main xml debug: TIMER module_Need() : 0.502 ms - Total 0.502 ms / 1 intvls (Avg 0.502 ms)
[00000373] access_mmap access debug: at end of memory mapped file
[00000378] playlist demux warning: invalid <playlist> attribute:"xmlns:vlc"
[00000378] playlist demux debug: parsed 0 tracks successfully
[00000393] main xml debug: removing module "xml"
[00000372] main input debug: EOF reached
[00000372] main input debug: control type=1
[00000378] main demux debug: removing module "playlist"
[00000373] main access debug: removing module "access_mmap"
[00000372] main input debug: TIMER input launching for 'Media Library' : 6.714 ms - Total 6.714 ms / 1 intvls (Avg 6.714 ms)
[00000395] main preparser debug: waiting for thread initialization
[00000370] main interaction debug: thread started
[00000395] main preparser debug: thread started
[00000395] main preparser debug: thread 3071032208 (preparser) created at priority 0 (playlist/thread.c:79)
[00000396] main fetcher debug: thread started
[00000396] main fetcher debug: waiting for thread initialization
[00000396] main fetcher debug: thread 3062639504 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000371] main playlist debug: thread started
[00000371] main playlist debug: waiting for thread initialization
[00000371] main playlist debug: rebuilding array of current - root Playlist
[00000371] main playlist debug: rebuild done - 0 items, index -1
[00000371] main playlist debug: thread 3054246800 (playlist) created at priority 0 (playlist/thread.c:117)
[00000397] main interface debug: looking for interface module: 1 candidate
[00000397] main interface debug: using interface module "hotkeys"
[00000397] main interface debug: TIMER module_Need() : 0.236 ms - Total 0.236 ms / 1 intvls (Avg 0.236 ms)
[00000397] main interface debug: thread started
[00000397] main interface debug: thread 3045854096 (interface) created at priority 0 (interface/interface.c:168)
[00000399] main interface debug: looking for interface module: 1 candidate
[00000399] main interface debug: using interface module "inhibit"
[00000399] main interface debug: TIMER module_Need() : 1.918 ms - Total 1.918 ms / 1 intvls (Avg 1.918 ms)
[00000399] main interface debug: thread started
[00000399] main interface debug: thread 3037461392 (interface) created at priority 0 (interface/interface.c:168)
[00000401] main interface debug: looking for interface module: 1 candidate
[00000401] main interface debug: using interface module "screensaver"
[00000401] main interface debug: TIMER module_Need() : 0.290 ms - Total 0.290 ms / 1 intvls (Avg 0.290 ms)
[00000401] main interface debug: thread started
[00000401] main interface debug: thread 3029068688 (interface) created at priority 0 (interface/interface.c:168)
[00000403] main interface debug: looking for interface module: 22 candidates
[00000403] main interface debug: using interface module "signals"
[00000403] main interface debug: TIMER module_Need() : 0.316 ms - Total 0.316 ms / 1 intvls (Avg 0.316 ms)
[00000403] main interface debug: thread started
[00000403] main interface debug: thread 3012283280 (interface) created at priority 0 (interface/interface.c:168)
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000405] main interface debug: looking for interface module: 4 candidates
[00000405] main interface debug: using interface module "qt4"
[00000405] main interface debug: TIMER module_Need() : 29.002 ms - Total 29.002 ms / 1 intvls (Avg 29.002 ms)
[00000405] main interface debug: thread started
[00000405] main interface debug: thread 2985888656 (interface) created at priority 0 (interface/interface.c:168)
[00000405] qt4 interface debug: Error while initializing qt-specific localization
[00000405] qt4 interface debug: Initialization of Capture device panel
[00000405] qt4 interface debug: This shouldn't happen, please report
[00000405] qt4 interface debug: This shouldn't happen, please report
[00000405] qt4 interface debug:  :pvr-caching=300 :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-width=-1 :pvr-height=-1 :pvr-frequency=-1 :pvr-framerate=-1 :pvr-keyint=-1 :pvr-bframes=-1 :pvr-bitrate=-1 :pvr-bitrate-peak=-1 :pvr-bitrate-mode=0 :pvr-audio-bitmask=-1 :pvr-audio-volume=-1 :pvr-channel=1
[00000405] qt4 interface debug: New item: pvr://
[00000405] qt4 interface debug: New Option: :pvr-device=
[00000405] qt4 interface debug: New Option: :pvr-radio-device=
[00000405] qt4 interface debug: New Option: :pvr-norm=0
[00000405] qt4 interface debug: New Option: :pvr-caching=300
[00000405] qt4 interface debug: New Option: :pvr-device=/dev/video0
[00000405] qt4 interface debug: New Option: :pvr-radio-device=/dev/radio0
[00000405] qt4 interface debug: New Option: :pvr-norm=0
[00000405] qt4 interface debug: New Option: :pvr-width=-1
[00000405] qt4 interface debug: New Option: :pvr-height=-1
[00000405] qt4 interface debug: New Option: :pvr-frequency=-1
[00000405] qt4 interface debug: New Option: :pvr-framerate=-1
[00000405] qt4 interface debug: New Option: :pvr-keyint=-1
[00000405] qt4 interface debug: New Option: :pvr-bframes=-1
[00000405] qt4 interface debug: New Option: :pvr-bitrate=-1
[00000405] qt4 interface debug: New Option: :pvr-bitrate-peak=-1
[00000405] qt4 interface debug: New Option: :pvr-bitrate-mode=0
[00000405] qt4 interface debug: New Option: :pvr-audio-bitmask=-1
[00000405] qt4 interface debug: New Option: :pvr-audio-volume=-1
[00000405] qt4 interface debug: New Option: :pvr-channel=1
[00000371] main playlist debug: adding item `pvr://' ( pvr:// )
[00000371] main playlist debug: rebuilding array of current - root Playlist
[00000371] main playlist debug: rebuild done - 1 items, index -1
[00000371] main playlist debug: starting new item
[00000371] main playlist debug: processing request item pvr:// node null skip 0
[00000371] main playlist debug: resyncing on pvr://
[00000371] main playlist debug: pvr:// is at 0
[00000371] main playlist debug: creating new input thread
[00000409] main input debug: Creating an input for 'pvr://'
[00000409] main input debug: waiting for thread initialization
[00000409] main input debug: thread started
[00000409] main input debug: thread 2957208464 (input) created at priority 10 (input/input.c:370)
[00000405] qt4 interface debug: Updating the stream status: 3
[00000409] main input debug: `pvr://' gives access `pvr' demux `' path `'
[00000409] main input debug: creating demux: access='pvr' demux='' path=''
[00000410] main demux debug: looking for access_demux module: 0 candidates
[00000410] main demux warning: no access_demux module matched "pvr"
[00000410] main demux debug: TIMER module_Need() : 0.142 ms - Total 0.142 ms / 1 intvls (Avg 0.142 ms)
[00000409] main input debug: creating access 'pvr' path=''
[00000411] main access debug: looking for access module: 1 candidate
[00000411] pvr access debug: Using video device: /dev/video0.
[00000411] pvr access debug: ivtv driver (Hauppauge WinTV PVR-350 on 0000:04:01.0) version 01.04.00
[00000411] pvr access debug: this driver uses the v4l2 API
[00000411] pvr access debug: input set to: 1
[00000411] pvr access debug: Setting [0] bitrate_mode = 0
[00000411] pvr access debug: Setting [1] bframes = 255
[00000411] pvr access error: Failed to write 1 new capture card settings.
[00000411] main access debug: using access module "pvr"
[00000411] main access debug: TIMER module_Need() : 41.625 ms - Total 41.625 ms / 1 intvls (Avg 41.625 ms)
[00000405] qt4 interface debug: New Event: type 1103
[00000405] qt4 interface debug: Updating the stream status: 2
[00000413] main stream debug: Using AStream*Stream
[00000413] main stream debug: pre-buffering...
[00000413] main stream debug: received first data for our buffer
[00000413] main stream debug: pre-buffering done 131068 bytes in 0s - 176 kbytes/s
[00000409] main input debug: creating demux: access='pvr' demux='' path=''
[00000414] main demux debug: looking for demux module: 52 candidates
[00000414] main demux debug: using demux module "ps"
[00000414] main demux debug: TIMER module_Need() : 190.370 ms - Total 190.370 ms / 1 intvls (Avg 190.370 ms)
[00000411] pvr access warning: Unimplemented query in control.
[00000409] main input debug: `pvr://' successfully opened
[00000405] qt4 interface debug: New Event: type 1103
[00000405] qt4 interface debug: Updating the stream status: 3
[00000409] main input debug: control type=1
[00000409] main input debug: selecting program id=0
[00000405] qt4 interface debug: New Event: type 1108
[00000447] main decoder debug: looking for decoder module: 30 candidates
[00000447] main decoder debug: using decoder module "libmpeg2"
[00000447] main decoder debug: TIMER module_Need() : 1.694 ms - Total 1.694 ms / 1 intvls (Avg 1.694 ms)
[00000447] main decoder debug: thread 2930789264 (decoder) created at priority 0 (input/decoder.c:217)
[00000453] main decoder debug: looking for decoder module: 30 candidates
[00000453] main decoder debug: using decoder module "mpeg_audio"
[00000453] main decoder debug: TIMER module_Need() : 7.154 ms - Total 7.154 ms / 1 intvls (Avg 7.154 ms)
[00000453] main decoder debug: thread started
[00000453] main decoder debug: thread 2920000400 (decoder) created at priority 5 (input/decoder.c:217)
[00000453] mpeg_audio decoder debug: MPGA channels:2 samplerate:48000 bitrate:224
[00000453] main decoder debug: no aout present, spawning one
[00000475] main audio output debug: looking for audio output module: 4 candidates
[00000475] alsa audio output debug: opening ALSA device `default'
[00000447] main decoder debug: thread started
[00000447] libmpeg2 decoder debug: 720x576 (display 720,576), aspect 576000, sar 16:15, 25.000 fps
[00000447] main decoder debug: no usable vout present, spawning one
[00000476] main video output debug: window size: 768x576
[00000476] main video output debug: looking for video output module: 6 candidates
[00000476] xvideo video output debug: adaptor 0, port 280, format 0x32315659 (YV12) planar
[00000479] main window debug: looking for vout window module: 2 candidates
[00000479] qt4 window debug: waiting for interface...
[00000479] qt4 window debug: requesting window...
[00000405] qt4 interface debug: Video was requested -1, -1
[00000405] qt4 interface debug: Video is resizing to: 768 576
[00000405] qt4 interface debug: Updating the geometry
[00000476] qt4 video output debug: Qt FS: Attaching Vout
[00000476] qt4 video output debug: Qt: Changing Fullscreen Mode
[00000479] main window debug: using vout window module "qt4"
[00000479] main window debug: TIMER module_Need() : 42.885 ms - Total 42.885 ms / 1 intvls (Avg 42.885 ms)
[00000475] main audio output debug: thread 2899561360 (aout) created at priority 15 (alsa.c:687)
[00000475] main audio output debug: using audio output module "alsa"
[00000475] main audio output debug: TIMER module_Need() : 132.544 ms - Total 132.544 ms / 1 intvls (Avg 132.544 ms)
[00000475] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000475] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000475] main audio output debug: no need for any filter
[00000475] main audio output debug: looking for audio mixer module: 3 candidates
[00000475] main audio output debug: using audio mixer module "float32_mixer"
[00000475] main audio output debug: TIMER module_Need() : 0.375 ms - Total 0.375 ms / 1 intvls (Avg 0.375 ms)
[00000475] main audio output debug: input 'mpga' 48000 Hz Stereo frame=1152 samples/1161 bytes
[00000475] main audio output debug: filter(s) 'mpga'->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[00000484] main audio output debug: looking for audio filter module: 24 candidates
[00000484] main audio output debug: using audio filter module "mpgatofixed32"
[00000484] main audio output debug: TIMER module_Need() : 0.713 ms - Total 0.713 ms / 1 intvls (Avg 0.713 ms)
[00000475] main audio output debug: found a filter for the whole conversion
[00000475] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000489] main audio output debug: looking for audio filter module: 24 candidates
[00000489] main audio output debug: using audio filter module "bandlimited_resampler"
[00000489] main audio output debug: TIMER module_Need() : 0.628 ms - Total 0.628 ms / 1 intvls (Avg 0.628 ms)
[00000475] main audio output debug: found a filter for the whole conversion
[00000475] main audio output debug: thread started
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000476] xvideo video output debug: XShm video extension v1.1 (without pixmaps, opcode: 147)
[00000476] xvideo video output debug: Window manager supports NetWM
[00000476] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000476] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000476] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000476] main video output debug: using video output module "xvideo"
[00000476] main video output debug: TIMER module_Need() : 186.943 ms - Total 186.943 ms / 1 intvls (Avg 186.943 ms)
[00000476] main video output debug: thread started
[00000476] main video output debug: waiting for thread initialization
QPainter::begin: Paint device returned engine == 0, type: 1
[00000476] main video output debug: got 8 direct buffer(s)
[00000476] main video output debug: picture in 720x576 (0,0,720x576), chroma I420, ar 4:3, sar 16:15
[00000476] main video output debug: picture user 720x576 (0,0,720x576), chroma I420, ar 4:3, sar 16:15
[00000476] main video output debug: picture out 720x576 (0,0,720x576), chroma I420, ar 4:3, sar 16:15
[00000476] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000476] main video output debug: thread 2890759056 (video output) created at priority 15 (video_output/video_output.c:504)
[00000405] qt4 interface debug: New Event: type 1109
[00000447] main decoder warning: decoder synchro warning: pts != current_date (223339)
[00000495] main spu text debug: looking for text renderer module: 2 candidates
[00000497] main generic debug: thread started
[00000475] main audio output debug: audio output is starving (30490), playing silence
[00000497] main generic debug: thread 2876771216 (fontlist builder) created at priority 0 (freetype.c:477)
[00000497] freetype generic debug: Building font database...
[00000497] freetype generic debug: Finished building font database.
[00000497] freetype generic debug: Took 0 seconds
[00000497] main generic debug: thread ended
[00000495] freetype spu text debug: using fontsize: 36
[00000495] main spu text debug: using text renderer module "freetype"
[00000495] main spu text debug: TIMER module_Need() : 13.845 ms - Total 13.845 ms / 1 intvls (Avg 13.845 ms)
[00000495] freetype spu text debug: using fontsize: 36
[00000494] main blend debug: looking for video blending module: 1 candidate
[00000494] blend blend debug: chroma: YUVA -> I420
[00000494] main blend debug: using video blending module "blend"
[00000494] main blend debug: TIMER module_Need() : 8.067 ms - Total 8.067 ms / 1 intvls (Avg 8.067 ms)
[00000475] main audio output warning: output date isn't PTS date, requesting resampling (71742)
[00000475] main audio output warning: buffer is 76970 late, triggering upsampling
[00000447] main decoder debug: decoded 106/108 pictures
[00000475] main audio output warning: resampling stopped after 21824834 usec (drift: 34755)
[00000371] main playlist debug: incoming request - stopping current input
[00000371] main playlist debug: dying input
[00000001] main libvlc debug: removing all interfaces
[00000405] qt4 interface debug: Quitting the Qt4 Interface
[00000476] qt4 video output debug: Qt FS: Detaching Vout
[00000476] qt4 video output debug: Qt: Changing Fullscreen Mode
[00000405] qt4 interface debug: Destroying the main interface
[00000479] main window debug: removing module "qt4"
[00000447] main decoder debug: removing module "libmpeg2"
[00000447] main decoder debug: thread ended
[00000405] qt4 interface debug: Destroying the Dialog Provider
[00000409] main input debug: control type=0
[00000409] main input debug: control: stopping input
[00000453] main decoder debug: removing module "mpeg_audio"
[00000453] main decoder debug: thread ended
[00000453] main decoder debug: thread 2920000400 joined (input/decoder.c:248)
[00000453] main decoder debug: killing decoder fourcc `mpga', 0 PES in FIFO
[00000484] main audio output debug: removing module "mpgatofixed32"
[00000489] main audio output debug: removing module "bandlimited_resampler"
[00000475] main audio output debug: thread ended
[00000475] main audio output debug: thread 2899561360 joined (alsa.c:742)
[00000475] main audio output debug: removing module "alsa"
[00000475] main audio output debug: removing module "float32_mixer"
[00000447] main decoder debug: thread 2930789264 joined (input/decoder.c:248)
[00000447] message decoder warning: message queue overflowed
[00000447] main decoder debug: killing decoder fourcc `mpgv', 181 PES in FIFO
[00000371] main playlist debug: dying input
[00000405] main interface debug: thread ended
[00000405] main interface debug: thread 2985888656 joined (interface/interface.c:188)
[00000405] main interface debug: removing module "qt4"
[00000403] main interface debug: thread ended
[00000403] main interface debug: thread 3012283280 joined (interface/interface.c:188)
[00000403] main interface debug: removing module "signals"
[00000401] main interface debug: thread ended
[00000401] main interface debug: thread 3029068688 joined (interface/interface.c:188)
[00000401] main interface debug: removing module "screensaver"
[00000399] main interface debug: thread ended
[00000399] main interface debug: thread 3037461392 joined (interface/interface.c:188)
[00000399] main interface debug: removing module "inhibit"
[00000397] main interface debug: thread ended
[00000397] main interface debug: thread 3045854096 joined (interface/interface.c:188)
[00000397] main interface debug: removing module "hotkeys"
[00000001] main libvlc debug: removing all services discovery tasks
[00000001] main libvlc debug: removing playlist
[00000494] main blend debug: removing module "blend"
[00000497] main generic debug: thread 2876771216 joined (freetype.c:511)
[00000495] main spu text debug: removing module "freetype"
[00000476] main video output debug: thread ended
[00000476] main video output debug: thread 2890759056 joined (video_output/video_output.c:536)
[00000476] main video output debug: removing module "xvideo"
[00000409] main input debug: Program doesn't contain anymore ES
[00000414] main demux debug: removing module "ps"
[00000371] main playlist debug: dying input
[00000371] main playlist debug: dying input
[00000411] main access debug: removing module "pvr"
[00000409] main input debug: thread ended
[00000371] main playlist debug: dead input
[00000409] main input debug: thread 2957208464 joined (playlist/engine.c:244)
[00000409] main input debug: TIMER input launching for 'pvr://' : 1020.440 ms - Total 1020.440 ms / 1 intvls (Avg 1020.440 ms)
[00000371] main playlist debug: saving Media Library to file /home/pbates/.local/share/vlc/ml.xspf
[00000371] main playlist debug: looking for playlist export module: 1 candidate
[00000371] main playlist debug: using playlist export module "export"
[00000371] main playlist debug: TIMER module_Need() : 0.339 ms - Total 0.339 ms / 1 intvls (Avg 0.339 ms)
[00000371] main playlist debug: removing module "export"
[00000395] main preparser debug: thread ended
[00000395] main preparser debug: thread 3071032208 joined (playlist/engine.c:521)
[00000396] main fetcher debug: thread ended
[00000396] main fetcher debug: thread 3062639504 joined (playlist/engine.c:523)
[00000371] main playlist debug: thread ended

[00000371] main playlist debug: thread 3054246800 joined (libvlc.c:992)
[00000395] main preparser debug: Destroyed
[00000396] main fetcher debug: Destroyed
[00000371] main playlist debug: Destroyed
[00000001] main libvlc debug: removing interaction
[00000370] main interaction debug: thread ended
[00000370] main interaction debug: thread 3082410896 joined (interface/interaction.c:400)
[00000001] main libvlc debug: removing all video outputs
[00000001] main libvlc debug: TIMER ML Load : Total 7.571 ms / 1 intvls (Avg 7.571 ms)
[00000001] main libvlc debug: TIMER Items array build : Total 0.042 ms / 2 intvls (Avg 0.021 ms)
[00000001] main libvlc debug: TIMER ML Dump : Total 0.467 ms / 1 intvls (Avg 0.467 ms)
[00000001] main libvlc debug: removing stats
[00000001] main libvlc debug: removing module "memcpymmxext"
[00000001] main libvlc debug: opening config file (/home/pbates/.config/vlc/vlcrc)
[00000001] main libvlc debug: opening config file (/home/pbates/.config/vlc/vlcrc)
[00000001] main libvlc debug: writing plugins cache /home/pbates/.cache/vlc/plugins-04041e.dat

```

Thanks in advance

---

