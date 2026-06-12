---
title: "DVD problem"
date: 2021-04-23
forum: Multimedia Software
---

### Post by zkab on 2021-04-23
I can't play DVD with VLC.
I have upgraded to 21.04
My /etc/apt/source.list looks like this:
```
forsete@balder:/etc/apt$ cat sources.list
deb http://archive.ubuntu.com/ubuntu hirsute main restricted
deb http://archive.ubuntu.com/ubuntu hirsute-updates main restricted
deb http://archive.ubuntu.com/ubuntu hirsute universe
deb http://archive.ubuntu.com/ubuntu hirsute-updates universe
deb http://archive.ubuntu.com/ubuntu hirsute multiverse
deb http://archive.ubuntu.com/ubuntu hirsute-updates multiverse
deb http://archive.ubuntu.com/ubuntu hirsute-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ hirsute-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hirsute partner
deb-src http://archive.canonical.com/ubuntu hirsute partner
deb http://archive.ubuntu.com/ubuntu hirsute-security main restricted
deb http://archive.ubuntu.com/ubuntu hirsute-security universe
deb http://archive.ubuntu.com/ubuntu hirsute-security multiverse

```

Appreciate help ...

---

### Post by CelticWarrior on 2021-04-23
Welcome.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by zkab on 2021-04-23
Thanks ...
I forgot to mention in my earlier post that I already followed that link and installed 'sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg'
As you can see from below
```
forsete@balder:~$ sudo apt install libdvd-pkg
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
libdvd-pkg is already the newest version (1.4.2-1-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
forsete@balder:~$ sudo dpkg-reconfigure libdvd-pkg
libdvd-pkg: guest package [libdvdcss2/1.4.2-1~local] is already installed.
forsete@balder:~$
```

but still can't play DVD in VLC ... when I open the disc in VLC a window pops-up and then it goes away

---

### Post by CelticWarrior on 2021-04-23
Can you play it with other software?

---

### Post by zkab on 2021-04-23
I managed to rip it with Handbrake ... but with VLC ... no success

---

### Post by CelticWarrior on 2021-04-23
Please run ```
snap list
``` and check if VLC is listed there. If so the VLC version you installed is a snap and need to enable additional permissions.

---

### Post by zkab on 2021-04-24
VLC is not in the list ...
```
forsete@balder:~$ snap list
Name                     Version                     Rev    Tracking         Publisher           Notes
blender                  2.92.0                      111    latest/stable    blenderfoundation&#10003;  classic
core                     16-2.49.2                   10958  latest/stable    canonical&#10003;          core
core18                   20210309                    1997   latest/stable    canonical&#10003;          base
gnome-3-28-1804          3.28.0-19-g98f9e67.98f9e67  145    latest/stable    canonical&#10003;          -
gnome-3-34-1804          0+git.3556cb3               66     latest/stable/…  canonical&#10003;          -
gnome-system-monitor     3.38.0-17-g38c1ce1d62       157    latest/stable/…  canonical&#10003;          -
gtk-common-themes        0.1-52-gb92ac40             1515   latest/stable/…  canonical&#10003;          -
gtk2-common-themes       0.1                         13     latest/stable    canonical&#10003;          -
kde-frameworks-5-core18  5.61.0                      32     latest/stable    kde&#10003;                -
snap-store               3.38.0-59-g494f078          518    latest/stable/…  canonical&#10003;          -
spotify                  1.1.55.498.gf9a83c60        46     latest/stable    spotify&#10003;            -
forsete@balder:~$ 
```

---

### Post by CelticWarrior on 2021-04-24
Then it's not what I was thinking.

Unfortunately you didn't test with other players to rule out the DVD itself. Handbrake supports a wide range of formats and read many thing s that normal media players don't.

---

