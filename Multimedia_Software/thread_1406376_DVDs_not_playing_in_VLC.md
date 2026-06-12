---
title: "DVDs not playing in VLC"
date: 2010-02-13
forum: Multimedia Software
---

### Post by Ubu_Fester on 2010-02-13
Help!

I have a fresh install of Ubuntu 9.10 on a new PC build, with all new components.  All software (except video programs) are working properly.  I can press music CDs from my DVD/CD writer.  I have installed what I believe are the most up to date video/dvd packages.  

I can play DVDs for only a short time.  DVDs play for about 5-10 minutes.  Spent about 5-6 hours on this for last 10 days.  

Using vlc from terminal (using "vlc -vv"), I get the following log:

ubu_fester@HTPC:~$ vlc -vv
VLC media player 1.0.2 Goldeneye
[0x83c9140] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x83c9140] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu2.1' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x83c9140] main libvlc debug: translation test: code is "C"
[0x83c9140] main libvlc debug: checking plugin modules
[0x83c9140] main libvlc debug: loading plugins cache file /home/ubu_fester/.cache/vlc/plugins-04041e.dat
[0x83c9140] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x83c9140] main libvlc debug: module bank initialized (379 modules)
[0x83c9140] main libvlc debug: opening config file (/home/ubu_fester/.config/vlc/vlcrc)
[0x83c9140] main libvlc debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT FPU 
[0x83c9140] main libvlc debug: looking for memcpy module: 4 candidates
[0x83c9140] main libvlc debug: using memcpy module "memcpymmxext"
[0x845e830] main input debug: Creating an input for 'Media Library'
[0x845e830] main input debug: Input is a meta file: disabling unneeded options
[0x845e830] main input debug: using timeshift granularity of 50 MBytes
[0x845e830] main input debug: using timeshift path '/tmp'
[0x845e830] main input debug: `file/xspf-open:///home/ubu_fester/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/ubu_fester/.local/share/vlc/ml.xspf'
[0x845e830] main input debug: creating demux: access='file' demux='xspf-open' path='/home/ubu_fester/.local/share/vlc/ml.xspf'
[0x84623b8] main demux debug: looking for access_demux module: 1 candidate
[0x84623b8] main demux warning: no access_demux module matching "file" could be loaded
[0x84623b8] main demux debug: TIMER module_need() : 0.342 ms - Total 0.342 ms / 1 intvls (Avg 0.342 ms)
[0x845e830] main input debug: creating access 'file' path='/home/ubu_fester/.local/share/vlc/ml.xspf'
[0x84623b8] main access debug: looking for access module: 3 candidates
[0x84623b8] access_file access debug: opening file `/home/ubu_fester/.local/share/vlc/ml.xspf'
[0x84623b8] main access debug: using access module "access_file"
[0x84623b8] main access debug: TIMER module_need() : 0.280 ms - Total 0.280 ms / 1 intvls (Avg 0.280 ms)
[0x846f108] main stream debug: Using AStream*Stream
[0x846f108] main stream debug: pre buffering
[0x846f108] main stream debug: received first data after 0 ms
[0x846f108] main stream debug: pre-buffering done 296 bytes in 0s - 32118 kbytes/s
[0x846f9c0] main stream debug: looking for stream_filter module: 4 candidates
[0x846f9c0] main stream debug: TIMER module_need() : 0.278 ms - Total 0.278 ms / 1 intvls (Avg 0.278 ms)
[0x8471c08] main stream debug: looking for stream_filter module: 1 candidate
[0x8471c08] main stream debug: using stream_filter module "stream_filter_record"
[0x8471c08] main stream debug: TIMER module_need() : 0.091 ms - Total 0.091 ms / 1 intvls (Avg 0.091 ms)
[0x845e830] main input debug: creating demux: access='file' demux='xspf-open' path='/home/ubu_fester/.local/share/vlc/ml.xspf'
[0x8470ef8] main demux debug: looking for demux module: 1 candidate
[0x8470ef8] playlist demux debug: using XSPF playlist reader
[0x8470ef8] main demux debug: using demux module "playlist"
[0x8470ef8] main demux debug: TIMER module_need() : 0.168 ms - Total 0.168 ms / 1 intvls (Avg 0.168 ms)
[0x845e830] main input debug: `file/xspf-open:///home/ubu_fester/.local/share/vlc/ml.xspf' successfully opened
[0x8474370] main xml debug: looking for xml module: 2 candidates
[0x8474370] main xml debug: using xml module "xtag"
[0x8474370] main xml debug: TIMER module_need() : 0.313 ms - Total 0.313 ms / 1 intvls (Avg 0.313 ms)
[0x8470ef8] playlist demux debug: parsed 0 tracks successfully
[0x8474370] main xml debug: removing module "xtag"
[0x845e830] main input debug: EOF reached
[0x8470ef8] main demux debug: removing module "playlist"
[0x8471c08] main stream debug: removing module "stream_filter_record"
[0x84623b8] main access debug: removing module "access_file"
[0x845e830] main input debug: TIMER input launching for 'Media Library' : 3.277 ms - Total 3.277 ms / 1 intvls (Avg 3.277 ms)
[0x845c6a8] main playlist debug: Activated
[0x845c6a8] main playlist debug: rebuilding array of current - root Playlist
[0x845c6a8] main playlist debug: rebuild done - 0 items, index -1
[0x846ef78] main interface debug: looking for interface module: 1 candidate
[0x846ef78] main interface debug: using interface module "hotkeys"
[0x846ef78] main interface debug: TIMER module_need() : 0.697 ms - Total 0.697 ms / 1 intvls (Avg 0.697 ms)
[0x846ef78] main interface debug: thread started
[0x846ef78] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0xb73004e8] main interface debug: looking for interface module: 1 candidate
[0xb73004e8] main interface debug: using interface module "inhibit"
[0xb73004e8] main interface debug: TIMER module_need() : 2.630 ms - Total 2.630 ms / 1 intvls (Avg 2.630 ms)
[0xb73004e8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0xb73004e8] main interface debug: thread started
[0x846de08] main interface debug: looking for interface module: 1 candidate
[0x846de08] main interface debug: using interface module "screensaver"
[0x846de08] main interface debug: TIMER module_need() : 0.442 ms - Total 0.442 ms / 1 intvls (Avg 0.442 ms)
[0x846de08] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x846de08] main interface debug: thread started
[0x8461c68] main interface debug: looking for interface module: 1 candidate
[0x8461c68] main interface debug: using interface module "signals"
[0x8461c68] main interface debug: TIMER module_need() : 0.379 ms - Total 0.379 ms / 1 intvls (Avg 0.379 ms)
[0x8461c68] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8461c68] main interface debug: thread started
[0x8461c68] main interface debug: thread ended
[0xb7300fa8] main interface debug: looking for interface module: 1 candidate
[0xb7300fa8] main interface debug: using interface module "globalhotkeys"
[0xb7300fa8] main interface debug: TIMER module_need() : 5.163 ms - Total 5.163 ms / 1 intvls (Avg 5.163 ms)
[0xb7300fa8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x83c9140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8473548] main interface debug: looking for interface module: 4 candidates
[0xb7300fa8] main interface debug: thread started
[0xb7300fa8] main interface debug: thread ended
[0x8473548] qt4 interface debug: Error while initializing qt-specific localization
[0x8473548] main interface debug: using interface module "qt4"
[0x8473548] main interface debug: TIMER module_need() : 129.178 ms - Total 129.178 ms / 1 intvls (Avg 129.178 ms)
[0x8473548] main interface debug: thread started
[0x8473548] main interface debug: thread ended
[0x8473548] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x845c6a8] main playlist debug: adding item `dvd:///dev/sr0' ( dvd:///dev/sr0 )
[0x8473548] qt4 interface debug: Adding a new MRL to recent ones: dvd:///dev/sr0
[0x845c6a8] main playlist debug: rebuilding array of current - root Playlist
[0x845c6a8] main playlist debug: rebuild done - 1 items, index -1
[0x845c6a8] main playlist debug: processing request item dvd:///dev/sr0 node null skip 0
[0x845c6a8] main playlist debug: resyncing on dvd:///dev/sr0
[0x845c6a8] main playlist debug: dvd:///dev/sr0 is at 0
[0x845c6a8] main playlist debug: starting new item
[0x845c6a8] main playlist debug: creating new input thread
[0x870a548] main input debug: Creating an input for 'dvd:///dev/sr0'
[0x870a548] main input debug: thread started
[0x870a548] main input debug: using timeshift granularity of 50 MBytes
[0x870a548] main input debug: using timeshift path '/tmp'
[0x870a548] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0x870a548] main input debug: `dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0'
[0x870a548] main input debug: creating demux: access='dvd' demux='' path='/dev/sr0'
[0x87078d0] main demux debug: looking for access_demux module: 2 candidates
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[0x8473548] qt4 interface debug: IM: Setting an input
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2D0E7F27
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ubu_fester/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000044e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00006a40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00030067
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002d46c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002d46e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003340c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003340e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0034b900
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0034b920
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0036d2a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0036d2c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003782a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003782c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003810c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003810e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00390520
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00390540
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x00397a80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00397aa0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0039d960
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0039d980
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003a3d00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003a3d20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003ae3e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003ae4a0
libdvdread: Elapsed time 0
libdvdread: Found 12 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
[0x87078d0] dvdnav demux debug: trying to go to dvd menu
libdvdnav: Suspected RCE Region Protection!!!
[0x87078d0] main demux debug: using access_demux module "dvdnav"
[0x87078d0] main demux debug: TIMER module_need() : 56.982 ms - Total 56.982 ms / 1 intvls (Avg 56.982 ms)
[0x870a548] main input debug: `dvd:///dev/sr0' successfully opened
[0x87078d0] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[0x870a548] main input error: ES_OUT_RESET_PCR called
[0x87078d0] dvdnav demux debug: DVDNAV_HIGHLIGHT
[0x87078d0] dvdnav demux debug:      - display=1
[0x87078d0] dvdnav demux debug:      - buttonN=5
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=5 t=0
[0x87078d0] dvdnav demux debug: DVDNAV_VTS_CHANGE
[0x87078d0] dvdnav demux debug:      - vtsN=1
[0x87078d0] dvdnav demux debug:      - domain=8
[0x870a548] main input error: ES_OUT_RESET_PCR called
[0x87078d0] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0x87078d0] dvdnav demux debug:      - cellN=1
[0x87078d0] dvdnav demux debug:      - pgN=1
[0x87078d0] dvdnav demux debug:      - cell_length=1650000
[0x87078d0] dvdnav demux debug:      - pg_length=1650000
[0x87078d0] dvdnav demux debug:      - pgc_length=23490000
[0x87078d0] dvdnav demux debug:      - cell_start=0
[0x87078d0] dvdnav demux debug:      - pg_start=0
[0x8473548] qt4 interface debug: Updating the geometry
[0x87078d0] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0x87078d0] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0x87078d0] dvdnav demux debug:      - physical_wide=0
[0x87078d0] dvdnav demux debug:      - physical_letterbox=0
[0x87078d0] dvdnav demux debug:      - physical_pan_scan=1
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=5 t=0
[0x870a548] main input debug: selecting program id=0
[0x8473548] qt4 interface debug: Title 30
[0x8473548] qt4 interface debug: Chapter: 7
[0xb7303060] main decoder debug: looking for decoder module: 31 candidates
[0x8473548] qt4 interface debug: New caching: 0
[0x8473548] qt4 interface debug: New caching: 0
[0xb7303060] avcodec decoder debug: libavcodec initialized (interface 0x341400)
[0xb7303060] main decoder debug: using decoder module "spudec"
[0xb7303060] main decoder debug: TIMER module_need() : 24.105 ms - Total 24.105 ms / 1 intvls (Avg 24.105 ms)
[0xb7306608] main packetizer debug: looking for packetizer module: 21 candidates
[0xb7306608] main packetizer debug: using packetizer module "spudec"
[0xb7306608] main packetizer debug: TIMER module_need() : 0.141 ms - Total 0.141 ms / 1 intvls (Avg 0.141 ms)
[0xb7303060] main decoder debug: thread started
[0xb7303060] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0xb7303060] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0xb7303060] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0x87078d0] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0x87078d0] dvdnav demux debug:      - physical=0
[0x870a548] main input debug: Buffering 0%
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=5 t=0
[0x870a548] main input debug: Buffering 0%
[0x87a4638] main decoder debug: looking for decoder module: 31 candidates
[0x87a4638] main decoder debug: using decoder module "libmpeg2"
[0x87a4638] main decoder debug: TIMER module_need() : 0.130 ms - Total 0.130 ms / 1 intvls (Avg 0.130 ms)
[0x87a4638] main decoder debug: thread started
[0x87a4638] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=5 t=0
[0x870a548] main input debug: Buffering 1%
[0x870a548] main input debug: Buffering 1%
[0x870a548] main input debug: Buffering 2%
[0x870a548] main input debug: Buffering 12%
[0x879f5a0] main decoder debug: looking for decoder module: 31 candidates
[0x879f5a0] main decoder debug: using decoder module "a52"
[0x879f5a0] main decoder debug: TIMER module_need() : 0.252 ms - Total 0.252 ms / 1 intvls (Avg 0.252 ms)
[0x879f5a0] main decoder debug: thread started
[0x87a4638] libmpeg2 decoder debug: 720x480 (display 540,480), aspect 768000, sar 0:0, 29.971 fps
[0x870a548] main input debug: no usable vout present, spawning one
[0x87686e8] main spu text debug: looking for text renderer module: 2 candidates
[0x87c92d0] main generic debug: thread started
[0x87c92d0] freetype generic debug: Building font database...
[0x87c92d0] freetype generic debug: Finished building font database.
[0x87c92d0] freetype generic debug: Took 344 microseconds
[0x879f5a0] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0x870a548] main input debug: Buffering 13%
[0x870a548] main input debug: Buffering 24%
[0x870a548] main input debug: Buffering 45%
[0x870a548] main input debug: Buffering 66%
[0x870a548] main input debug: Buffering 80%
[0x870a548] main input debug: Buffering 98%
[0x870a548] main input debug: Stream buffering done (359 ms in 7 ms)
[0x879f5a0] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x87c92d0] main generic debug: thread (fontlist builder) created at priority 0 (freetype.c:475)
[0x87686e8] freetype spu text debug: using fontsize: 2
[0x87686e8] main spu text debug: using text renderer module "freetype"
[0x87686e8] main spu text debug: TIMER module_need() : 4.482 ms - Total 4.482 ms / 1 intvls (Avg 4.482 ms)
[0x87d7930] main scale debug: looking for video filter2 module: 17 candidates
[0x87d7930] swscale scale debug: 32x32 chroma: YUVA -> 16x16 chroma: YUVA with scaling using Bicubic (good quality)
[0x87d7930] main scale debug: using video filter2 module "swscale"
[0x87d7930] main scale debug: TIMER module_need() : 1.387 ms - Total 1.387 ms / 1 intvls (Avg 1.387 ms)
[0x87cb460] main scale debug: looking for video filter2 module: 17 candidates
[0x87cb460] yuvp scale debug: YUVP to YUVA converter
[0x87cb460] main scale debug: using video filter2 module "yuvp"
[0x87cb460] main scale debug: TIMER module_need() : 1.093 ms - Total 1.093 ms / 1 intvls (Avg 1.093 ms)
[0x87bbd00] main video output debug: window size: 853x480
[0x87bbd00] main video output debug: looking for video output module: 6 candidates
[0x87c92d0] main generic debug: thread ended
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: New caching: 100
[0x8473548] qt4 interface debug: New caching: 100
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x87bbd00] xvideo video output debug: adaptor 0, port 283, format 0x32315659 (YV12) planar
[0xb73399f0] main window debug: looking for xwindow module: 3 candidates
[0xb73399f0] qt4 window debug: requesting video...
[0x8473548] qt4 interface debug: Video was requested -1, -1
[0x8473548] qt4 interface debug: Video is resizing to: 853 480
[0x8473548] qt4 interface debug: Updating the geometry
[0xb73399f0] main window debug: using xwindow module "qt4"
[0xb73399f0] main window debug: TIMER module_need() : 14.696 ms - Total 14.696 ms / 1 intvls (Avg 14.696 ms)
[0x87bbd00] xvideo video output debug: XShm video extension v1.1 (without pixmaps, opcode: 142)
[0x87bbd00] xvideo video output debug: Window manager supports NetWM
[0x87bbd00] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[0x87bbd00] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[0x87bbd00] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[0x87bbd00] main video output debug: using video output module "xvideo"
[0x87bbd00] main video output debug: TIMER module_need() : 179.579 ms - Total 179.579 ms / 1 intvls (Avg 179.579 ms)
[0x87bbd00] main video output debug: Deinterlacing available
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x87bbd00] main video output debug: got 16 direct buffer(s)
[0x87bbd00] main video output debug: pic render sz 720x480, of (0,0), vsz 720x480, 4cc I420, ar 16:9, sar 32:27, msk r0x0 g0x0 b0x0
[0x87bbd00] main video output debug: pic in sz 720x480, of (0,0), vsz 720x480, 4cc I420, ar 16:9, sar 32:27, msk r0x0 g0x0 b0x0
[0x87bbd00] main video output debug: pic out sz 720x480, of (0,0), vsz 720x480, 4cc I420, ar 16:9, sar 32:27, msk r0x0 g0x0 b0x0
[0x87bbd00] main video output debug: direct render, mapping render pictures 0-14 to system pictures 1-15
[0x87bbd00] qt4 video output debug: Qt: Entering Fullscreen
[0x870a548] main input debug: creating aout
[0x86ecca8] main audio output debug: looking for audio output module: 5 candidates
[0x86ecca8] pulse audio output: No. of Audio Channels: 2
[0x87a4638] main decoder warning: backward_pts != current_pts (-33367)
[0x87a4638] main decoder debug: End of video preroll
[0x87a4638] main decoder debug: Received first picture
[0x87686e8] freetype spu text debug: using fontsize: 30
[0x888f378] main blend debug: looking for video blending module: 1 candidate
[0x888f378] blend blend debug: chroma: YUVA -> I420
[0x888f378] main blend debug: using video blending module "blend"
[0x888f378] main blend debug: TIMER module_need() : 0.275 ms - Total 0.275 ms / 1 intvls (Avg 0.275 ms)
[0x86ecca8] pulse audio output debug: Pulse mainloop started
[0x86ecca8] pulse audio output debug: Pulse stream connected
[0x86ecca8] pulse audio output debug: Pulse initialized successfully
[0x86ecca8] pulse audio output debug: Buffer metrics: maxlength=153600, tlength=46080, prebuf=38400, minreq=7680
[0x86ecca8] pulse audio output debug: Using sample spec 'float32le 2ch 48000Hz', channel map 'front-left,front-right'.
[0x86ecca8] pulse audio output debug: Connected to device alsa_output.pci-0000_00_07.0.analog-stereo (0, not suspended).
[0x86ecca8] main audio output debug: using audio output module "pulse"
[0x86ecca8] main audio output debug: TIMER module_need() : 109.409 ms - Total 109.409 ms / 1 intvls (Avg 109.409 ms)
[0x86ecca8] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[0x86ecca8] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[0x86ecca8] main audio output debug: no need for any filter
[0x86ecca8] main audio output debug: looking for audio mixer module: 3 candidates
[0x86ecca8] main audio output debug: using audio mixer module "float32_mixer"
[0x86ecca8] main audio output debug: TIMER module_need() : 0.592 ms - Total 0.592 ms / 1 intvls (Avg 0.592 ms)
[0x86ecca8] main audio output debug: input 'a52 ' 48000 Hz Stereo frame=1536 samples/768 bytes
[0x887f6c0] main audio filter debug: looking for audio filter module: 1 candidate
[0x887f6c0] scaletempo audio filter warning: bad input or output format
[0x887f6c0] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x887f6c0] main audio filter debug: TIMER module_need() : 0.529 ms - Total 0.529 ms / 1 intvls (Avg 0.529 ms)
[0x887f6c0] main audio filter debug: looking for audio filter module: 1 candidate
[0x887f6c0] scaletempo audio filter debug: format: 48000 rate, 2 nch, 4 bps, fl32
[0x887f6c0] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0x887f6c0] scaletempo audio filter debug: 1.000 scale, 1440.000 stride_in, 1440 stride_out, 1152 standing, 288 overlap, 672 search, 2400 queue, fl32 mode
[0x887f6c0] main audio filter debug: using audio filter module "scaletempo"
[0x887f6c0] main audio filter debug: TIMER module_need() : 0.493 ms - Total 0.493 ms / 1 intvls (Avg 0.493 ms)
[0x86ecca8] main audio output debug: filter(s) 'a52 '->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[0x8889060] main audio output debug: looking for audio filter module: 24 candidates
[0x8889060] main audio output debug: using audio filter module "a52tofloat32"
[0x8889060] main audio output debug: TIMER module_need() : 1.966 ms - Total 1.966 ms / 1 intvls (Avg 1.966 ms)
[0x86ecca8] main audio output debug: found a filter for the whole conversion
[0x86ecca8] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[0x8889f00] main audio output debug: looking for audio filter module: 24 candidates
[0x8889f00] main audio output debug: using audio filter module "bandlimited_resampler"
[0x8889f00] main audio output debug: TIMER module_need() : 1.627 ms - Total 1.627 ms / 1 intvls (Avg 1.627 ms)
[0x86ecca8] main audio output debug: found a filter for the whole conversion
[0x879f5a0] main decoder debug: End of audio preroll
[0x870a548] main input debug: Decoder buffering done in 331 ms
[0x86ecca8] pulse audio output debug: Pulse stream started
[0x86ecca8] main audio output warning: output date isn't PTS date, requesting resampling (124428)
[0x86ecca8] main audio output warning: audio drift is too big (124428), dropping buffer
[0x86ecca8] main audio output warning: buffer is 92428 late, triggering upsampling
[0x86ecca8] main audio output warning: resampling stopped after 17049046 usec (drift: 677)
[0x87078d0] dvdnav demux debug: DVDNAV_NOP
[0x87078d0] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0x87078d0] dvdnav demux debug:      - cellN=2
[0x87078d0] dvdnav demux debug:      - pgN=2
[0x87078d0] dvdnav demux debug:      - cell_length=10350000
[0x87078d0] dvdnav demux debug:      - pg_length=10350000
[0x87078d0] dvdnav demux debug:      - pgc_length=23490000
[0x87078d0] dvdnav demux debug:      - cell_start=1650000
[0x87078d0] dvdnav demux debug:      - pg_start=1650000
[0x87078d0] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0x87078d0] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0x87078d0] dvdnav demux debug:      - physical_wide=0
[0x87078d0] dvdnav demux debug:      - physical_letterbox=0
[0x87078d0] dvdnav demux debug:      - physical_pan_scan=1
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=5 t=0
[0xb7303060] main decoder debug: removing module "spudec"
[0xb7303060] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[0xb7306608] main packetizer debug: removing module "spudec"
[0x8767130] main decoder debug: looking for decoder module: 31 candidates
[0x8767130] avcodec decoder debug: libavcodec already initialized
[0x8767130] main decoder debug: using decoder module "spudec"
[0x8767130] main decoder debug: TIMER module_need() : 1.690 ms - Total 1.690 ms / 1 intvls (Avg 1.690 ms)
[0x8473548] qt4 interface debug: Updating the geometry
[0x889db40] main packetizer debug: looking for packetizer module: 21 candidates
[0x889db40] main packetizer debug: using packetizer module "spudec"
[0x889db40] main packetizer debug: TIMER module_need() : 1.017 ms - Total 1.017 ms / 1 intvls (Avg 1.017 ms)
[0x8767130] main decoder debug: thread started
[0x8767130] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x87078d0] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0x87078d0] dvdnav demux debug:      - physical=0
[0x870a548] main input debug: crop: 319,354,65,83, palette forced: 1
[0x87078d0] dvdnav demux debug: buttonUpdate 5
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x870a548] main input debug: idx1=-1(??) idx2=-1(??)
[0x8473548] qt4 interface debug: Updating the geometry
[0x87078d0] dvdnav demux debug: DVDNAV_HIGHLIGHT
[0x87078d0] dvdnav demux debug:      - display=1
[0x87078d0] dvdnav demux debug:      - buttonN=6
[0x870a548] main input debug: crop: 377,324,31,28, palette forced: 1
[0x87078d0] dvdnav demux debug: buttonUpdate 6
[0x87078d0] dvdnav demux debug: DVDNAV_HIGHLIGHT
[0x87078d0] dvdnav demux debug:      - display=1
[0x87078d0] dvdnav demux debug:      - buttonN=5
[0x870a548] main input debug: crop: 319,354,65,83, palette forced: 1
[0x87078d0] dvdnav demux debug: buttonUpdate 5
[0x870a548] main input debug: crop: 319,354,65,83, palette forced: 1
[0x87078d0] dvdnav demux debug: buttonUpdate 5
[0x87078d0] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[0x870a548] main input error: ES_OUT_RESET_PCR called
[0x8767130] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0x8473548] qt4 interface debug: New caching: 0
[0x8767130] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0x8473548] qt4 interface debug: New caching: 0
[0x87078d0] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0x87078d0] dvdnav demux debug:      - cellN=8
[0x87078d0] dvdnav demux debug:      - pgN=8
[0x87078d0] dvdnav demux debug:      - cell_length=270000
[0x87078d0] dvdnav demux debug:      - pg_length=270000
[0x87078d0] dvdnav demux debug:      - pgc_length=23490000
[0x87078d0] dvdnav demux debug:      - cell_start=22950000
[0x87078d0] dvdnav demux debug:      - pg_start=22950000
[0x87078d0] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0x87078d0] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0x87078d0] dvdnav demux debug:      - physical_wide=0
[0x87078d0] dvdnav demux debug:      - physical_letterbox=0
[0x87078d0] dvdnav demux debug:      - physical_pan_scan=1
[0x870a548] main input debug: crop: 319,354,65,83, palette forced: 1
[0x87078d0] dvdnav demux debug: buttonUpdate 5
[0x8767130] main decoder debug: removing module "spudec"
[0x8767130] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[0x889db40] main packetizer debug: removing module "spudec"
[0x8767130] main decoder debug: looking for decoder module: 31 candidates
[0x8767130] avcodec decoder debug: libavcodec already initialized
[0x8767130] main decoder debug: using decoder module "spudec"
[0x8767130] main decoder debug: TIMER module_need() : 1.526 ms - Total 1.526 ms / 1 intvls (Avg 1.526 ms)
[0x889db40] main packetizer debug: looking for packetizer module: 21 candidates
[0x889db40] main packetizer debug: using packetizer module "spudec"
[0x889db40] main packetizer debug: TIMER module_need() : 0.320 ms - Total 0.320 ms / 1 intvls (Avg 0.320 ms)
[0x8767130] main decoder debug: thread started
[0x8767130] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x8767130] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0x8767130] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0x87078d0] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0x87078d0] dvdnav demux debug:      - physical=0
[0x870a548] main input debug: Buffering 0%
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=5 t=0
[0x870a548] main input debug: Buffering 27%
[0x870a548] main input debug: Buffering 28%
[0x870a548] main input debug: Buffering 28%
[0x870a548] main input debug: Buffering 29%
--more--

