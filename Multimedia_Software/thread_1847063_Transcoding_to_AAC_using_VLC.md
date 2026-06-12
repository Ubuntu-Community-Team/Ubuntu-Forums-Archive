---
title: "Transcoding to AAC using VLC"
date: 2011-09-20
forum: Multimedia Software
---

### Post by eremos on 2011-09-20
Hi all,

I've had this issue for months and have finally reached the end of my rope and am asking for help.

I was using VLC to stream movies to my Android phone (using VLC Stream & Convert) and it was working great until I upgraded to Natty.

Unfortunately I can't remember exactly how it was set up when I was on the earlier version (I think it was Maverick but I'm not sure).

I'm using 64-bit natty.

Here's the -vv output of vlc:
```
media@hex:~$ vlc -vv -I http
VLC media player 1.1.9 The Luggage (revision exported)
[0x1288120] main libvlc debug: VLC media player - 1.1.9 The Luggage
[0x1288120] main libvlc debug: Copyright Â© 1996-2011 the VideoLAN team
[0x1288120] main libvlc debug: revision exported
[0x1288120] main libvlc debug: configured with ./configure  '--enable-static' '--build=x86_64-linux-gnu' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--sysconfdir=/etc' '--with-binary-version=1ubuntu1.3' '--enable-a52' '--enable-aa' '--enable-bonjour' '--enable-caca' '--enable-dca' '--enable-dirac' '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-ggi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libmpeg2' '--enable-libproxy' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mozilla' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-pulse' '--enable-qt4' '--enable-realrtsp' '--enable-schroedinger' '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--with-mozilla-pkg=libxul' '--disable-dxva2' '--disable-gnomevfs' '--disable-goom' '--disable-osso_screensaver' '--disable-portaudio' '--disable-projectm' '--disable-sqlite' '--disable-telx' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv' '--enable-libva' '--enable-pvr' '--enable-udev' '--enable-v4l2' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x1288120] main libvlc debug: translation test: code is "C"
[0x1288120] main libvlc debug: checking plugin modules
[0x1288120] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins-04081e-1f8.dat
[0x1288120] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x1288120] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins-04081e-1f8.dat
[0x1288120] main libvlc debug: module bank initialized (370 modules)
[0x1288120] main libvlc debug: opening config file (/mnt/tank/home/media/.config/vlc/vlcrc)
[0x1288120] main libvlc debug: CPU has capabilities MMX 3DNow! MMXEXT SSE SSE2 SSE3 FPU
[0x1288120] main libvlc debug: looking for memcpy module: 4 candidates
[0x1288120] main libvlc debug: using memcpy module "memcpymmxext"
[0x1371330] main input debug: Creating an input for 'Media Library'
[0x1371330] main input debug: Input is a meta file: disabling unneeded options
[0x1371330] main input debug: using timeshift granularity of 50 MiB
[0x1371330] main input debug: using timeshift path '/tmp'
[0x1371330] main input debug: `file/xspf-open:///mnt/tank/home/media/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/mnt/tank/home/media/.local/share/vlc/ml.xspf'
[0x1371330] main input debug: creating demux: access='file' demux='xspf-open' path='/mnt/tank/home/media/.local/share/vlc/ml.xspf'
[0x136b8a0] main demux debug: looking for access_demux module: 2 candidates
[0x136b8a0] main demux debug: no access_demux module matching "file" could be loaded
[0x136b8a0] main demux debug: TIMER module_need() : 0.854 ms - Total 0.854 ms / 1 intvls (Avg 0.854 ms)
[0x1371330] main input debug: creating access 'file' path='/mnt/tank/home/media/.local/share/vlc/ml.xspf'
[0x136eb60] main access debug: looking for access module: 2 candidates
[0x136eb60] filesystem access debug: opening file `/mnt/tank/home/media/.local/share/vlc/ml.xspf'
[0x136eb60] main access debug: using access module "filesystem"
[0x136eb60] main access debug: TIMER module_need() : 0.429 ms - Total 0.429 ms / 1 intvls (Avg 0.429 ms)
[0x136cf60] main stream debug: Using AStream*Stream
[0x136cf60] main stream debug: pre buffering
[0x136cf60] main stream debug: received first data after 0 ms
[0x136cf60] main stream debug: pre-buffering done 296 bytes in 0s - 17003 KiB/s
[0x136d1d0] main stream debug: looking for stream_filter module: 5 candidates
[0x136d1d0] main stream debug: no stream_filter module matching "any" could be loaded
[0x136d1d0] main stream debug: TIMER module_need() : 0.641 ms - Total 0.641 ms / 1 intvls (Avg 0.641 ms)
[0x136d1d0] main stream debug: looking for stream_filter module: 1 candidate
[0x136d1d0] main stream debug: using stream_filter module "stream_filter_record"
[0x136d1d0] main stream debug: TIMER module_need() : 0.219 ms - Total 0.219 ms / 1 intvls (Avg 0.219 ms)
[0x1371330] main input debug: creating demux: access='file' demux='xspf-open' path='/mnt/tank/home/media/.local/share/vlc/ml.xspf'
[0x1381100] main demux debug: looking for demux module: 1 candidate
[0x1381100] playlist demux debug: using XSPF playlist reader
[0x1381100] main demux debug: using demux module "playlist"
[0x1381100] main demux debug: TIMER module_need() : 0.404 ms - Total 0.404 ms / 1 intvls (Avg 0.404 ms)
[0x1384fd0] main demux meta debug: looking for meta reader module: 2 candidates
[0x1384fd0] lua demux meta debug: Trying Lua scripts in /mnt/tank/home/media/.local/share/vlc/lua/meta/reader
[0x1384fd0] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x1384fd0] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x1384fd0] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x1384fd0] main demux meta debug: no meta reader module matching "any" could be loaded
[0x1384fd0] main demux meta debug: TIMER module_need() : 2458.512 ms - Total 2458.512 ms / 1 intvls (Avg 2458.512 ms)
[0x1371330] main input debug: `file/xspf-open:///mnt/tank/home/media/.local/share/vlc/ml.xspf' successfully opened
[0x1384fd0] main xml debug: looking for xml module: 2 candidates
[0x1384fd0] main xml debug: using xml module "xml"
[0x1384fd0] main xml debug: TIMER module_need() : 673.914 ms - Total 673.914 ms / 1 intvls (Avg 673.914 ms)
[0x1381100] playlist demux debug: parsed 0 tracks successfully
[0x1384fd0] main xml debug: removing module "xml"
[0x1371330] main input debug: EOF reached
[0x1381100] main demux debug: removing module "playlist"
[0x136d1d0] main stream debug: removing module "stream_filter_record"
[0x136eb60] main access debug: removing module "filesystem"
[0x1371330] main input debug: TIMER input launching for 'Media Library' : 2461.730 ms - Total 2461.730 ms / 1 intvls (Avg 2461.730 ms)
[0x1371510] main interface debug: looking for interface module: 1 candidate
[0x1371510] main interface debug: using interface module "hotkeys"
[0x1371510] main interface debug: TIMER module_need() : 0.355 ms - Total 0.355 ms / 1 intvls (Avg 0.355 ms)
[0x138c690] main interface debug: looking for interface module: 1 candidate
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x138c690] inhibit interface error: Failed to connect to the D-Bus session daemon: //bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0x138c690] main interface debug: no interface module matching "inhibit,none" could be loaded
[0x138c690] main interface debug: TIMER module_need() : 4028.525 ms - Total 4028.525 ms / 1 intvls (Avg 4028.525 ms)
[0x138c690] main interface error: no suitable interface module
[0x1369940] main interface debug: looking for interface module: 1 candidate
[0x1369940] main interface debug: using interface module "signals"
[0x1369940] main interface debug: TIMER module_need() : 0.805 ms - Total 0.805 ms / 1 intvls (Avg 0.805 ms)
[0x13728c0] main interface debug: looking for interface module: 0 candidates
[0x13728c0] main interface debug: no interface module matched "globalhotkeys,none"
[0x13728c0] main interface debug: TIMER module_need() : 0.133 ms - Total 0.133 ms / 1 intvls (Avg 0.133 ms)
[0x13728c0] main interface error: no suitable interface module
[0x1288120] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x1372c50] main interface debug: looking for interface module: 1 candidate
[0x137eec0] main playlist debug: Activated
[0x1372c50] oldhttp interface debug: base :8080
[0x1372c50] main interface: creating httpd
[0x1372c50] main interface debug: net: listening to  port 8080
[0x137eec0] main playlist debug: rebuilding array of current - root Playlist
[0x137eec0] main playlist debug: rebuild done - 0 items, index -1
[0x1372c50] oldhttp interface debug: dir=/usr/share/vlc/http
[0x1372c50] main interface debug: find .hosts in dir=/usr/share/vlc/http/.hosts
[0x1372c50] main interface debug: restricted to ::1
[0x1372c50] main interface debug: restricted to 127.0.0.1
[0x1372c50] oldhttp interface debug: dir=/usr/share/vlc/http/requests
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/requests/playlist.xml (url=/requests/playlist.xml)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/requests/status.xml (url=/requests/status.xml)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/requests/browse.xml (url=/requests/browse.xml)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/requests/readme (url=/requests/readme)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/requests/vlm.xml (url=/requests/vlm.xml)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/requests/vlm_cmd.xml (url=/requests/vlm_cmd.xml)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/index.html (url=/)
[0x1372c50] oldhttp interface debug: redir= -> /
[0x1372c50] oldhttp interface debug: redir=/index.html -> /
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/style.css (url=/style.css)
[0x1372c50] oldhttp interface debug: dir=/usr/share/vlc/http/js
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/js/vlm.js (url=/js/vlm.js)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/js/functions.js (url=/js/functions.js)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/js/mosaic.js (url=/js/mosaic.js)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/iehacks.css (url=/iehacks.css)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/favicon.ico (url=/favicon.ico)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/vlm.html (url=/vlm.html)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/flash.html (url=/flash.html)
[0x1372c50] oldhttp interface debug: dir=/usr/share/vlc/http/images
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/white_cross_small.png (url=/images/white_cross_small.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/stop.png (url=/images/stop.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/volume_down.png (url=/images/volume_down.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/empty.png (url=/images/empty.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/slider_bar.png (url=/images/slider_bar.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/white.png (url=/images/white.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/eject.png (url=/images/eject.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/speaker.png (url=/images/speaker.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/slider_point.png (url=/images/slider_point.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/shuffle.png (url=/images/shuffle.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/snapshot.png (url=/images/snapshot.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/speaker_mute.png (url=/images/speaker_mute.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/slider_left.png (url=/images/slider_left.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/play.png (url=/images/play.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/playlist.png (url=/images/playlist.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/delete_small.png (url=/images/delete_small.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/playlist_small.png (url=/images/playlist_small.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/sort.png (url=/images/sort.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/sout.png (url=/images/sout.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/pause.png (url=/images/pause.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/sd.png (url=/images/sd.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/vlc16x16.png (url=/images/vlc16x16.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/slider_right.png (url=/images/slider_right.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/fullscreen.png (url=/images/fullscreen.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/next.png (url=/images/next.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/slow.png (url=/images/slow.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/loop.png (url=/images/loop.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/info.png (url=/images/info.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/plus.png (url=/images/plus.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/refresh.png (url=/images/refresh.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/prev.png (url=/images/prev.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/repeat.png (url=/images/repeat.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/delete.png (url=/images/delete.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/help.png (url=/images/help.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/volume_up.png (url=/images/volume_up.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/images/minus.png (url=/images/minus.png)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/vlm_export.html (url=/vlm_export.html)
[0x1372c50] oldhttp interface debug: dir=/usr/share/vlc/http/dialogs
[0x1372c50] main interface debug: find .hosts in dir=/usr/share/vlc/http/dialogs/.hosts
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/dialogs/vlm (url=/dialogs/vlm)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/dialogs/input (url=/dialogs/input)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/dialogs/playlist (url=/dialogs/playlist)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/dialogs/browse (url=/dialogs/browse)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/dialogs/sout (url=/dialogs/sout)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/dialogs/main (url=/dialogs/main)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/dialogs/footer (url=/dialogs/footer)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/dialogs/mosaic (url=/dialogs/mosaic)
[0x1372c50] oldhttp interface debug: file=/usr/share/vlc/http/mosaic.html (url=/mosaic.html)
[0x1372c50] main interface debug: using interface module "oldhttp"
[0x1372c50] main interface debug: TIMER module_need() : 7.648 ms - Total 7.648 ms / 1 intvls (Avg 7.648 ms)
[0x137eec0] main playlist debug: adding item `/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi :audio-desync=-50 :no-sout-keep :meta-title=mrush-2001aso-cd1.avi :sout=#transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3},vcodec=h264,vb=384,fps=25,vfilter=canvas{width=480,height=320,aspect=480:320,padd},no-audio-sync,acodec=mp4a,ab=64,channels=1,no-soverlay}:rtp{sdp=rtsp://0.0.0.0:5554/android.sdp,no-sap,caching=2000,no-mp4a-latm}' ( /mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi )
[0x1372c50] oldhttp interface debug: requested mrl add: /mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi :audio-desync=-50 :no-sout-keep :meta-title=mrush-2001aso-cd1.avi :sout=#transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3},vcodec=h264,vb=384,fps=25,vfilter=canvas{width=480,height=320,aspect=480:320,padd},no-audio-sync,acodec=mp4a,ab=64,channels=1,no-soverlay}:rtp{sdp=rtsp://0.0.0.0:5554/android.sdp,no-sap,caching=2000,no-mp4a-latm}
[0x137eec0] main playlist debug: rebuilding array of current - root Playlist
[0x137eec0] main playlist debug: rebuild done - 1 items, index -1
[0x1372c50] oldhttp interface debug: requested playlist item: 4
[0x137eec0] main playlist debug: processing request item /mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi :audio-desync=-50 :no-sout-keep :meta-title=mrush-2001aso-cd1.avi :sout=#transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3},vcodec=h264,vb=384,fps=25,vfilter=canvas{width=480,height=320,aspect=480:320,padd},no-audio-sync,acodec=mp4a,ab=64,channels=1,no-soverlay}:rtp{sdp=rtsp://0.0.0.0:5554/android.sdp,no-sap,caching=2000,no-mp4a-latm} node Playlist skip 0
[0x137eec0] main playlist debug: resyncing on /mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi :audio-desync=-50 :no-sout-keep :meta-title=mrush-2001aso-cd1.avi :sout=#transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3},vcodec=h264,vb=384,fps=25,vfilter=canvas{width=480,height=320,aspect=480:320,padd},no-audio-sync,acodec=mp4a,ab=64,channels=1,no-soverlay}:rtp{sdp=rtsp://0.0.0.0:5554/android.sdp,no-sap,caching=2000,no-mp4a-latm}
[0x137eec0] main playlist debug: /mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi :audio-desync=-50 :no-sout-keep :meta-title=mrush-2001aso-cd1.avi :sout=#transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3},vcodec=h264,vb=384,fps=25,vfilter=canvas{width=480,height=320,aspect=480:320,padd},no-audio-sync,acodec=mp4a,ab=64,channels=1,no-soverlay}:rtp{sdp=rtsp://0.0.0.0:5554/android.sdp,no-sap,caching=2000,no-mp4a-latm} is at 0
[0x137eec0] main playlist debug: starting new item
[0x137eec0] main playlist debug: creating new input thread
[0x7f47840173d0] main input debug: Creating an input for '/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi :audio-desync=-50 :no-sout-keep :meta-title=mrush-2001aso-cd1.avi :sout=#transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3},vcodec=h264,vb=384,fps=25,vfilter=canvas{width=480,height=320,aspect=480:320,padd},no-audio-sync,acodec=mp4a,ab=64,channels=1,no-soverlay}:rtp{sdp=rtsp://0.0.0.0:5554/android.sdp,no-sap,caching=2000,no-mp4a-latm}'
[0x7f47840173d0] main input debug: thread (input) created at priority 10 (input/input.c:220)
[0x7f47840172e0] main input debug: Creating an input for '/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi :audio-desync=-50 :no-sout-keep :meta-title=mrush-2001aso-cd1.avi :sout=#transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3},vcodec=h264,vb=384,fps=25,vfilter=canvas{width=480,height=320,aspect=480:320,padd},no-audio-sync,acodec=mp4a,ab=64,channels=1,no-soverlay}:rtp{sdp=rtsp://0.0.0.0:5554/android.sdp,no-sap,caching=2000,no-mp4a-latm}'
[0x7f47840173d0] main input debug: thread started
[0x138ef70] main stream output debug: using sout chain=`transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3},vcodec=h264,vb=384,fps=25,vfilter=canvas{width=480,height=320,aspect=480:320,padd},no-audio-sync,acodec=mp4a,ab=64,channels=1,no-soverlay}:rtp{sdp=rtsp://0.0.0.0:5554/android.sdp,no-sap,caching=2000,no-mp4a-latm}'
[0x138ef70] main stream output debug: stream=`rtp'
[0x13b6e80] main stream out debug: looking for sout stream module: 1 candidate
[0x13b6e80] main stream out debug: set config option: sout-rtp-sdp to rtsp://0.0.0.0:5554/android.sdp
[0x13b6e80] main stream out debug: set config option: sout-rtp-sap to (null)
[0x13b6e80] main stream out debug: set config option: sout-rtp-caching to 2000
[0x13b6e80] main stream out debug: set config option: sout-rtp-mp4a-latm to (null)
[0x13b6e80] stream_out_rtp stream out debug: RTSP stream: host 0.0.0.0 port 5554 at /android.sdp
[0x13b6e80] main stream out debug: net: listening to 0.0.0.0 port 5554
[0x13b6e80] main stream out debug: using sout stream module "stream_out_rtp"
[0x13b6e80] main stream out debug: TIMER module_need() : 1.765 ms - Total 1.765 ms / 1 intvls (Avg 1.765 ms)
[0x138ef70] main stream output debug: stream=`transcode'
[0x13baec0] main stream out debug: looking for sout stream module: 1 candidate
[0x13baec0] main stream out debug: set config option: sout-transcode-venc to x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframes=0,no-cabac,no-interlaced,weightp=0,no-8x8dct,level=3}
[0x13baec0] main stream out debug: set config option: sout-transcode-vcodec to h264
[0x13baec0] main stream out debug: set config option: sout-transcode-vb to 384
[0x13baec0] main stream out debug: set config option: sout-transcode-fps to 25
[0x13baec0] main stream out debug: set config option: sout-transcode-vfilter to canvas{width=480,height=320,aspect=480:320,padd}
[0x13baec0] main stream out debug: set config option: sout-transcode-audio-sync to (null)
[0x13baec0] main stream out debug: set config option: sout-transcode-acodec to mp4a
[0x13baec0] main stream out debug: set config option: sout-transcode-ab to 64
[0x13baec0] main stream out debug: set config option: sout-transcode-channels to 1
[0x13baec0] main stream out debug: set config option: sout-transcode-soverlay to (null)
[0x13baec0] stream_out_transcode stream out debug: codec audio=mp4a 0Hz 1 channels 64Kb/s
[0x13baec0] stream_out_transcode stream out debug: codec video=h264 0x0 scaling: 0.000000 384kb/s
[0x13baec0] main stream out debug: using sout stream module "stream_out_transcode"
[0x13baec0] main stream out debug: TIMER module_need() : 0.807 ms - Total 0.807 ms / 1 intvls (Avg 0.807 ms)
[0x7f47840173d0] main input debug: using timeshift granularity of 50 MiB
[0x7f47840173d0] main input debug: using timeshift path '/tmp'
[0x7f47840173d0] main input debug: `/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi' gives access `' demux `' path `/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi'
[0x7f47840173d0] main input debug: creating demux: access='' demux='' path='/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi'
[0x17b0460] main demux debug: looking for access_demux module: 7 candidates
[0x17b0460] main demux debug: no access_demux module matching "any" could be loaded
[0x17b0460] main demux debug: TIMER module_need() : 2.425 ms - Total 2.425 ms / 1 intvls (Avg 2.425 ms)
[0x7f47840173d0] main input debug: creating access '' path='/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi'
[0x17b6ad0] main access debug: looking for access module: 7 candidates
[0x17b6ad0] vcd access debug: trying .cue file: /mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.cue
[0x17b6ad0] vcd access debug: could not find .cue file
[0x17b6ad0] filesystem access debug: opening file `/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi'
[0x17b6ad0] main access debug: using access module "filesystem"
[0x17b6ad0] main access debug: TIMER module_need() : 1.571 ms - Total 1.571 ms / 1 intvls (Avg 1.571 ms)
[0x17b7150] main stream debug: Using AStream*Stream
[0x17b7150] main stream debug: pre buffering
[0x17b7150] main stream debug: received first data after 0 ms
[0x17b7150] main stream debug: pre-buffering done 1024 bytes in 0s - 55555 KiB/s
[0x17b75c0] main stream debug: looking for stream_filter module: 5 candidates
[0x17b75c0] main stream debug: no stream_filter module matching "any" could be loaded
[0x17b75c0] main stream debug: TIMER module_need() : 0.143 ms - Total 0.143 ms / 1 intvls (Avg 0.143 ms)
[0x17b7570] main stream debug: looking for stream_filter module: 1 candidate
[0x17b7570] main stream debug: using stream_filter module "stream_filter_record"
[0x17b7570] main stream debug: TIMER module_need() : 2.664 ms - Total 2.664 ms / 1 intvls (Avg 2.664 ms)
[0x7f47840173d0] main input debug: creating demux: access='' demux='' path='/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi'
[0x17b7810] main demux debug: looking for demux module: 52 candidates
[0x17b7570] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:732041380 pos:0
[0x17b7570] avi stream debug: found LIST chunk: 'AVI '
[0x17b7570] avi stream debug: <list 'AVI '>
[0x17b7570] avi stream debug: found Chunk fourcc:5453494c (LIST) size:8830 pos:12
[0x17b7570] avi stream debug: found LIST chunk: 'hdrl'
[0x17b7570] avi stream debug: <list 'hdrl'>
[0x17b7570] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24
[0x17b7570] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 608x272
[0x17b7570] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4244 pos:88
[0x17b7570] avi stream debug: found LIST chunk: 'strl'
[0x17b7570] avi stream debug: <list 'strl'>
[0x17b7570] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100
[0x17b7570] avi stream debug: strh: type:vids handler:0x64697678 samplesize:0 25.00fps
[0x17b7570] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164
[0x17b7570] avi stream debug: strf: video:XVID 608x272 planes:1 12bpp
[0x17b7570] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:212
[0x17b7570] avi stream debug: </list 'strl'>
[0x17b7570] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4234 pos:4340
[0x17b7570] avi stream debug: found LIST chunk: 'strl'
[0x17b7570] avi stream debug: <list 'strl'>
[0x17b7570] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:4352
[0x17b7570] avi stream debug: strh: type:auds handler:0x00000000 samplesize:0 41.67fps
[0x17b7570] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:4416
[0x17b7570] avi stream debug: strf: audio:0x0055 channels:2 48000Hz 0bits/sample 119kb/s
[0x17b7570] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:4454
[0x17b7570] avi stream debug: </list 'strl'>
[0x17b7570] avi stream debug: found Chunk fourcc:5453494c (LIST) size:260 pos:8582
[0x17b7570] avi stream debug: found LIST chunk: 'odml'
[0x17b7570] avi stream debug: <list 'odml'>
[0x17b7570] avi stream debug: found Chunk fourcc:686c6d64 (dmlh) size:248 pos:8594
[0x17b7570] avi stream warning: unknown chunk (not loaded)
[0x17b7570] avi stream debug: </list 'odml'>
[0x17b7570] avi stream debug: </list 'hdrl'>
[0x17b7570] avi stream debug: found Chunk fourcc:5453494c (LIST) size:56 pos:8850
[0x17b7570] avi stream debug: found LIST chunk: 'INFO'
[0x17b7570] avi stream debug: <list 'INFO'>
[0x17b7570] avi stream debug: found Chunk fourcc:54465349 (ISFT) size:44 pos:8862
[0x17b7570] avi stream debug: ISFT: software : VirtualDubMod 1.5.10.2 (build 2540/release)
[0x17b7570] avi stream debug: </list 'INFO'>
[0x17b7570] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1318 pos:8914
[0x17b7570] avi stream debug: found Chunk fourcc:5453494c (LIST) size:727901084 pos:10240
[0x17b7570] avi stream debug: skipping movi chunk
[0x17b7570] avi stream debug: found Chunk fourcc:31786469 (idx1) size:4130048 pos:727911332
[0x17b7570] avi stream debug: idx1: index entry:258128
[0x17b7570] avi stream debug: </list 'AVI '>
[0x17b7570] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1868 pos:732041388
[0x17b7570] avi stream debug: * LIST-root size:732043264 pos:0
[0x17b7570] avi stream debug:      + RIFF-AVI  size:732041380 pos:0
[0x17b7570] avi stream debug:      |    + LIST-hdrl size:8830 pos:12
[0x17b7570] avi stream debug:      |    |    + avih size:56 pos:24
[0x17b7570] avi stream debug:      |    |    + LIST-strl size:4244 pos:88
[0x17b7570] avi stream debug:      |    |    |    + strh size:56 pos:100
[0x17b7570] avi stream debug:      |    |    |    + strf size:40 pos:164
[0x17b7570] avi stream debug:      |    |    |    + JUNK size:4120 pos:212
[0x17b7570] avi stream debug:      |    |    + LIST-strl size:4234 pos:4340
[0x17b7570] avi stream debug:      |    |    |    + strh size:56 pos:4352
[0x17b7570] avi stream debug:      |    |    |    + strf size:30 pos:4416
[0x17b7570] avi stream debug:      |    |    |    + JUNK size:4120 pos:4454
[0x17b7570] avi stream debug:      |    |    + LIST-odml size:260 pos:8582
[0x17b7570] avi stream debug:      |    |    |    + dmlh size:248 pos:8594
[0x17b7570] avi stream debug:      |    + LIST-INFO size:56 pos:8850
[0x17b7570] avi stream debug:      |    |    + ISFT size:44 pos:8862
[0x17b7570] avi stream debug:      |    + JUNK size:1318 pos:8914
[0x17b7570] avi stream debug:      |    + LIST-movi size:727901084 pos:10240
[0x17b7570] avi stream debug:      |    + idx1 size:4130048 pos:727911332
[0x17b7570] avi stream debug:      + JUNK size:1868 pos:732041388
[0x17b7810] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED
[0x17b7810] avi demux debug: stream[0] rate:25 scale:1 samplesize:0
[0x17b7810] avi demux debug: stream[0] video(XVID) 608x272 12bpp 25.000000fps
[0x7f47840173d0] main input debug: selecting program id=0
[0x17b7810] avi demux debug: stream[1] rate:48000 scale:1152 samplesize:0
[0x17b7810] avi demux debug: stream[1] audio(0x55) 2 channels 48000Hz 0bits
[0x137eec0] main playlist debug: no fetch required for mrush-2001aso-cd1.avi (art currently (null))
[0x17b7810] avi demux debug: selected standard index for stream[0]
[0x17b7810] avi demux debug: selected standard index for stream[1]
[0x17b7810] avi demux debug: stream[0] created 96798 index entries
[0x17b7810] avi demux debug: stream[1] created 161330 index entries
[0x17b7810] avi demux debug: stream[0] length:3871 (based on index)
[0x17b7810] avi demux debug: stream[1] length:3871 (based on index)
[0x17b7810] main demux debug: using demux module "avi"
[0x17b7810] main demux debug: TIMER module_need() : 67.306 ms - Total 67.306 ms / 1 intvls (Avg 67.306 ms)
[0x13bb770] main decoder debug: looking for packetizer module: 21 candidates
[0x13bb770] main decoder debug: using packetizer module "packetizer_mpeg4video"
[0x13bb770] main decoder debug: TIMER module_need() : 136.122 ms - Total 136.122 ms / 1 intvls (Avg 136.122 ms)
[0x13bb770] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:301)
[0x13bb770] main decoder debug: thread started
[0x138e3c0] main decoder debug: looking for packetizer module: 21 candidates
[0x138e3c0] main decoder debug: using packetizer module "mpeg_audio"
[0x138e3c0] main decoder debug: TIMER module_need() : 12.679 ms - Total 12.679 ms / 1 intvls (Avg 12.679 ms)
[0x138e3c0] main decoder debug: thread started
[0x138e3c0] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:301)
[0x7f47840173d0] main input debug: starting in async mode
[0x2b3ddd0] main demux meta debug: looking for meta reader module: 2 candidates
[0x2b3ddd0] lua demux meta debug: Trying Lua scripts in /mnt/tank/home/media/.local/share/vlc/lua/meta/reader
[0x2b3ddd0] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x2b3ddd0] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x2b3ddd0] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x2b3ddd0] main demux meta debug: no meta reader module matching "any" could be loaded
[0x2b3ddd0] main demux meta debug: TIMER module_need() : 0.812 ms - Total 0.812 ms / 1 intvls (Avg 0.812 ms)
[0x7f47840173d0] main input debug: `/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi' successfully opened
[0x7f47840173d0] main input debug: Buffering 0%
[0x7f47840173d0] main input debug: switching to sync mode
[0x7f47840173d0] main input debug: Buffering 7%
[0x138e3c0] mpeg_audio decoder debug: MPGA channels:2 samplerate:48000 bitrate:128
[0x13bb770] packetizer_mpeg4video decoder warning: waiting for VOL
[0x7f47840173d0] main input debug: Buffering 14%
[0x13bb770] packetizer_mpeg4video decoder warning: waiting for VOL
[0x7f47840173d0] main input debug: Buffering 21%
[0x138ef70] main stream output debug: adding a new sout input (sout_input:0x7f4784002980)
[0x138ef70] main stream output debug: adding a new sout input (sout_input:0x7f477c0008f0)
[0x7f47840173d0] main input debug: Buffering 28%
[0x13baec0] stream_out_transcode stream out debug: creating audio transcoding from fcc=`mpga' to fcc=`mp4a'
[0x7f47840173d0] main input debug: Buffering 35%
[0x7f47840173d0] main input debug: Buffering 42%
[0x7f47840173d0] main input debug: Buffering 50%
[0x7f47840173d0] main input debug: Buffering 57%
[0x7f47840173d0] main input debug: Buffering 64%
[0x7f4784002440] main generic debug: looking for decoder module: 28 candidates
[0x7f47840173d0] main input debug: Buffering 71%
[0x7f47840173d0] main input debug: Buffering 78%
[0x7f47840173d0] main input debug: Buffering 85%
[0x7f47840173d0] main input debug: Buffering 92%
[0x7f47840173d0] main input debug: Buffering 100%
[0x7f47840173d0] main input debug: Stream buffering done (375 ms in 0 ms)
[0x7f4784002440] main generic debug: using decoder module "mpeg_audio"
[0x7f4784002440] main generic debug: TIMER module_need() : 2444.148 ms - Total 2444.148 ms / 1 intvls (Avg 2444.148 ms)
[0x7f4784002a50] main encoder debug: looking for encoder module: 11 candidates
[0x7f4784002a50] main encoder debug: no encoder module matching "any" could be loaded
[0x7f4784002a50] main encoder debug: TIMER module_need() : 653.204 ms - Total 653.204 ms / 1 intvls (Avg 653.204 ms)
[0x13baec0] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mp4a)
[0x7f4784002440] main generic debug: removing module "mpeg_audio"
[0x13baec0] stream_out_transcode stream out error: cannot create audio chain
[0x138e3c0] main decoder error: cannot create packetizer output (mpga)
[0x13baec0] stream_out_transcode stream out debug: creating video transcoding from fcc=`mp4v' to fcc=`h264'
[0x7f477c00c010] main generic debug: looking for decoder module: 28 candidates
[0x7f477c00c010] main generic debug: no decoder module matching "any" could be loaded
[0x7f477c00c010] main generic debug: TIMER module_need() : 701.264 ms - Total 701.264 ms / 1 intvls (Avg 701.264 ms)
[0x13baec0] stream_out_transcode stream out error: cannot find video decoder
[0x13baec0] stream_out_transcode stream out error: cannot create video chain
[0x13bb770] main decoder error: cannot create packetizer output (mp4v)
[0x7f47840173d0] main input debug: Decoder buffering done in 3798 ms
^C[0x1369940] signals interface error: Caught Interrupt signal, exiting...
[0x1288120] main libvlc debug: deactivating the playlist
[0x137eec0] main playlist debug: Deactivate
[0x137eec0] main playlist debug: incoming request - stopping current input
[0x137eec0] main playlist debug: dying input
[0x7f47840173d0] main input debug: control type=0
[0x7f47840173d0] main input debug: control: stopping input
[0x137eec0] main playlist debug: dying input
[0x13bb770] main decoder debug: removing module "packetizer_mpeg4video"
[0x13bb770] main decoder debug: killing decoder fourcc `mp4v', 0 PES in FIFO
[0x138e3c0] main decoder debug: removing module "mpeg_audio"
[0x138e3c0] main decoder debug: killing decoder fourcc `mpga', 0 PES in FIFO
[0x17b7570] avi stream debug: free chunk avih
[0x17b7570] avi stream debug: free chunk strh
[0x17b7570] avi stream debug: free chunk strf
[0x17b7570] avi stream debug: free chunk JUNK
[0x17b7570] avi stream debug: free chunk LIST
[0x17b7570] avi stream debug: free chunk strh
[0x17b7570] avi stream debug: free chunk strf
[0x17b7570] avi stream debug: free chunk JUNK
[0x17b7570] avi stream debug: free chunk LIST
[0x17b7570] avi stream warning: unknown chunk (not unloaded)
[0x17b7570] avi stream debug: free chunk LIST
[0x17b7570] avi stream debug: free chunk LIST
[0x17b7570] avi stream debug: free chunk ISFT
[0x17b7570] avi stream debug: free chunk LIST
[0x17b7570] avi stream debug: free chunk JUNK
[0x17b7570] avi stream debug: free chunk LIST
[0x17b7570] avi stream debug: free chunk idx1
[0x17b7570] avi stream debug: free chunk RIFF
[0x17b7570] avi stream debug: free chunk JUNK
[0x17b7570] avi stream debug: free chunk LIST
[0x17b7810] main demux debug: removing module "avi"
[0x17b7570] main stream debug: removing module "stream_filter_record"
[0x17b6ad0] main access debug: removing module "filesystem"
[0x7f47840173d0] main input debug: Program doesn't contain anymore ES
[0x7f47840173d0] main input debug: thread ended
[0x137eec0] main playlist debug: dead input
[0x138ef70] main stream output debug: destroying useless sout
[0x13baec0] main stream out debug: destroying chain... (name=transcode)
[0x13baec0] main stream out debug: removing module "stream_out_transcode"
[0x13baec0] main stream out debug: destroying chain done
[0x13b6e80] main stream out debug: destroying chain... (name=rtp)
[0x7f4784006890] main http server debug: waitpipe: object killed
[0x7f4784006890] main http server debug: HTTP host removed
[0x13b6e80] main stream out debug: removing module "stream_out_rtp"
[0x13b6e80] main stream out debug: destroying chain done
[0x7f47840173d0] main input debug: TIMER input launching for '/mnt/tank/media/Movies/2001 A Space Odyssey (1968)/mrush-2001aso-cd1.avi :audio-desync=-50 :no-sout-keep :meta-title=mrush-2001aso-cd1.avi :sout=#transcode{venc=x264{keyint=50,ref=1,qpmin=10,qpmax=36,qcomp=0.6,profile=baseline,bframe : 227.899 ms - Total 227.899 ms / 1 intvls (Avg 227.899 ms)
[0x17b84a0] main playlist export debug: saving Media Library to file /mnt/tank/home/media/.local/share/vlc/ml.xspf
[0x17b84a0] main playlist export debug: looking for playlist export module: 1 candidate
[0x17b84a0] main playlist export debug: using playlist export module "export"
[0x17b84a0] main playlist export debug: TIMER module_need() : 0.370 ms - Total 0.370 ms / 1 intvls (Avg 0.370 ms)
[0x17b84a0] main playlist export debug: removing module "export"
[0x137eec0] main playlist debug: Deactivated
[0x1288120] main libvlc debug: removing all services discovery tasks
[0x1288120] main libvlc debug: removing all interfaces
[0x136b610] main http server debug: waitpipe: object killed
[0x136b610] main http server debug: HTTP host removed
[0x136b610] main http server warning: client still connected
[0x136b610] main http server warning: client still connected
[0x1368770] main http server debug: no hosts left, stopping httpd
[0x1372c50] main interface debug: removing module "oldhttp"
[0x1369940] main interface debug: removing module "signals"
[0x1371510] main interface debug: removing module "hotkeys"
[0x137eec0] main playlist debug: destroying
[0x1288120] main libvlc debug: TIMER ML Load : Total 3136.154 ms / 1 intvls (Avg 3136.154 ms)
[0x1288120] main libvlc debug: TIMER Items array build : Total 0.169 ms / 2 intvls (Avg 0.084 ms)
[0x1288120] main libvlc debug: TIMER Preparse run : Total 70.379 ms / 1 intvls (Avg 70.379 ms)
[0x1288120] main libvlc debug: TIMER ML Dump : Total 0.501 ms / 1 intvls (Avg 0.501 ms)
[0x1288120] main libvlc debug: removing stats
[0x1288120] main libvlc debug: removing module "memcpymmxext"
media@hex:~$
```

ffmpeg -codecs:
```
media@hex:~$ ffmpeg -codecs
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1.1, Copyright (c) 2000-2010 the Libav developers
  built on Sep 16 2011 17:00:39 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavdevice configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavfilter configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Codecs:
 D..... = Decoding supported
 .E.... = Encoding supported
 ..V... = Video codec
 ..A... = Audio codec
 ..S... = Subtitle codec
 ...S.. = Supports draw_horiz_band
 ....D. = Supports direct rendering method 1
 .....T = Supports weird frame truncation
 ------
 D V D  4xm             4X Movie
 D V D  8bps            QuickTime 8BPS video
 D A    8svx_exp        8SVX exponential
 D A    8svx_fib        8SVX fibonacci
 D V D  FRWU            Forward Uncompressed
 DEA    aac             Advanced Audio Coding
 D V D  aasc            Autodesk RLE
 DEA    ac3             ATSC A/52A (AC-3)
 D A    adpcm_4xm       ADPCM 4X Movie
 DEA    adpcm_adx       SEGA CRI ADX ADPCM
 D A    adpcm_ct        ADPCM Creative Technology
 D A    adpcm_ea        ADPCM Electronic Arts
 D A    adpcm_ea_maxis_xa ADPCM Electronic Arts Maxis CDROM XA
 D A    adpcm_ea_r1     ADPCM Electronic Arts R1
 D A    adpcm_ea_r2     ADPCM Electronic Arts R2
 D A    adpcm_ea_r3     ADPCM Electronic Arts R3
 D A    adpcm_ea_xas    ADPCM Electronic Arts XAS
 D A    adpcm_ima_amv   ADPCM IMA AMV
 D A    adpcm_ima_dk3   ADPCM IMA Duck DK3
 D A    adpcm_ima_dk4   ADPCM IMA Duck DK4
 D A    adpcm_ima_ea_eacs ADPCM IMA Electronic Arts EACS
 D A    adpcm_ima_ea_sead ADPCM IMA Electronic Arts SEAD
 D A    adpcm_ima_iss   ADPCM IMA Funcom ISS
 DEA    adpcm_ima_qt    ADPCM IMA QuickTime
 D A    adpcm_ima_smjpeg ADPCM IMA Loki SDL MJPEG
 DEA    adpcm_ima_wav   ADPCM IMA WAV
 D A    adpcm_ima_ws    ADPCM IMA Westwood
 DEA    adpcm_ms        ADPCM Microsoft
 D A    adpcm_sbpro_2   ADPCM Sound Blaster Pro 2-bit
 D A    adpcm_sbpro_3   ADPCM Sound Blaster Pro 2.6-bit
 D A    adpcm_sbpro_4   ADPCM Sound Blaster Pro 4-bit
 DEA    adpcm_swf       ADPCM Shockwave Flash
 D A    adpcm_thp       ADPCM Nintendo Gamecube THP
 D A    adpcm_xa        ADPCM CDROM XA
 DEA    adpcm_yamaha    ADPCM Yamaha
 DEA    alac            ALAC (Apple Lossless Audio Codec)
 D A    als             MPEG-4 Audio Lossless Coding (ALS)
 D A    amrnb           Adaptive Multi-Rate NarrowBand
 D V D  amv             AMV Video
 D V D  anm             Deluxe Paint Animation
 D A    ape             Monkey's Audio
 DEV D  asv1            ASUS V1
 DEV D  asv2            ASUS V2
 D A    atrac1          Atrac 1 (Adaptive TRansform Acoustic Coding)
 D A    atrac3          Atrac 3 (Adaptive TRansform Acoustic Coding 3)
 D V D  aura            Auravision AURA
 D V D  aura2           Auravision Aura 2
 D V D  avs             AVS (Audio Video Standard) video
 D V D  bethsoftvid     Bethesda VID video
 D V D  bfi             Brute Force & Ignorance
 D A    binkaudio_dct   Bink Audio (DCT)
 D A    binkaudio_rdft  Bink Audio (RDFT)
 D V    binkvideo       Bink video
 DEV D  bmp             BMP image
 D V D  c93             Interplay C93
 D V D  camstudio       CamStudio
 D V D  camtasia        TechSmith Screen Capture Codec
 D V D  cavs            Chinese AVS video (AVS1-P2, JiZhun profile)
 D V D  cdgraphics      CD Graphics video
 D V D  cinepak         Cinepak
 D V D  cljr            Cirrus Logic AccuPak
 D A    cook            COOK
 D V D  cyuv            Creative YUV (CYUV)
 D A    dca             DCA (DTS Coherent Acoustics)
 DEV D  dnxhd           VC3/DNxHD
 D V    dpx             DPX image
 D A    dsicinaudio     Delphine Software International CIN audio
 D V D  dsicinvideo     Delphine Software International CIN video
 DES    dvbsub          DVB subtitles
 DES    dvdsub          DVD subtitles
 DEV D  dvvideo         DV (Digital Video)
 D V D  dxa             Feeble Files/ScummVM DXA
 D A    eac3            ATSC A/52B (AC-3, E-AC-3)
 D V D  eacmv           Electronic Arts CMV video
 D V D  eamad           Electronic Arts Madcow Video
 D V D  eatgq           Electronic Arts TGQ video
 D V    eatgv           Electronic Arts TGV video
 D V D  eatqi           Electronic Arts TQI Video
 D V D  escape124       Escape 124
 DEV D  ffv1            FFmpeg video codec #1
 DEVSD  ffvhuff         Huffyuv FFmpeg variant
 DEA    flac            FLAC (Free Lossless Audio Codec)
 DEV D  flashsv         Flash Screen Video
 D V D  flic            Autodesk Animator Flic video
 DEVSD  flv             Flash Video (FLV) / Sorenson Spark / Sorenson H.263
 D V D  fraps           Fraps
 DEA    g726            G.726 ADPCM
 DEV D  gif             GIF (Graphics Interchange Format)
 DEV D  h261            H.261
 DEVSDT h263            H.263 / H.263-1996
 D VSD  h263i           Intel H.263
  EV    h263p           H.263+ / H.263-1998 / H.263 version 2
 D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
 DEVSD  huffyuv         Huffyuv / HuffYUV
 D V D  idcinvideo      id Quake II CIN video
 D V D  iff_byterun1    IFF ByteRun1
 D V D  iff_ilbm        IFF ILBM
 D A    imc             IMC (Intel Music Coder)
 D V D  indeo2          Intel Indeo 2
 D V D  indeo3          Intel Indeo 3
 D V    indeo5          Intel Indeo Video Interactive 5
 D A    interplay_dpcm  DPCM Interplay
 D V D  interplayvideo  Interplay MVE video
 DEV D  jpegls          JPEG-LS
 D V    kgv1            Kega Game Video
 D V D  kmvc            Karl Morton's video codec
  EV    libdirac        libdirac Dirac 2.2
  EA    libfaac         libfaac AAC (Advanced Audio Codec)
 D A    libfaad         libfaad AAC (Advanced Audio Codec)
 DEA    libgsm          libgsm GSM
 DEA    libgsm_ms       libgsm GSM Microsoft variant
  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
 DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
 D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band
 D V D  libopenjpeg     OpenJPEG based JPEG 2000 decoder
 DEV    libschroedinger libschroedinger Dirac 2.2
 D A    libspeex        libspeex Speex
  EV    libtheora       libtheora Theora
  EA    libvorbis       libvorbis Vorbis
 DEV    libvpx          libvpx VP8
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
  EV    libxvid         libxvidcore MPEG-4 part 2
  EV    ljpeg           Lossless JPEG
 D V D  loco            LOCO
 D A    mace3           MACE (Macintosh Audio Compression/Expansion) 3:1
 D A    mace6           MACE (Macintosh Audio Compression/Expansion) 6:1
 D V D  mdec            Sony PlayStation MDEC (Motion DECoder)
 D V D  mimic           Mimic
 DEV D  mjpeg           MJPEG (Motion JPEG)
 D V D  mjpegb          Apple MJPEG-B
 D A    mlp             MLP (Meridian Lossless Packing)
 D V D  mmvideo         American Laser Games MM Video
 D V D  motionpixels    Motion Pixels video
 D A    mp1             MP1 (MPEG audio layer 1)
 DEA    mp2             MP2 (MPEG audio layer 2)
 D A    mp3             MP3 (MPEG audio layer 3)
 D A    mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3on4          MP3onMP4
 D A    mpc7            Musepack SV7
 D A    mpc8            Musepack SV8
 DEVSDT mpeg1video      MPEG-1 video
 D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
 DEVSDT mpeg2video      MPEG-2 video
 DEVSDT mpeg4           MPEG-4 part 2
 D V DT mpeg4_vdpau     MPEG-4 part 2 (VDPAU)
 D VSDT mpegvideo       MPEG-1 video
 D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
 D VSDT mpegvideo_xvmc  MPEG-1/2 video XvMC (X-Video Motion Compensation)
 DEVSD  msmpeg4         MPEG-4 part 2 Microsoft variant version 3
 DEVSD  msmpeg4v1       MPEG-4 part 2 Microsoft variant version 1
 DEVSD  msmpeg4v2       MPEG-4 part 2 Microsoft variant version 2
 D V D  msrle           Microsoft RLE
 D V D  msvideo1        Microsoft Video 1
 D V D  mszh            LCL (LossLess Codec Library) MSZH
 DEA    nellymoser      Nellymoser Asao
 D V D  nuv             NuppelVideo/RTJPEG
 DEV D  pam             PAM (Portable AnyMap) image
 DEV D  pbm             PBM (Portable BitMap) image
 DEA    pcm_alaw        PCM A-law
 D A    pcm_bluray      PCM signed 16|20|24-bit big-endian for Blu-ray media
 D A    pcm_dvd         PCM signed 20|24-bit big-endian
 DEA    pcm_f32be       PCM 32-bit floating point big-endian
 DEA    pcm_f32le       PCM 32-bit floating point little-endian
 DEA    pcm_f64be       PCM 64-bit floating point big-endian
 DEA    pcm_f64le       PCM 64-bit floating point little-endian
 DEA    pcm_mulaw       PCM mu-law
 DEA    pcm_s16be       PCM signed 16-bit big-endian
 DEA    pcm_s16le       PCM signed 16-bit little-endian
 D A    pcm_s16le_planar PCM 16-bit little-endian planar
 DEA    pcm_s24be       PCM signed 24-bit big-endian
 DEA    pcm_s24daud     PCM D-Cinema audio signed 24-bit
 DEA    pcm_s24le       PCM signed 24-bit little-endian
 DEA    pcm_s32be       PCM signed 32-bit big-endian
 DEA    pcm_s32le       PCM signed 32-bit little-endian
 DEA    pcm_s8          PCM signed 8-bit
 DEA    pcm_u16be       PCM unsigned 16-bit big-endian
 DEA    pcm_u16le       PCM unsigned 16-bit little-endian
 DEA    pcm_u24be       PCM unsigned 24-bit big-endian
 DEA    pcm_u24le       PCM unsigned 24-bit little-endian
 DEA    pcm_u32be       PCM unsigned 32-bit big-endian
 DEA    pcm_u32le       PCM unsigned 32-bit little-endian
 DEA    pcm_u8          PCM unsigned 8-bit
 DEA    pcm_zork        PCM Zork
 DEV D  pcx             PC Paintbrush PCX image
 DEV D  pgm             PGM (Portable GrayMap) image
 DEV D  pgmyuv          PGMYUV (Portable GrayMap YUV) image
 D S    pgssub          HDMV Presentation Graphic Stream subtitles
 DEV D  png             PNG image
 DEV D  ppm             PPM (Portable PixelMap) image
 D V D  ptx             V.Flash PTX image
 D A    qcelp           QCELP / PureVoice
 D A    qdm2            QDesign Music Codec 2
 D V D  qdraw           Apple QuickDraw
 D V D  qpeg            Q-team QPEG
 DEV D  qtrle           QuickTime Animation (RLE) video
 D V D  r210            Uncompressed RGB 10-bit
 DEV    rawvideo        raw video
 D A    real_144        RealAudio 1.0 (14.4K)
 D A    real_288        RealAudio 2.0 (28.8K)
 D V D  rl2             RL2 video
 DEA    roq_dpcm        id RoQ DPCM
 DEV D  roqvideo        id RoQ video
 D V D  rpza            QuickTime video (RPZA)
 DEV D  rv10            RealVideo 1.0
 DEV D  rv20            RealVideo 2.0
 D V D  rv30            RealVideo 3.0
 D V D  rv40            RealVideo 4.0
 DEV    sgi             SGI image
 D A    shorten         Shorten
 D A    sipr            RealAudio SIPR / ACELP.NET
 D A    smackaud        Smacker audio
 D V D  smackvid        Smacker video
 D V D  smc             QuickTime Graphics (SMC)
 DEV D  snow            Snow
 D A    sol_dpcm        DPCM Sol
 DEA    sonic           Sonic
  EA    sonicls         Sonic lossless
 D V D  sp5x            Sunplus JPEG (SP5X)
 D V D  sunrast         Sun Rasterfile image
 DEV D  svq1            Sorenson Vector Quantizer 1 / Sorenson Video 1 / SVQ1
 D VSD  svq3            Sorenson Vector Quantizer 3 / Sorenson Video 3 / SVQ3
 DEV D  targa           Truevision Targa image
 D VSD  theora          Theora
 D V D  thp             Nintendo Gamecube THP video
 D V D  tiertexseqvideo Tiertex Limited SEQ video
 DEV D  tiff            TIFF image
 D V D  tmv             8088flex TMV
 D A    truehd          TrueHD
 D V D  truemotion1     Duck TrueMotion 1.0
 D V D  truemotion2     Duck TrueMotion 2.0
 D A    truespeech      DSP Group TrueSpeech
 D A    tta             True Audio (TTA)
 D A    twinvq          VQF TwinVQ
 D V D  txd             Renderware TXD (TeXture Dictionary) image
 D V D  ultimotion      IBM UltiMotion
 DEV D  v210            Uncompressed 4:2:2 10-bit
 D V D  v210x           Uncompressed 4:2:2 10-bit
 D V    vb              Beam Software VB
 D V D  vc1             SMPTE VC-1
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
 D V D  vcr1            ATI VCR1
 D A    vmdaudio        Sierra VMD audio
 D V D  vmdvideo        Sierra VMD video
 D V D  vmnc            VMware Screen Codec / VMware Video
 D A    vorbis          Vorbis
 D VSD  vp3             On2 VP3
 D V D  vp5             On2 VP5
 D V D  vp6             On2 VP6
 D V D  vp6a            On2 VP6 (Flash version, with alpha channel)
 D V D  vp6f            On2 VP6 (Flash version)
 D V D  vqavideo        Westwood Studios VQA (Vector Quantized Animation) video
 D A    wavpack         WavPack
 D A    wmapro          Windows Media Audio 9 Professional
 DEA    wmav1           Windows Media Audio 1
 DEA    wmav2           Windows Media Audio 2
 D A    wmavoice        Windows Media Audio Voice
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V D  wmv3            Windows Media Video 9
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU
 D V D  wnv1            Winnov WNV1
 D A    ws_snd1         Westwood Audio (SND1)
 D A    xan_dpcm        DPCM Xan
 D V D  xan_wc3         Wing Commander III / Xan
 D V D  xl              Miro VideoXL
 DES    xsub            DivX subtitles (XSUB)
 D V    yop             Psygnosis YOP Video
 DEV D  zlib            LCL (LossLess Codec Library) ZLIB
 DEV D  zmbv            Zip Motion Blocks Video

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.
media@hex:~$
```

ffmpeg -formats
```
media@hex:~$ ffmpeg -formats
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1.1, Copyright (c) 2000-2010 the Libav developers
  built on Sep 16 2011 17:00:39 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavdevice configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavfilter configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
File formats:
 D. = Demuxing supported
 .E = Muxing supported
 --
  E 3g2             3GP2 format
  E 3gp             3GP format
 D  4xm             4X Technologies format
 D  IFF             IFF format
 D  ISS             Funcom ISS format
 D  MTV             MTV format
 DE RoQ             raw id RoQ format
 D  aac             raw ADTS AAC
 DE ac3             raw AC-3
  E adts            ADTS AAC
 D  aea             MD STUDIO audio
 DE aiff            Audio IFF
 DE alaw            PCM A-law format
 DE alsa            ALSA audio output
 DE amr             3GPP AMR file format
 D  anm             Deluxe Paint Animation
 D  apc             CRYO APC format
 D  ape             Monkey's Audio
 DE asf             ASF format
  E asf_stream      ASF format
 DE ***             SSA/*** format
 DE au              SUN AU format
 DE avi             AVI format
  E avm2            Flash 9 (AVM2) format
 D  avs             AVS format
 D  bethsoftvid     Bethesda Softworks VID format
 D  bfi             Brute Force & Ignorance
 D  bink            Bink
 D  c93             Interplay C93
 D  caf             Apple Core Audio Format
 D  cavsvideo       raw Chinese AVS video
 D  cdg             CD Graphics Format
  E crc             CRC testing format
 DE daud            D-Cinema audio format
 DE dirac           raw Dirac
 DE dnxhd           raw DNxHD (SMPTE VC-3)
 D  dsicin          Delphine Software International CIN format
 DE dts             raw DTS
 DE dv              DV video format
 D  dv1394          DV1394 A/V grab
  E dvd             MPEG-2 PS format (DVD VOB)
 D  dxa             DXA
 D  ea              Electronic Arts Multimedia Format
 D  ea_cdata        Electronic Arts cdata
 DE eac3            raw E-AC-3
 DE f32be           PCM 32 bit floating-point big-endian format
 DE f32le           PCM 32 bit floating-point little-endian format
 DE f64be           PCM 64 bit floating-point big-endian format
 DE f64le           PCM 64 bit floating-point little-endian format
 DE ffm             FFM (FFserver live feed) format
 D  film_cpk        Sega FILM/CPK format
 DE filmstrip       Adobe Filmstrip
 DE flac            raw FLAC
 D  flic            FLI/FLC/FLX animation format
 DE flv             FLV format
  E framecrc        framecrc testing format
  E gif             GIF Animation
 D  gsm             raw GSM
 DE gxf             GXF format
 DE h261            raw H.261
 DE h263            raw H.263
 DE h264            raw H.264 video format
 D  idcin           id Cinematic format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       raw Ingenient MJPEG
 D  ipmovie         Interplay MVE format
  E ipod            iPod H.264 MP4 format
 D  iv8             A format generated by IndigoVision 8000 video server
 D  libdc1394       dc1394 v.2 A/V grab
 D  lmlm4           lmlm4 raw format
 DE m4v             raw MPEG-4 video format
 DE matroska        Matroska file format
 DE mjpeg           raw MJPEG video
 DE mlp             raw MLP
 D  mm              American Laser Games MM format
 DE mmf             Yamaha SMAF
  E mov             MOV format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG-4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             MP4 format
 D  mpc             Musepack
 D  mpc8            Musepack SV8
 DE mpeg            MPEG-1 System format
  E mpeg1video      raw MPEG-1 video
  E mpeg2video      raw MPEG-2 video
 DE mpegts          MPEG-2 transport stream format
 D  mpegtsraw       MPEG-2 raw transport stream format
 D  mpegvideo       raw MPEG video
  E mpjpeg          MIME multipart JPEG format
 D  msnwctcp        MSN TCP Webcam stream
 DE mulaw           PCM mu-law format
 D  mvi             Motion Pixels MVI format
 DE mxf             Material eXchange Format
  E mxf_d10         Material eXchange Format, D-10 Mapping
 D  nc              NC camera feed format
 D  nsv             Nullsoft Streaming Video
  E null            raw null video format
 DE nut             NUT format
 D  nuv             NuppelVideo format
 DE ogg             Ogg
 D  oma             Sony OpenMG audio
 DE oss             Open Sound System playback
  E psp             PSP MP4 format
 D  psxstr          Sony Playstation STR format
 D  pva             TechnoTrend PVA file and stream format
 D  qcp             QCP format
 D  r3d             REDCODE R3D format
 DE rawvideo        raw video format
  E rcv             VC-1 test bitstream
 D  rl2             RL2 format
 DE rm              RealMedia format
 D  rpl             RPL/ARMovie format
  E rtp             RTP output format
 DE rtsp            RTSP output format
 DE s16be           PCM signed 16 bit big-endian format
 DE s16le           PCM signed 16 bit little-endian format
 DE s24be           PCM signed 24 bit big-endian format
 DE s24le           PCM signed 24 bit little-endian format
 DE s32be           PCM signed 32 bit big-endian format
 DE s32le           PCM signed 32 bit little-endian format
 DE s8              PCM signed 8 bit format
 D  sdp             SDP
 D  shn             raw Shorten
 D  siff            Beam Software SIFF
 D  smk             Smacker video
 D  sol             Sierra SOL format
 DE sox             SoX native format
  E spdif           IEC958 - S/PDIF (IEC-61937)
  E svcd            MPEG-2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tmv             8088flex TMV
 DE truehd          raw TrueHD
 D  tta             True Audio
 D  txd             Renderware TeXture Dictionary
 DE u16be           PCM unsigned 16 bit big-endian format
 DE u16le           PCM unsigned 16 bit little-endian format
 DE u24be           PCM unsigned 24 bit big-endian format
 DE u24le           PCM unsigned 24 bit little-endian format
 DE u32be           PCM unsigned 32 bit big-endian format
 DE u32le           PCM unsigned 32 bit little-endian format
 DE u8              PCM unsigned 8 bit format
 D  vc1             raw VC-1
 D  vc1test         VC-1 test bitstream format
  E vcd             MPEG-1 System format (VCD)
 D  video4linux2    Video4Linux2 device grab
 D  vmd             Sierra VMD format
  E vob             MPEG-2 PS format (VOB)
 DE voc             Creative Voice file format
 D  vqf             Nippon Telegraph and Telephone Corporation (NTT) TwinVQ
 D  w64             Sony Wave64 format
 DE wav             WAV format
 D  wc3movie        Wing Commander III movie format
  E webm            WebM file format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 D  x11grab         X11grab
 D  xa              Maxis XA File Format
 D  yop             Psygnosis YOP Format
 DE yuv4mpegpipe    YUV4MPEG pipe format
```

What I find interesting here is that libfaac shows up in -codecs but not in -formats, which I'm guessing is the cause of my issues, since it shows a decoder flag but no encoder flag.

I'm using the medibuntu -extra versions of all ffmpeg's dependencies. I'd like to avoid resorting to sources if at all possible since I have limited disk space on this server and don't want to have to install a bunch of dev packages.

Any pointers would be greatly appreciated. Thanks.

---