### Post by zkab on 2021-04-24
OK ... I tested the DVD with 'Gnome Videos' and it worked fine (both video&sound) ... also MPlayer worked OK from command line (but no sound).
So the DVD seems to be fine.
I created a logfile from VLC ...
```
-- logger module started --
main debug: VLC media player - 3.0.12 Vetinari
main debug: Copyright © 1996-2020 the VideoLAN team
main debug: revision 3.0.12-1-0-gd147bb5e7e
main debug: configured with ./configure  '--build=x86_64-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--disable-option-checking' '--disable-silent-rules' '--libdir=${prefix}/lib/x86_64-linux-gnu' '--runstatedir=/run' '--disable-maintainer-mode' '--disable-dependency-tracking' '--disable-debug' '--config-cache' '--disable-update-check' '--enable-fast-install' '--docdir=/usr/share/doc/vlc' '--with-binary-version=3.0.12-3' '--enable-a52' '--enable-aa' '--enable-aribsub' '--enable-avahi' '--enable-bluray' '--enable-caca' '--enable-chromaprint' '--enable-chromecast' '--enable-dav1d' '--enable-dbus' '--enable-dca' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gles2' '--enable-gnutls' '--enable-harfbuzz' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libmpeg2' '--enable-libxml2' '--enable-lirc' '--enable-mad' '--enable-matroska' '--enable-mod' '--enable-mpc' '--enable-mpg123' '--enable-mtp' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-pulse' '--enable-qt' '--enable-realrtsp' '--enable-samplerate' '--enable-sdl-image' '--enable-sftp' '--enable-shine' '--enable-shout' '--enable-skins2' '--enable-sndio' '--enable-soxr' '--enable-spatialaudio' '--enable-speex' '--enable-svg' '--enable-svgdec' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vdpau' '--enable-vnc' '--enable-vorbis' '--enable-x264' '--enable-x265' '--enable-zvbi' '--with-kde-solid=/usr/share/solid/actions/' '--disable-aom' '--disable-crystalhd' '--disable-d3d11va' '--disable-decklink' '--disable-directx' '--disable-dsm' '--disable-dxva2' '--disable-fdkaac' '--disable-fluidlite' '--disable-freerdp' '--disable-goom' '--disable-gst-decode' '--disable-libtar' '--disable-live555' '--disable-macosx' '--disable-macosx-avfoundation' '--disable-macosx-qtkit' '--disable-mfx' '--disable-microdns' '--disable-opencv' '--disable-projectm' '--disable-schroedinger' '--disable-sparkle' '--disable-srt' '--disable-telx' '--disable-vpx' '--disable-vsxu' '--disable-wasapi' '--enable-alsa' '--enable-dc1394' '--enable-dv1394' '--enable-libplacebo' '--enable-linsys' '--enable-nfs' '--enable-udev' '--enable-v4l2' '--enable-wayland' '--enable-libva' '--enable-vcd' '--enable-smbclient' '--disable-oss' '--enable-mmx' '--enable-sse' '--disable-neon' '--disable-altivec' '--disable-omxil' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2 -ffile-prefix-map=/build/vlc-HLg3gZ/vlc-3.0.12=. -fstack-protector-strong -Wformat -Werror=format-security ' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now' 'CPPFLAGS=-Wdate-time -D_FORTIFY_SOURCE=2' 'CXXFLAGS=-g -O2 -ffile-prefix-map=/build/vlc-HLg3gZ/vlc-3.0.12=. -fstack-protector-strong -Wformat -Werror=format-security ' 'OBJCFLAGS=-g -O2 -ffile-prefix-map=/build/vlc-HLg3gZ/vlc-3.0.12=. -fstack-protector-strong -Wformat -Werror=format-security'
main debug: searching plug-in modules
main debug: loading plugins cache file /usr/lib/x86_64-linux-gnu/vlc/plugins/plugins.dat
main debug: recursively browsing `/usr/lib/x86_64-linux-gnu/vlc/plugins'
main debug: plug-ins loaded: 519 modules
main debug: opening config file (/home/forsete/.config/vlc/vlcrc)
main debug: looking for logger module matching "any": 4 candidates
file debug: opening logfile `/home/forsete/Downloads/vlc-log'
main debug: using logger module "file"
main debug: translation test: code is "C"
main debug: looking for keystore module matching "memory": 4 candidates
main debug: using keystore module "memory"
main debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 SSE4.2 SSE4A AVX AVX2 FPU 
main debug: Creating an input for 'Media Library'
main debug: Input is a meta file: disabling unneeded options
main debug: using timeshift granularity of 50 MiB
main debug: using default timeshift path
main debug: `file/directory:///home/forsete/.local/share/vlc/ml.xspf' gives access `file' demux `directory' path `/home/forsete/.local/share/vlc/ml.xspf'
main debug: creating demux: access='file' demux='directory' location='/home/forsete/.local/share/vlc/ml.xspf' file='/home/forsete/.local/share/vlc/ml.xspf'
main debug: looking for access_demux module matching "file": 18 candidates
main debug: no access_demux modules matched
main debug: creating access: file:///home/forsete/.local/share/vlc/ml.xspf
main debug:  (path: /home/forsete/.local/share/vlc/ml.xspf)
main debug: looking for access module matching "file": 29 candidates
main debug: using access module "filesystem"
main debug: looking for stream_filter module matching "prefetch,cache_read": 26 candidates
cache_read debug: Using stream method for AStream*
cache_read debug: starting pre-buffering
cache_read debug: received first data after 0 ms
cache_read debug: pre-buffering done 296 bytes in 0s - 24088 KiB/s
main debug: using stream_filter module "cache_read"
main debug: looking for stream_filter module matching "any": 26 candidates
playlist debug: using XSPF playlist reader
main debug: using stream_filter module "playlist"
main debug: stream filter added to 0x55a972496740
main debug: looking for stream_filter module matching "any": 26 candidates
main debug: no stream_filter modules matched
main debug: looking for stream_directory module matching "any": 1 candidates
main debug: no stream_directory modules matched
main debug: attachment of directory-extractor failed for file:///home/forsete/.local/share/vlc/ml.xspf
main debug: looking for stream_filter module matching "record": 26 candidates
main debug: using stream_filter module "record"
main debug: creating demux: access='file' demux='directory' location='/home/forsete/.local/share/vlc/ml.xspf' file='/home/forsete/.local/share/vlc/ml.xspf'
main debug: looking for demux module matching "directory": 54 candidates
main debug: using demux module "directory"
main debug: looking for meta reader module matching "any": 2 candidates
lua debug: Trying Lua scripts in /home/forsete/.local/share/vlc/lua/meta/reader
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/reader
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/reader/filename.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
main debug: no meta reader modules matched
main debug: `file/directory:///home/forsete/.local/share/vlc/ml.xspf' successfully opened
main debug: looking for xml reader module matching "any": 1 candidates
main debug: using xml reader module "xml"
main debug: EOF reached
main debug: removing module "directory"
main debug: removing module "record"
main debug: removing module "playlist"
main debug: removing module "cache_read"
main debug: removing module "filesystem"
main debug: creating audio output
main debug: looking for audio output module matching "any": 6 candidates
vlcpulse debug: using library version 14.2.0
vlcpulse debug:  (compiled with version 14.2.0, protocol 34)
vlcpulse debug: connected locally to /run/user/1000/pulse/native as client #831
vlcpulse debug: using protocol 34, server protocol 34
pulse debug: adding sink 2: alsa_output.pci-0000_05_00.6.analog-stereo (Family 17h (Models 10h-1fh) HD Audio Controller Analog Stereo)
pulse debug: adding sink 5: alsa_output.pci-0000_05_00.1.hdmi-stereo-extra1 (Raven/Raven2/Fenghuang HDMI/DP Audio Controller Digital Stereo (HDMI 2))
main debug: using audio output module "pulse"
main debug: keeping audio output
main debug: looking for interface module matching "dbus,none": 19 candidates
dbus debug: listening on dbus as: org.mpris.MediaPlayer2.vlc
main debug: using interface module "dbus"
main debug: no running VLC instance - continuing normally...
main debug: looking for interface module matching "hotkeys,none": 19 candidates
main debug: using interface module "hotkeys"
main debug: looking for interface module matching "globalhotkeys,none": 19 candidates
main debug: using interface module "xcb_hotkeys"
main: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
main debug: looking for interface module matching "any": 19 candidates
dbus debug: Getting All properties
dbus debug: Getting All properties
dbus debug: Getting All properties
main debug: looking for extension module matching "any": 1 candidates
lua debug: Opening Lua Extension module
lua debug: Trying Lua scripts in /home/forsete/.local/share/vlc/lua/extensions
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/extensions
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/extensions/VLSub.luac
lua debug: Scanning Lua script /usr/lib/x86_64-linux-gnu/vlc/lua/extensions/VLSub.luac
lua debug: Script /usr/lib/x86_64-linux-gnu/vlc/lua/extensions/VLSub.luac has the following capability flags: 0x5
lua debug: Trying Lua scripts in /usr/share/vlc/lua/extensions
main debug: using extension module "lua"
main debug: looking for services probe module matching "any": 10 candidates
main debug: no services probe modules matched
qt debug: Sorting by column -1, order 0
qt debug: Sorting by column -1, order 0
main debug: using interface module "qt"
main: playlist is empty
main debug: nothing to play
main debug: looking for services_discovery module matching "disc": 14 candidates
udev debug: adding dvd:///dev/sr0 (Leiutajateküla Lotte (DVD))
main debug: adding: Leiutajateküla Lotte (DVD)
main debug: using services_discovery module "udev"
main debug: processing request item: Leiutajateküla Lotte (DVD), node: Discs, skip: 0
main debug: rebuilding array of current - root Discs
main debug: rebuild done - 1 items, index 0
main debug: starting playback of new item
main debug: resyncing on Leiutajateküla Lotte (DVD)
main debug: Leiutajateküla Lotte (DVD) is at 0
main debug: creating new input thread
main debug: Creating an input for 'Leiutajateküla Lotte (DVD)'
main debug: requesting art for new input thread
main debug: using timeshift granularity of 50 MiB
main debug: using default timeshift path
main debug: `dvd:///dev/sr0' gives access `dvd' demux `any' path `/dev/sr0'
main debug: creating demux: access='dvd' demux='any' location='/dev/sr0' file='/dev/sr0'
main debug: looking for access_demux module matching "dvd": 18 candidates
main debug: looking for meta fetcher module matching "any": 1 candidates
lua debug: Trying Lua scripts in /home/forsete/.local/share/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
main debug: no meta fetcher modules matched
main debug: looking for art finder module matching "any": 2 candidates
qt debug: IM: Setting an input
lua debug: Trying Lua scripts in /home/forsete/.local/share/vlc/lua/meta/art
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
lua debug: skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
lua debug: skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
lua debug: skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
lua debug: skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
main debug: no art finder modules matched
main debug: looking for meta fetcher module matching "any": 1 candidates
lua debug: Trying Lua scripts in /home/forsete/.local/share/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
main debug: no meta fetcher modules matched
main debug: looking for art finder module matching "any": 2 candidates
lua debug: Trying Lua scripts in /home/forsete/.local/share/vlc/lua/meta/art
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
main debug: no art finder modules matched
dvdnav error: Zero check failed in src/ifo_read.c:567 for vmgi_mat->zero_3 : 0x00000000010000000000000000000000000000
dvdnav: DVD Title: Leiutajatek la Lotte
dvdnav: DVD Serial Number: 355fbccf
dvdnav: DVD Title (Alternative): 
dvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 01 02 03 04 05 06 07 08
dvdnav debug: trying to go to dvd menu
main debug: using access_demux module "dvdnav"
main debug: attempt to destroy nonexistent variable "title  0"
main debug: attempt to destroy nonexistent variable "title  1"
main debug: attempt to destroy nonexistent variable "title  2"
main debug: attempt to destroy nonexistent variable "title  3"
main debug: looking for meta reader module matching "any": 2 candidates
lua debug: Trying Lua scripts in /home/forsete/.local/share/vlc/lua/meta/reader
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/reader
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/reader/filename.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
main debug: no meta reader modules matched
main debug: `dvd:///dev/sr0' successfully opened
dvdnav debug: DVDNAV_HOP_CHANNEL
main debug: ES_OUT_RESET_PCR called
dvdnav debug: DVDNAV_HIGHLIGHT
dvdnav debug:      - display=1
dvdnav debug:      - buttonN=1
dvdnav debug: buttonUpdate not done b=1 t=0
dvdnav: Attempting to retrieve all CSS keys
dvdnav: This can take a _long_ time, please be patient
dvdnav debug: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000159
dvdnav debug: Elapsed time 0
dvdnav debug: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0002a31e
dvdnav debug: Elapsed time 0
dvdnav debug: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000e236a
dvdnav debug: Elapsed time 0
dvdnav debug: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00310d61
dvdnav debug: Elapsed time 0
dvdnav debug: Found 3 VTS's
dvdnav debug: Elapsed time 0
dvdnav debug: DVDNAV_VTS_CHANGE
dvdnav debug:      - vtsN=1
dvdnav debug:      - domain=8
main debug: ES_OUT_RESET_PCR called
dvdnav debug: DVDNAV_CELL_CHANGE
dvdnav debug:      - cellN=1
dvdnav debug:      - pgN=1
dvdnav debug:      - cell_length=82590
dvdnav debug:      - pg_length=82590
dvdnav debug:      - pgc_length=648000
dvdnav debug:      - cell_start=0
dvdnav debug:      - pg_start=0
dvdnav debug: DVDNAV_SPU_CLUT_CHANGE
dvdnav debug: DVDNAV_SPU_STREAM_CHANGE
dvdnav debug:      - physical_wide=0
dvdnav debug:      - physical_letterbox=0
dvdnav debug:      - physical_pan_scan=0
dvdnav debug: buttonUpdate not done b=1 t=0
main debug: selecting program id=0
main debug: looking for packetizer module matching "any": 25 candidates
main debug: using packetizer module "spudec"
main debug: looking for spu decoder module matching "any": 22 candidates
main debug: using spu decoder module "spudec"
dvdnav debug: DVDNAV_AUDIO_STREAM_CHANGE
dvdnav debug:      - physical=0
main debug: Buffering 0%
dvdnav debug: buttonUpdate not done b=1 t=0
main debug: looking for packetizer module matching "any": 25 candidates
main debug: using packetizer module "mpegvideo"
main debug: looking for video decoder module matching "any": 15 candidates
avcodec debug: using ffmpeg Lavc58.91.100
avcodec debug: CPU flags: 0x000fd3db
avcodec debug: allowing 6 thread(s) for decoding
avcodec debug: codec (mpeg2video) started
main debug: using video decoder module "avcodec"
dvdnav debug: buttonUpdate not done b=1 t=0
mpegvideo debug: size 720x576/720x576 fps=25,000
main debug: Buffering 1%
main debug: Buffering 2%
main debug: restarting module due to input format change
main debug: Buffering 3%
main debug: removing module "avcodec"
main debug: Buffering 4%
main debug: looking for video decoder module matching "any": 15 candidates
avcodec debug: using ffmpeg Lavc58.91.100
avcodec debug: CPU flags: 0x000fd3db
main debug: Buffering 5%
avcodec debug: allowing 6 thread(s) for decoding
main debug: Buffering 6%
avcodec debug: codec (mpeg2video) started
main debug: using video decoder module "avcodec"
main debug: Buffering 7%
avcodec debug: available hardware decoder output format 119 (cuda)
avcodec debug: available hardware decoder output format 153 (xvmc)
avcodec debug: available hardware decoder output format 100 (vdpau)
avcodec debug: available hardware decoder output format 46 (vaapi_vld)
avcodec debug: available software decoder output format 0 (yuv420p)
avcodec debug: trying format vaapi_vld
main debug: Buffering 8%
main debug: Buffering 9%
main debug: Buffering 10%
main debug: looking for text renderer module matching "any": 2 candidates
main debug: Buffering 11%
main debug: Buffering 12%
main debug: Buffering 13%
main debug: Buffering 14%
main debug: Buffering 15%
main debug: Stream buffering done (400 ms in 8 ms)
freetype debug: Building font databases.
freetype debug: Took -22910 microseconds
main debug: using text renderer module "freetype"
main debug: looking for video converter module matching "any": 23 candidates
swscale debug: 32x32 (32x32) chroma: YUVA -> 16x16 (16x16) chroma: RGBA with scaling using Bicubic (good quality)
main debug: using video converter module "swscale"
main debug: looking for video converter module matching "any": 23 candidates
yuvp debug: YUVP to YUVA converter
main debug: using video converter module "yuvp"
main debug: Deinterlacing available
main debug: deinterlace -1, mode auto, is_needed 0
main debug: looking for vout window module matching "qt,any": 6 candidates
qt debug: requesting video window...
main debug: using vout window module "qt"
main debug: looking for inhibit module matching "any": 2 candidates
main debug: resized to 720x576
dbus_screensaver debug: found service org.freedesktop.ScreenSaver
main debug: using inhibit module "dbus_screensaver"
main debug: Opening vout display wrapper
main debug: looking for vout display module matching "any": 14 candidates
main debug: VoutDisplayEvent 'resize' 720x576
main debug: looking for opengl module matching "any": 3 candidates

```

---

