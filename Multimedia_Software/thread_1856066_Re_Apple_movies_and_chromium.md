---
title: "Re: Apple movies and chromium"
date: 2011-10-07
forum: Multimedia Software
---

### Post by Osmodivs on 2011-10-07
I can't watch *Apple* videos either on **Chrome**, all I get is this:


```
osmodivs@Djiin:~$ chromium-browser 
Attempting to load the system libmoon 
[3903:3903:2002508327:ERROR:CONSOLE(6465)] "Uncaught TypeError: Cannot read property 'can_uninstall' of undefined", source: chrome://newtab/ (6465)
[0x7fc21f505eb0] main libvlc debug: VLC media player - 1.1.9 The Luggage
[0x7fc21f505eb0] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x7fc21f505eb0] main libvlc debug: revision exported
[0x7fc21f505eb0] main libvlc debug: configured with ./configure  '--enable-static' '--build=x86_64-linux-gnu' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--sysconfdir=/etc' '--with-binary-version=1ubuntu1.3' '--enable-a52' '--enable-aa' '--enable-bonjour' '--enable-caca' '--enable-dca' '--enable-dirac' '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-ggi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libmpeg2' '--enable-libproxy' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mozilla' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-pulse' '--enable-qt4' '--enable-realrtsp' '--enable-schroedinger' '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--with-mozilla-pkg=libxul' '--disable-dxva2' '--disable-gnomevfs' '--disable-goom' '--disable-osso_screensaver' '--disable-portaudio' '--disable-projectm' '--disable-sqlite' '--disable-telx' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv' '--enable-libva' '--enable-pvr' '--enable-udev' '--enable-v4l2' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x7fc21f505eb0] main libvlc debug: translation test: code is "C"
[0x7fc21f505eb0] main libvlc debug: checking plugin modules
[0x7fc21f505eb0] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins-04081e-7e8.dat
[0x7fc21f505eb0] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x7fc21f505eb0] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins-04081e-7e8.dat
[0x7fc21f505eb0] main libvlc debug: module bank initialized (395 modules)
[0x7fc21f505eb0] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 FPU 
[0x7fc21f505eb0] main libvlc debug: looking for memcpy module: 3 candidates
[0x7fc21f505eb0] main libvlc debug: using memcpy module "memcpymmxext"
[0x7fc21f875890] main interface debug: looking for interface module: 1 candidate
[0x7fc21f875890] main interface debug: using interface module "hotkeys"
[0x7fc21f875770] main interface debug: looking for interface module: 1 candidate
[0x7fc21f870d30] main playlist debug: Activated
[0x7fc21f875770] main interface debug: using interface module "inhibit"
[0x7fc21f870d30] main playlist debug: rebuilding array of current - root Playlist
[0x7fc21f870d30] main playlist debug: rebuild done - 0 items, index -1
[3990:3990:2004859328:ERROR:webplugin_delegate_impl_gtk.cc(132)] Not implemented reached in bool webkit::npapi::WebPluginDelegateImpl::WindowedCreatePlugin() windowed plugin but without xembed. See http://code.google.com/p/chromium/issues/detail?id=38229
[0x7fc21f505eb0] main libvlc debug: deactivating the playlist
[0x7fc21f870d30] main playlist debug: Deactivate
[0x7fc21f870d30] main playlist debug: Deactivated
[0x7fc21f505eb0] main libvlc debug: removing all services discovery tasks
[0x7fc21f505eb0] main libvlc debug: removing all interfaces
[0x7fc21f875770] main interface debug: removing module "inhibit"
[0x7fc21f875890] main interface debug: removing module "hotkeys"
[0x7fc21f870d30] main playlist debug: destroying
[0x7fc21f505eb0] main libvlc debug: removing stats
[0x7fc21f505eb0] main libvlc debug: removing module "memcpymmxext"
```

And in **Firefox** I get this:

