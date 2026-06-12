---
title: "Chromium no longer plays embedded quicktime videos on apple.com"
date: 2010-06-27
forum: Multimedia Software
---

### Post by maddbaron on 2010-06-27
i've had ubuntu 10.04 for almost 2 months and when i first installed all the media codecs and used chromium everything worked fine and I was able to watch videos on apple.com but for past 2 weeks I haven't...there's been no change to my files, justed updated Chromium. I can view .mov video's in the media players or if I have the direct address but not embedded.

Anything I can do to fix this?

---

### Post by mc4man on 2010-06-27
No issue here on 10.04 and most apple trailers in Chromium browser (using the daily ppa.
It depends on the the clip and the plugin being used
 - 
Using totem-mozilla plugin all of the 'watch now' clips work fine, either in browser from 'watch now', expanding the arrow -> download and going r.click -> open link in new tab or window, or using the arrow on right side to open in external player (totem by default)

The other advantage to totem-mozilla plugin is it caches apple trailers very quickly in /tmp - many times I just start the cache, pause the browser player and play from the cache with vlc or mplayer - better quality playback
(you can play the file as it's being cached, no need to wait

For the older style - the grey box - 'choose a clip' - the gecko-mediaplayer plugin works better - totem-mozilla seems to have stopped working on those correctly.
(though you can wget those and play in an external player

---

### Post by mc4man on 2010-06-27
duped post..

---

### Post by redvil on 2011-05-03
i used to be able to play movie trailers from apple.com using chromium browser...now it just displays the screen with the words: Missing Plugin 

how do i get this said plugin?

---

### Post by fromgi on 2011-05-03
Something must have changed over the weekend.  On Friday I played the trailers with the Totem plugin, but today when you click on a movie and go the movie page, the drop down menus have disappeared.

---

### Post by Osmodivs on 2011-10-07
I can't play *Apple* videos either, all I get is this:


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

What on earth is wrong with my **_Ubuntu 11.04 56 bits_**!?

---

