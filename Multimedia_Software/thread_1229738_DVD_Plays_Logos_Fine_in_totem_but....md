---
title: "DVD Plays Logos Fine in totem but..."
date: 2009-08-02
forum: Multimedia Software
---

### Post by coldReactive on 2009-08-02
Here is a detailed description of my problem.

A. Totem

-- Totem loads the DVD, as soon as the FBI Warning is passed, it hangs.
-- Can skip ahead to the logos, but it skips the bandai logo, and thus you must skip back to see the bandai logo.
-- upon reaching the end of the logo reels, the player hangs. Skipping does not work.

B. VLC

-- No Video Outputs during playback (IE: Only the interface/controls show for VLC), only sound, does not show logos, skips straight to the menu.

Followed this guide for Ubuntu x64 9.04: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

```
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc debug: checking builtin modules
[00000001] main libvlc debug: checking plugin modules
[00000001] main libvlc debug: removing plugins cache file /home/ian/.cache/vlc/plugins-04081e.dat
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main libvlc debug: module bank initialized, found 271 modules
[00000001] main libvlc debug: opening config file (/home/ian/.config/vlc/vlcrc)
[00000001] main libvlc debug: opening config file (/home/ian/.config/vlc/vlcrc)
[00000001] main libvlc debug: opening config file (/home/ian/.config/vlc/vlcrc)
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000365] main interaction debug: thread 140099172854096 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000365] main interaction debug: thread started
[00000367] main input debug: Creating an input for 'Media Library'
[00000367] main input debug: Input is a meta file: disabling unneeded options
[00000367] main input debug: `file/xspf-open:///home/ian/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/ian/.local/share/vlc/ml.xspf'
[00000367] main input debug: creating access 'file' path='/home/ian/.local/share/vlc/ml.xspf'
[00000368] main access debug: looking for access module: 3 candidates
[00000368] access_file access debug: opening file `/home/ian/.local/share/vlc/ml.xspf'
[00000368] main access debug: using access module "access_file"
[00000368] main access debug: TIMER module_Need() : 0.274 ms - Total 0.274 ms / 1 intvls (Avg 0.274 ms)
[00000369] main stream debug: Using AStream*Stream
[00000369] main stream debug: pre-buffering...
[00000369] main stream debug: received first data for our buffer
[00000367] main input debug: creating demux: access='file' demux='xspf-open' path='/home/ian/.local/share/vlc/ml.xspf'
[00000370] main demux debug: looking for demux module: 1 candidate
[00000370] playlist demux debug: using XSPF playlist reader
[00000370] main demux debug: using demux module "playlist"
[00000370] main demux debug: TIMER module_Need() : 0.157 ms - Total 0.157 ms / 1 intvls (Avg 0.157 ms)
[00000367] main input debug: `file/xspf-open:///home/ian/.local/share/vlc/ml.xspf' successfully opened
[00000371] main xml debug: looking for xml module: 2 candidates
[00000371] main xml debug: using xml module "xml"
[00000371] main xml debug: TIMER module_Need() : 0.152 ms - Total 0.152 ms / 1 intvls (Avg 0.152 ms)
[00000370] playlist demux debug: parsed 0 tracks successfully
[00000371] main xml debug: removing module "xml"
[00000367] main input debug: EOF reached
[00000367] main input debug: control type=1
[00000370] main demux debug: removing module "playlist"
[00000368] main access debug: removing module "access_file"
[00000367] main input debug: TIMER input launching for 'Media Library' : 3.189 ms - Total 3.189 ms / 1 intvls (Avg 3.189 ms)
[00000372] main preparser debug: waiting for thread initialization
[00000372] main preparser debug: thread started
[00000372] main preparser debug: thread 140099164461392 (preparser) created at priority 0 (playlist/thread.c:79)
[00000373] main fetcher debug: waiting for thread initialization
[00000373] main fetcher debug: thread started
[00000373] main fetcher debug: thread 140099156068688 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000366] main playlist debug: waiting for thread initialization
[00000366] main playlist debug: thread started
[00000366] main playlist debug: rebuilding array of current - root Playlist
[00000366] main playlist debug: rebuild done - 0 items, index -1
[00000366] main playlist debug: thread 140099147675984 (playlist) created at priority 0 (playlist/thread.c:117)
[00000374] main interface debug: looking for interface module: 1 candidate
[00000374] main interface debug: using interface module "hotkeys"
[00000374] main interface debug: TIMER module_Need() : 0.072 ms - Total 0.072 ms / 1 intvls (Avg 0.072 ms)
[00000374] main interface debug: thread 140099139283280 (interface) created at priority 0 (interface/interface.c:168)
[00000374] main interface debug: thread started
[00000375] main interface debug: looking for interface module: 1 candidate
[00000375] main interface debug: using interface module "inhibit"
[00000375] main interface debug: TIMER module_Need() : 1.415 ms - Total 1.415 ms / 1 intvls (Avg 1.415 ms)
[00000375] main interface debug: thread started
[00000375] main interface debug: thread 140099130890576 (interface) created at priority 0 (interface/interface.c:168)
[00000376] main interface debug: looking for interface module: 1 candidate
[00000376] main interface debug: using interface module "screensaver"
[00000376] main interface debug: TIMER module_Need() : 0.080 ms - Total 0.080 ms / 1 intvls (Avg 0.080 ms)
[00000376] main interface debug: thread started
[00000376] main interface debug: thread 140099122497872 (interface) created at priority 0 (interface/interface.c:168)
[00000377] main interface debug: looking for interface module: 22 candidates
[00000377] main interface debug: using interface module "signals"
[00000377] main interface debug: TIMER module_Need() : 0.109 ms - Total 0.109 ms / 1 intvls (Avg 0.109 ms)
[00000377] main interface debug: thread started
[00000377] main interface debug: thread 140099105712464 (interface) created at priority 0 (interface/interface.c:168)
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000378] main interface debug: looking for interface module: 4 candidates
[00000378] main interface debug: using interface module "qt4"
[00000378] main interface debug: TIMER module_Need() : 0.736 ms - Total 0.736 ms / 1 intvls (Avg 0.736 ms)
[00000378] main interface debug: thread started
[00000378] main interface debug: thread 140099097319760 (interface) created at priority 0 (interface/interface.c:168)
[00000378] main interface debug: opening config file (/home/ian/.config/vlc/vlcrc)
[00000378] main interface debug: opening config file (/home/ian/.config/vlc/vlcrc)
[00000378] qt4 interface debug: Error while initializing qt-specific localization
[00000378] qt4 interface debug: New item: dvd:///dev/sr0
[00000366] main playlist debug: adding item `dvd:///dev/sr0' ( dvd:///dev/sr0 )
[00000366] main playlist debug: rebuilding array of current - root Playlist
[00000366] main playlist debug: rebuild done - 1 items, index -1
[00000366] main playlist debug: starting new item
[00000366] main playlist debug: processing request item dvd:///dev/sr0 node null skip 0
[00000366] main playlist debug: resyncing on dvd:///dev/sr0
[00000366] main playlist debug: dvd:///dev/sr0 is at 0
[00000366] main playlist debug: creating new input thread
[00000379] main input debug: Creating an input for 'dvd:///dev/sr0'
[00000379] main input debug: thread started
[00000379] main input debug: waiting for thread initialization
[00000379] main input debug: `dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0'
[00000379] main input debug: creating demux: access='dvd' demux='' path='/dev/sr0'
[00000380] main demux debug: looking for access_demux module: 2 candidates
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[00000379] main input debug: thread 140098933909840 (input) created at priority 10 (input/input.c:370)
[00000378] qt4 interface debug: Updating the stream status: 3
libdvdnav: DVD Title: SWORD_OF_THE_STRANGER
libdvdnav: DVD Serial Number: 3aa57270
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ian/.dvdnav/SWORD_OF_THE_STRANGER.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000139
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000108e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000432a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00265458
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0026545c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002da1d2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002da1d6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002dda70
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002dda74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002fc3d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002fc3d8
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0
[00000380] dvdnav demux debug: trying to go to dvd menu
[00000381] main generic debug: thread started
[00000381] main generic debug: thread 140098923383120 (dvdnav event thread handler) created at priority 0 (dvdnav.c:352)
[00000380] main demux debug: using access_demux module "dvdnav"
[00000380] main demux debug: TIMER module_Need() : 59.937 ms - Total 59.937 ms / 1 intvls (Avg 59.937 ms)
[00000379] main input debug: `dvd:///dev/sr0' successfully opened
[00000380] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[00000379] main input debug: control type=1
[00000380] dvdnav demux debug: DVDNAV_VTS_CHANGE
[00000380] dvdnav demux debug:      - vtsN=1
[00000380] dvdnav demux debug:      - domain=8
[00000380] dvdnav demux debug: DVDNAV_CELL_CHANGE
[00000380] dvdnav demux debug:      - cellN=1
[00000380] dvdnav demux debug:      - pgN=1
[00000380] dvdnav demux debug:      - cell_length=3516000
[00000380] dvdnav demux debug:      - pg_length=3516000
[00000380] dvdnav demux debug:      - pgc_length=3516000
[00000380] dvdnav demux debug:      - cell_start=0
[00000380] dvdnav demux debug:      - pg_start=0
[00000380] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[00000380] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[00000380] dvdnav demux debug:      - physical_wide=0
[00000380] dvdnav demux debug:      - physical_letterbox=0
[00000380] dvdnav demux debug:      - physical_pan_scan=1
[00000380] dvdnav demux debug: buttonUpdate not done b=1 t=0
[00000379] main input debug: selecting program id=0
[00000382] main decoder debug: looking for decoder module: 30 candidates
[00000378] qt4 interface debug: New Event: type 1103
[00000378] qt4 interface debug: Updating the stream status: 3
[00000382] main decoder debug: using decoder module "spudec"
[00000382] main decoder debug: TIMER module_Need() : 0.257 ms - Total 0.257 ms / 1 intvls (Avg 0.257 ms)
[00000382] main decoder debug: thread started
[00000382] main decoder debug: thread 140098914990416 (decoder) created at priority 0 (input/decoder.c:217)
[00000380] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[00000380] dvdnav demux debug:      - physical=0
[00000380] dvdnav demux debug: buttonUpdate 1
[00000378] qt4 interface debug: New Event: type 1108
[00000383] main decoder debug: looking for decoder module: 30 candidates
[00000383] main decoder debug: using decoder module "libmpeg2"
[00000383] main decoder debug: TIMER module_Need() : 0.164 ms - Total 0.164 ms / 1 intvls (Avg 0.164 ms)
[00000383] main decoder debug: thread started
[00000383] main decoder debug: thread 140098906597712 (decoder) created at priority 0 (input/decoder.c:217)
[00000380] dvdnav demux debug: buttonUpdate 1
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000379] main input debug: idx1=-1(??) idx2=-1(??)
[00000384] main decoder debug: looking for decoder module: 30 candidates
[00000384] main decoder debug: using decoder module "a52"
[00000384] main decoder debug: TIMER module_Need() : 0.216 ms - Total 0.216 ms / 1 intvls (Avg 0.216 ms)
[00000384] main decoder debug: thread 140098898205008 (decoder) created at priority 5 (input/decoder.c:217)
[00000384] main decoder debug: thread started
[00000384] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000384] main decoder debug: no aout present, spawning one
[00000385] main audio output debug: looking for audio output module: 3 candidates
[00000385] alsa audio output debug: opening ALSA device `default'
[00000385] main audio output debug: thread 140098807572816 (aout) created at priority 15 (alsa.c:687)
[00000385] main audio output debug: thread started
[00000385] main audio output debug: using audio output module "alsa"
[00000385] main audio output debug: TIMER module_Need() : 109.523 ms - Total 109.523 ms / 1 intvls (Avg 109.523 ms)
[00000385] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000385] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000385] main audio output debug: no need for any filter
[00000385] main audio output debug: looking for audio mixer module: 3 candidates
[00000385] main audio output debug: using audio mixer module "float32_mixer"
[00000385] main audio output debug: TIMER module_Need() : 0.143 ms - Total 0.143 ms / 1 intvls (Avg 0.143 ms)
[00000385] main audio output debug: input 'a52 ' 48000 Hz Stereo frame=1536 samples/768 bytes
[00000385] main audio output debug: filter(s) 'a52 '->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[00000386] main audio output debug: looking for audio filter module: 24 candidates
[00000386] main audio output debug: using audio filter module "a52tofloat32"
[00000386] main audio output debug: TIMER module_Need() : 0.586 ms - Total 0.586 ms / 1 intvls (Avg 0.586 ms)
[00000385] main audio output debug: found a filter for the whole conversion
[00000385] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000387] main audio output debug: looking for audio filter module: 24 candidates
[00000387] main audio output debug: using audio filter module "bandlimited_resampler"
[00000387] main audio output debug: TIMER module_Need() : 0.191 ms - Total 0.191 ms / 1 intvls (Avg 0.191 ms)
[00000385] main audio output debug: found a filter for the whole conversion
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000385] main audio output warning: output date isn't PTS date, requesting resampling (119495)
[00000385] main audio output warning: buffer is 119495 late, triggering upsampling
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000385] main audio output debug: audio output is starving (22455), playing silence
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000385] alsa audio output debug: recovered from buffer underrun
[00000385] main audio output warning: output date isn't PTS date, requesting resampling (74737)
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000385] main audio output warning: audio drift is too big (190669), dropping buffer
[00000385] main audio output warning: audio drift is too big (158669), dropping buffer
[00000385] main audio output warning: audio drift is too big (126669), dropping buffer
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000382] main decoder warning: no vout found, dropping subpicture
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000383] libmpeg2 decoder warning: invalid picture encountered
[00000366] main playlist debug: incoming request - stopping current input
[00000366] main playlist debug: dying input
[00000379] main input debug: control type=0
[00000379] main input debug: control: stopping input
[00000383] main decoder debug: removing module "libmpeg2"
[00000383] main decoder debug: thread ended
[00000378] qt4 interface debug: Updating the stream status: 8
[00000381] main generic debug: thread ended
[00000381] main generic debug: thread 140098923383120 joined (dvdnav.c:368)
[00000383] main decoder debug: thread 140098906597712 joined (input/decoder.c:248)
[00000383] main decoder debug: killing decoder fourcc `mpgv', 1 PES in FIFO
[00000382] main decoder debug: removing module "spudec"
[00000382] main decoder debug: thread ended
[00000382] main decoder debug: thread 140098914990416 joined (input/decoder.c:248)
[00000382] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[00000384] main decoder debug: removing module "a52"
[00000384] main decoder debug: thread ended
[00000384] main decoder debug: thread 140098898205008 joined (input/decoder.c:248)
[00000384] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[00000386] main audio output debug: removing module "a52tofloat32"
[00000387] main audio output debug: removing module "bandlimited_resampler"
[00000385] main audio output debug: thread ended
[00000385] main audio output debug: thread 140098807572816 joined (alsa.c:742)
[00000385] main audio output debug: removing module "alsa"
[00000385] main audio output debug: removing module "float32_mixer"
[00000379] main input debug: Program doesn't contain anymore ES
[00000380] main demux debug: removing module "dvdnav"
[00000379] main input debug: thread ended
[00000366] main playlist debug: dead input
[00000379] main input debug: thread 140098933909840 joined (playlist/engine.c:244)
[00000379] main input debug: TIMER input launching for 'dvd:///dev/sr0' : 68.448 ms - Total 68.448 ms / 1 intvls (Avg 68.448 ms)
```

