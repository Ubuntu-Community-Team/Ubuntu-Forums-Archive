---
title: "VLC Will Not Load."
date: 2014-06-16
forum: Multimedia Software
---

### Post by jooge on 2014-06-16
I just installed VLC media player as I always do when I install Ubuntu (I just upgraded to 14.04 last night). After it successfully installed through the Ubuntu Software Center the icon appeared but when I clicked on it it flashed  twice and then did nothing. I uninstalled and reinstalled it and the same thing happened. I even tried installing it via PPA and the same thing still happened. Can someone plz help me out? I dont know what this all means unfortuneatley so I hope someone can point me in the right direction:


VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x65c118] main libvlc debug: VLC media player - 2.1.4 Rincewind
[0x65c118] main libvlc debug: Copyright © 1996-2014 the VideoLAN team
[0x65c118] main libvlc debug: revision 2.1.4-0-g2a072be
[0x65c118] main libvlc debug: configured with ./configure  '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--localstatedir=/var' '--libdir=${prefix}/lib/x86_64-linux-gnu' '--libexecdir=${prefix}/lib/x86_64-linux-gnu' '--disable-dependency-tracking' '--build=x86_64-linux-gnu' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--libdir=/usr/lib' '--sysconfdir=/etc' '--with-binary-version=0ubuntu14.04.1' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-chromaprint' '--enable-dbus' '--enable-dca' '--enable-dirac' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libfreerdp' '--enable-libmpeg2' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-oss' '--enable-pulse' '--enable-qt' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-sftp' '--enable-shout' '--enable-skins2' '--enable-smbclient' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-decklink' '--disable-dxva2' '--disable-fdkaac' '--disable-gnomevfs' '--disable-goom' '--disable-libvnc' '--disable-opencv' '--disable-projectm' '--disable-quicksync' '--disable-sndio' '--disable-telx' '--disable-vsxu' '--disable-wasapi' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv1394' '--enable-linsys' '--enable-omxil' '--enable-udev' '--enable-libva' '--enable-v4l2' '--enable-crystalhd' '--enable-mmx' '--enable-sse' '--disable-neon' '--disable-altivec' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'build_alias=x86_64-linux-gnu'
[0x65c118] main libvlc debug: searching plug-in modules
[0x65c118] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x65c118] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x65c118] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x65c118] main libvlc debug: plug-ins loaded: 426 modules
[0x65c118] main libvlc debug: opening config file (/home/jooge/.config/vlc/vlcrc)
[0x65c118] main libvlc debug: translation test: code is "C"
[0x65c118] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSE4A 3DNow! FPU 
[0x688328] main input debug: Creating an input for 'Media Library'
[0x688328] main input debug: Input is a meta file: disabling unneeded options
[0x688328] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x688328] main input debug: `file/xspf-open:///home/jooge/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/jooge/.local/share/vlc/ml.xspf'
[0x688328] main input debug: creating demux: access='file' demux='xspf-open' location='/home/jooge/.local/share/vlc/ml.xspf' file='/home/jooge/.local/share/vlc/ml.xspf'
[0x676dd8] main demux debug: looking for access_demux module matching "file": 20 candidates
[0x676dd8] main demux debug: no access_demux modules matched
[0x688328] main input debug: creating access 'file' location='/home/jooge/.local/share/vlc/ml.xspf', path='/home/jooge/.local/share/vlc/ml.xspf'
[0x722d78] main access debug: looking for access module matching "file": 25 candidates
[0x722d78] filesystem access debug: opening file `/home/jooge/.local/share/vlc/ml.xspf'
[0x722d78] main access debug: using access module "filesystem"
[0x723ac8] main stream debug: Using stream method for AStream*
[0x723ac8] main stream debug: starting pre-buffering
[0x723ac8] main stream debug: received first data after 0 ms
[0x723ac8] main stream debug: pre-buffering done 296 bytes in 0s - 8029 KiB/s
[0x723d28] main stream debug: looking for stream_filter module matching "any": 9 candidates
[0x723d28] main stream debug: no stream_filter modules matched
[0x723d28] main stream debug: looking for stream_filter module matching "record": 9 candidates
[0x723d28] main stream debug: using stream_filter module "record"
[0x688328] main input debug: creating demux: access='file' demux='xspf-open' location='/home/jooge/.local/share/vlc/ml.xspf' file='/home/jooge/.local/share/vlc/ml.xspf'
[0x726d38] main demux debug: looking for demux module matching "xspf-open": 63 candidates
[0x726d38] playlist demux debug: using XSPF playlist reader
[0x726d38] main demux debug: using demux module "playlist"
[0x726fe8] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x726fe8] lua demux meta debug: Trying Lua scripts in /home/jooge/.local/share/vlc/lua/meta/reader
[0x726fe8] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x726fe8] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x726fe8] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x726fe8] main demux meta debug: no meta reader modules matched
[0x688328] main input debug: `file/xspf-open:///home/jooge/.local/share/vlc/ml.xspf' successfully opened
[0x730428] main xml reader debug: looking for xml reader module matching "any": 1 candidates
[0x730428] main xml reader debug: using xml reader module "xml"
[0x726d38] playlist demux debug: parsed 0 tracks successfully
[0x688328] main input debug: EOF reached
[0x726d38] main demux debug: removing module "playlist"
[0x723d28] main stream debug: removing module "record"
[0x722d78] main access debug: removing module "filesystem"
[0x670088] main playlist debug: creating audio output
[0x733488] main audio output debug: looking for audio output module matching "any": 6 candidates
[0x733488] pulse audio output debug: using library version 4.0.0
[0x733488] pulse audio output debug:  (compiled with version 4.0.0, protocol 28)
[0x733488] pulse audio output debug: connected locally to unix:/run/user/1000/pulse/native as client #19
[0x733488] pulse audio output debug: using protocol 28, server protocol 28
[0x733488] main audio output debug: using audio output module "pulse"
[0x670088] main playlist debug: keeping audio output
[0x676408] main interface debug: looking for interface module matching "hotkeys,none": 19 candidates
[0x676408] main interface debug: using interface module "hotkeys"
[0x734db8] main interface debug: looking for interface module matching "globalhotkeys,none": 19 candidates
[0x733488] pulse audio output debug: adding sink 0: alsa_output.pci-0000_00_14.2.analog-stereo (Built-in Audio Analog Stereo)
[0x734db8] main interface debug: using interface module "globalhotkeys"
[0x7218b8] main interface debug: looking for interface module matching "dbus,none": 19 candidates
[0x7218b8] dbus interface debug: listening on dbus as: org.mpris.MediaPlayer2.vlc.instance6063
[0x7218b8] main interface debug: using interface module "dbus"
[0x68b428] main interface debug: looking for interface module matching "skins2,any": 19 candidates
[0x68b428] skins2 interface debug: EWMH: supported 1
[0x68b428] skins2 interface debug: _NET_WM_STATE support: yes
[0x68b428] skins2 interface debug: _NET_WM_STATE_FULLSCREEN support: yes
[0x68b428] skins2 interface debug: _NET_WM_STATE_STAYS_ON_TOP support: no
[0x68b428] skins2 interface debug: _NET_WM_STATE_ABOVE support: yes
[0x68b428] skins2 interface debug: _NET_WM_WINDOW_OPACITY support: yes
[0x68b428] skins2 interface debug: _NET_WM_PID support: no
[0x68b428] skins2 interface debug: number of monitors detected : 1
[0x68b428] skins2 interface debug:   monitor #0 : 1366x768 at +0+0
[0x68b428] skins2 interface debug: cannot open directory /home/jooge/.local/share/vlc/skins2
[0x68b428] skins2 interface debug: cannot open directory share/skins2
[0x68b428] skins2 interface debug: found skin /usr/share/vlc/skins2/default.vlt
[0x68b428] skins2 interface debug: requested skins /home/jooge/Documents/VLC Skins/165521-KeepItCleanv1.vlt is NOT accessible
[0x7fe5a8029178] main generic debug: looking for dialogs provider module matching "any": 1 candidates

(vlc:6063): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

(vlc:6063): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(vlc:6063): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",
[0x7fe5a8029178] main generic debug: using dialogs provider module "qt4"
Segmentation fault (core dumped)

---

### Post by Yellow Pasque on 2014-06-16
Can you start with a default configuration?
```
vlc --ignore-config
```

---

### Post by jooge on 2014-06-16
> **Temüjin said:**
> Can you start with a default configuration?
```
vlc --ignore-config
```

Holy Cow!

[[IMG]http://thumbnails109.imagebam.com/33360/137ca8333590526.jpg[/IMG]](http://www.imagebam.com/image/137ca8333590526) 


That did it. Thanks a ton my friend.

---

### Post by Yellow Pasque on 2014-06-16
That was just a temporary measure. If you use --ignore-config every time, your preferences/options will never be saved. You may want to run with --reset-config to delete your old configuration.

---