[0x870a548] main input debug: Buffering 83%
[0x870a548] main input debug: Buffering 83%
[0x870a548] main input debug: Buffering 85%
[0x87a4638] main decoder warning: backward_pts != dts (218618400)
[0x870a548] main input debug: Buffering 92%
[0x87a4638] main decoder warning: backward_pts != current_pts (-33368)
[0x870a548] main input debug: Buffering 92%
[0x870a548] main input debug: Buffering 93%
[0x870a548] main input debug: Buffering 93%
[0x870a548] main input debug: Buffering 94%
[0x870a548] main input debug: Buffering 94%
[0x870a548] main input debug: Buffering 98%
[0x870a548] main input debug: Buffering 98%
[0x870a548] main input debug: Buffering 99%
[0x870a548] main input debug: Buffering 99%
[0x870a548] main input debug: Stream buffering done (301 ms in 6 ms)
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: New caching: 100
[0x8473548] qt4 interface debug: New caching: 100
[0x879f5a0] main decoder debug: End of audio preroll
[0x87a4638] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x87a4638] main decoder warning: backward_pts != current_pts (-218618401)
[0x87a4638] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x87a4638] main decoder debug: End of video preroll
[0x87a4638] main decoder debug: Received first picture
[0x870a548] main input debug: Decoder buffering done in 37 ms
[0x86ecca8] main audio output warning: the mixer got a packet in the past (70004)
[0x86ecca8] main audio output warning: the mixer got a packet in the past (38004)
[0x86ecca8] main audio output warning: the mixer got a packet in the past (6004)
[0x86ecca8] main audio output warning: mixer start isn't output start (2305)
[0x87078d0] dvdnav demux debug: DVDNAV_NOP
[0x87078d0] dvdnav demux debug: DVDNAV_HIGHLIGHT
[0x87078d0] dvdnav demux debug:      - display=1
[0x87078d0] dvdnav demux debug:      - buttonN=1
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=1 t=1
[0x87078d0] dvdnav demux debug: DVDNAV_VTS_CHANGE
[0x87078d0] dvdnav demux debug:      - vtsN=1
[0x87078d0] dvdnav demux debug:      - domain=2
[0x870a548] main input error: ES_OUT_RESET_PCR called
[0x8767130] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0x8767130] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0x8473548] qt4 interface debug: New caching: 0
[0x8473548] qt4 interface debug: New caching: 0
[0x87a4638] main decoder debug: removing module "libmpeg2"
[0x87a4638] main decoder debug: killing decoder fourcc `mpgv', 0 PES in FIFO
[0x87bbd00] main video output debug: [0] 2 0
[0x87bbd00] main video output debug: [1] 2 0
[0x87bbd00] main video output debug: [2] 2 0
[0x87bbd00] main video output debug: [3] 2 0
[0x87bbd00] main video output debug: [4] 4 0
[0x87bbd00] main video output debug: [5] 2 0
[0x87bbd00] main video output debug: [6] 4 0
[0x87bbd00] main video output debug: [7] 4 0
[0x87bbd00] main video output debug: [8] 4 0
[0x87bbd00] main video output debug: [9] 4 0
[0x87bbd00] main video output debug: [10] 2 0
[0x87bbd00] main video output debug: [11] 4 0
[0x87bbd00] main video output debug: [12] 2 0
[0x87bbd00] main video output debug: [13] 2 0
[0x87bbd00] main video output debug: [14] 2 0
[0x870a548] main input debug: saving a free vout
[0x8767130] main decoder debug: removing module "spudec"
[0x8767130] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[0x889db40] main packetizer debug: removing module "spudec"
[0x879f5a0] main decoder debug: removing module "a52"
[0x879f5a0] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[0x8889060] main audio output debug: removing module "a52tofloat32"
[0x887f6c0] main audio filter debug: removing module "scaletempo"
[0x8889f00] main audio output debug: removing module "bandlimited_resampler"
[0x86ecca8] pulse audio output debug: Pulse Close
[0x87bbd00] qt4 video output debug: Qt: Entering Fullscreen
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x86ecca8] main audio output debug: removing module "pulse"
[0x86ecca8] main audio output debug: removing module "float32_mixer"
[0x870a548] main input debug: releasing aout
[0x870a548] main input debug: Program doesn't contain anymore ES
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x87078d0] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0x87078d0] dvdnav demux debug:      - cellN=1
[0x87078d0] dvdnav demux debug:      - pgN=1
[0x87078d0] dvdnav demux debug:      - cell_length=35037000
[0x87078d0] dvdnav demux debug:      - pg_length=35037000
[0x87078d0] dvdnav demux debug:      - pgc_length=653916000
[0x87078d0] dvdnav demux debug:      - cell_start=0
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Title 30
[0x8473548] qt4 interface debug: Chapter: 28
[0x87078d0] dvdnav demux debug:      - pg_start=0
[0x87078d0] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0x87078d0] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0x87078d0] dvdnav demux debug:      - physical_wide=128
[0x87078d0] dvdnav demux debug:      - physical_letterbox=128
[0x87078d0] dvdnav demux debug:      - physical_pan_scan=128
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=1 t=1
[0x87078d0] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0x87078d0] dvdnav demux debug:      - physical=0
[0x870a548] main input debug: Buffering 0%
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=1 t=1
[0x870a548] main input warning: clock gap, unexpected stream discontinuity
[0x870a548] main input warning: feeding synchro with a new reference point trying to recover from clock gap
[0x870a548] main input debug: Buffering 0%
[0x879f5a0] main decoder debug: looking for decoder module: 31 candidates
[0x879f5a0] main decoder debug: using decoder module "libmpeg2"
[0x879f5a0] main decoder debug: TIMER module_need() : 0.747 ms - Total 0.747 ms / 1 intvls (Avg 0.747 ms)
[0x879f5a0] main decoder debug: thread started
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x879f5a0] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x87078d0] dvdnav demux debug: buttonUpdate not done b=1 t=1
[0x87078d0] dvdnav demux warning: cannot get next block (Error reading from DVD.)
[0x879f5a0] libmpeg2 decoder debug: 720x480 (display 540,480), aspect 768000, sar 0:0, 29.971 fps
[0x845c6a8] main playlist debug: finished input
[0x870a548] main input debug: trying to reuse free vout
[0x870a548] main input debug: reusing provided vout
[0x879f5a0] main decoder warning: can't get output picture
[0x879f5a0] main decoder debug: removing module "libmpeg2"
[0x879f5a0] main decoder debug: killing decoder fourcc `mpgv', 0 PES in FIFO
[0x87bbd00] main video output debug: [0] 4 0
[0x87bbd00] main video output debug: [1] 4 0
[0x87bbd00] main video output debug: [2] 4 0
[0x87bbd00] main video output debug: [3] 4 0
[0x87bbd00] main video output debug: [4] 4 0
[0x87bbd00] main video output debug: [5] 4 0
[0x87bbd00] main video output debug: [6] 4 0
[0x87bbd00] main video output debug: [7] 4 0
[0x87bbd00] main video output debug: [8] 4 0
[0x87bbd00] main video output debug: [9] 4 0
[0x87bbd00] main video output debug: [10] 4 0
[0x87bbd00] main video output debug: [11] 4 0
[0x87bbd00] main video output debug: [12] 2 0
[0x87bbd00] main video output debug: [13] 4 0
[0x87bbd00] main video output debug: [14] 4 0
[0x870a548] main input debug: saving a free vout
[0x870a548] main input debug: Program doesn't contain anymore ES
[0x87078d0] main demux debug: removing module "dvdnav"
[0x870a548] main input debug: thread ended
[0x845c6a8] main playlist debug: dead input
[0x845c6a8] main playlist debug: changing item without a request (current 0/1)
[0x845c6a8] main playlist debug: nothing to play
[0x87bbd00] main video output debug: destroying useless vout
[0x8473548] qt4 interface debug: IM: Deleting the input
[0x8473548] qt4 interface debug: Updating the geometry
[0x8473548] qt4 interface debug: Updating the geometry
[0x870a548] main input debug: TIMER input launching for 'dvd:///dev/sr0' : 61.167 ms - Total 61.167 ms / 1 intvls (Avg 61.167 ms)
[0xb73399f0] qt4 window debug: releasing video...
[0x8473548] qt4 interface debug: Video is not needed anymore
[0x8473548] qt4 interface debug: Updating the geometry
[0xb73399f0] main window debug: removing module "qt4"
[0x87bbd00] main video output debug: removing module "xvideo"
[0x888f378] main blend debug: removing module "blend"
[0x87686e8] main spu text debug: removing module "freetype"
[0x87cb460] main scale debug: removing module "yuvp"
[0x87d7930] main scale debug: removing module "swscale"

---

### Post by Ubu_Fester on 2011-01-29
I upgraded to a new video card, and DVDs now play correctly.

---