```
osmodivs@Djiin:~$ firefox
4703473282 > 2419317540
CHECK IS 2160991483
[0x7feb66ed2550] main libvlc debug: VLC media player - 1.1.9 The Luggage
[0x7feb66ed2550] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x7feb66ed2550] main libvlc debug: revision exported
[0x7feb66ed2550] main libvlc debug: configured with ./configure  '--enable-static' '--build=x86_64-linux-gnu' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--sysconfdir=/etc' '--with-binary-version=1ubuntu1.3' '--enable-a52' '--enable-aa' '--enable-bonjour' '--enable-caca' '--enable-dca' '--enable-dirac' '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-ggi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libmpeg2' '--enable-libproxy' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mozilla' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-pulse' '--enable-qt4' '--enable-realrtsp' '--enable-schroedinger' '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--with-mozilla-pkg=libxul' '--disable-dxva2' '--disable-gnomevfs' '--disable-goom' '--disable-osso_screensaver' '--disable-portaudio' '--disable-projectm' '--disable-sqlite' '--disable-telx' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv' '--enable-libva' '--enable-pvr' '--enable-udev' '--enable-v4l2' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x7feb66ed2550] main libvlc debug: translation test: code is "C"
[0x7feb66ed2550] main libvlc debug: checking plugin modules
[0x7feb66ed2550] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins-04081e-7e8.dat
[0x7feb66ed2550] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x7feb66ed2550] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins-04081e-7e8.dat
[0x7feb66ed2550] main libvlc debug: module bank initialized (395 modules)
[0x7feb66ed2550] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 FPU 
[0x7feb66ed2550] main libvlc debug: looking for memcpy module: 3 candidates
[0x7feb66ed2550] main libvlc debug: using memcpy module "memcpymmxext"
[0x7feb6543ca70] main interface debug: looking for interface module: 1 candidate
[0x7feb6543ca70] main interface debug: using interface module "hotkeys"
[0x7feb6543cb80] main interface debug: looking for interface module: 1 candidate
[0x7feb7f54c4b0] main playlist debug: Activated
[0x7feb6543cb80] main interface debug: using interface module "inhibit"
[0x7feb7f54c4b0] main playlist debug: rebuilding array of current - root Playlist
[0x7feb7f54c4b0] main playlist debug: rebuild done - 0 items, index -1
[0x7feb7f70e670] main input debug: Creating an input for 'http://trailers.apple.com/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272'
[0x7feb7f70e670] main input debug: thread (input) created at priority 10 (input/input.c:220)
[0x7feb7f70e670] main input debug: thread started
[0x7feb7f70e670] main input debug: using timeshift granularity of 50 MiB
[0x7feb7f70e670] main input debug: using timeshift path '/tmp'
[0x7feb7f70e670] main input debug: `http://trailers.apple.com/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272' gives access `http' demux `' path `trailers.apple.com/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272'
[0x7feb7f70e670] main input debug: creating demux: access='http' demux='' path='trailers.apple.com/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272'
[0x7feb7fa189f0] main demux debug: looking for access_demux module: 0 candidates
[0x7feb7fa189f0] main demux debug: no access_demux module matched "http"
[0x7feb7f70e670] main input debug: creating access 'http' path='trailers.apple.com/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272'
[0x7feb7fa48060] main access debug: looking for access module: 2 candidates
[0x7feb7fa48060] access_http access debug: asking libproxy about url 'http://trailers.apple.com/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272'
[0x7feb7fa48060] access_http access debug: libproxy suggest to use 'direct://'
[0x7feb7fa48060] access_http access debug: http: server='trailers.apple.com' port=80 file='/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272'
[0x7feb7fa48060] main access debug: net: connecting to trailers.apple.com port 80
[0x7feb7fa48060] main access debug: connection succeeded (socket = 84)
[0x7feb7fa48060] access_http access debug: protocol 'HTTP' answer code 206
[0x7feb7fa48060] access_http access debug: Server: Apache/2.2.3 (Oracle)
[0x7feb7fa48060] access_http access debug: Content-Type: video/quicktime
[0x7feb7fa48060] access_http access debug: stream size=434,pos=0,remaining=434
[0x7feb7fa48060] access_http access debug: this frame size=434
[0x7feb7fa48060] access_http access debug: Connection: close
[0x7feb7fa48060] main access debug: using access module "access_http"
[0x7feb642548e0] main stream debug: Using AStream*Stream
[0x7feb642548e0] main stream debug: pre buffering
[0x7feb642548e0] main stream debug: received first data after 0 ms
[0x7feb642548e0] main stream debug: pre-buffering done 434 bytes in 0s - 17659 KiB/s
[0x7feb64254a10] main stream debug: looking for stream_filter module: 5 candidates
[0x7feb64254a10] main stream debug: no stream_filter module matching "any" could be loaded
[0x7feb64254a10] main stream debug: looking for stream_filter module: 1 candidate
[0x7feb64254a10] main stream debug: using stream_filter module "stream_filter_record"
[0x7feb7f70e670] main input debug: creating demux: access='http' demux='' path='trailers.apple.com/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272'
[0x7feb7fa188b0] main demux debug: looking for demux module: 52 candidates
[0x7feb7fa188b0] mp4 demux warning: MP4 plugin discarded (not fastseekable)
[0x7feb642180b0] main demux packetizer debug: looking for packetizer module: 21 candidates
[0x7feb642180b0] main demux packetizer debug: using packetizer module "packetizer_mpegvideo"
[0x7feb7f70e670] main input debug: selecting program id=0
[0x7feb7fa188b0] main demux debug: using demux module "mpgv"
[0x7feb6421f8b0] main decoder debug: looking for decoder module: 30 candidates
[0x7feb6421f8b0] avcodec decoder debug: libavcodec initialized (interface 0x344802)
[0x7feb6421f8b0] avcodec decoder debug: trying to use direct rendering
[0x7feb6421f8b0] avcodec decoder debug: ffmpeg codec (MPEG-1/2 Video) started
[0x7feb6421f8b0] main decoder debug: using decoder module "avcodec"
[0x7feb6421f8b0] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:301)
[0x7feb6421f8b0] main decoder debug: thread started
[0x7feb7f5fc1b0] main demux meta debug: looking for meta reader module: 2 candidates
[0x7feb7f5fc1b0] lua demux meta debug: Trying Lua scripts in /home/osmodivs/.local/share/vlc/lua/meta/reader
[0x7feb7f5fc1b0] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x7feb7f5fc1b0] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x7feb7f5fc1b0] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x7feb7f5fc1b0] main demux meta debug: no meta reader module matching "any" could be loaded
[0x7feb7f70e670] main input debug: `http://trailers.apple.com/movies/independent/thelegendisborn/thelegendisbornipman-tlr1_r640s.mov?width=640&height=272' successfully opened
[0x7feb7f70e670] main input debug: EOF reached
[0x7feb6421f8b0] avcodec decoder debug: ffmpeg codec (MPEG-1/2 Video) stopped
[0x7feb6421f8b0] main decoder debug: removing module "avcodec"
[0x7feb6421f8b0] main decoder debug: killing decoder fourcc `mpgv', 0 PES in FIFO
[0x7feb642180b0] main demux packetizer debug: removing module "packetizer_mpegvideo"
[0x7feb7fa188b0] main demux debug: removing module "mpgv"
[0x7feb64254a10] main stream debug: removing module "stream_filter_record"
[0x7feb7fa48060] main access debug: removing module "access_http"
[0x7feb7fa48060] main access debug: waitpipe: object killed
[0x7feb7f70e670] main input debug: Program doesn't contain anymore ES
[0x7feb7f70e670] main input debug: thread ended
```

What's wrong with this so called *STABLE* Ubuntu ***11.04 64bits***?

---

### Post by oldos2er on 2011-10-07
Post moved to its own thread. Please try not to post in threads more than a year old.

---

### Post by mc4man on 2011-10-07
If you are using the mozilla-plugin-vlc then try something else, it's not very good and has some 'issues' with apple depending on version of vlc
The totem-mozilla or gecko-mediaplayer are fine, generally best to only install one at a time

---