---

### Post by vinutux on 2009-08-02
install vlc.10 fro here **[https://launchpad.net/~c-korn/+archive/vlc]("https://launchpad.net/~c-korn/+archive/vlc")**

and install libdvdcss2 from **[mediubunt repos]("www.medibuntu.org")**

---

### Post by mc4man on 2009-08-02
A couple of things
First totem-gstreamer is not worth wasting words in regards to dvd playback

By default vlc will attempt to start on dvd menu, that can be adjusted if you wish playback more like on a standalone dvd player

The jaunty repo version of 0.9.9a plays video in a separate window, your not getting it because the video output module is failing to load

The most likely cause is the video output module being used is unsuitable for your setup, either in general or as configured (display adapter, video drivers or lack of

Another possibility is an issue in that dvd's menu or vlc's settings

To test both, open vlc with fresh settings
```

vlc --reset-config --reset-plugins-cache
```

Then start the dvd from Media -> open disk and check the box 'No dvd menus' (dvdsimple), see if the video plays. (will bypass menu and start on main title

If not then try changing your video output from 'default' to something specific
Tools -> preferences, click on the video icon and in the Output box try X11 and or OpenGl - click save after changing
(the default is usually Xv, which while preferred, is the most resource/hardware dependent, though feel free to try specifically

Note that the audio output can also be a factor (and can affect video), your other posts seem to indicate you've been 'adjusting' that to some degree.

---

### Post by coldReactive on 2009-08-02
Thanks guys, but I found out that gxine actually plays the DVD fully, go figure.

---

