---
title: "VLC w/ HEVC"
date: 2016-05-24
forum: Multimedia Software
---

### Post by czgirb on 2016-05-24
today, i follow the instruction from [http://askubuntu.com/questions/631200/unable-to-play-hevc-files-on-ubuntu-14-04-lte](http://askubuntu.com/questions/631200/unable-to-play-hevc-files-on-ubuntu-14-04-lte) and i have this result

```

czgirb@ubuntu:~$ sudo apt-add-repository ppa:strukturag/libde265
[sudo] password for czgirb: 
 libde265 is an open source implementation of the h.265 video codec. It is written from scratch and has a plain C API to enable a simple integration into other software.

libde265 supports WPP and tile-based multithreading and includes SSE optimizations. The decoder supports all features of the Main and Main10 profile (HEVC-V1) and most profiles of HEVC-V2 (chroma 4:2:2, 4:4:4, monochrome, and bit depths up to 14 bits).

libde265 is released under the LGPL, further information are available at
[http://www.libde265.org](http://www.libde265.org)
[https://github.com/strukturag/libde265](https://github.com/strukturag/libde265)

This PPA contains Ubuntu packages of the libde265 library, plugins for
the GStreamer framework, VLC and required dependencies.

The GStreamer plugin source is available at
[https://github.com/strukturag/gstreamer-libde265](https://github.com/strukturag/gstreamer-libde265)

The VLC plugin source is available at
[https://github.com/strukturag/vlc-libde265](https://github.com/strukturag/vlc-libde265)

You can get sample Matroska streams from
[http://www.libde265.org/downloads-videos/](http://www.libde265.org/downloads-videos/)
[http://www.divx.com/de/hevc](http://www.divx.com/de/hevc)
[http://labs.divx.com/node/127909](http://labs.divx.com/node/127909)
 More info: [https://launchpad.net/~strukturag/+archive/ubuntu/libde265](https://launchpad.net/~strukturag/+archive/ubuntu/libde265)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpjvzl5x7b/secring.gpg' created
gpg: keyring `/tmp/tmpjvzl5x7b/pubring.gpg' created
gpg: requesting key 705C2B92 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpjvzl5x7b/trustdb.gpg: trustdb created
gpg: key 705C2B92: public key "Launchpad PPA for struktur AG" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
czgirb@ubuntu:~$

```

is there anybody know what it is? please guide me ...
[B]thank you

i use ubuntu 14.04 LTS with VLC 2.1.6 Rincewind
[/B]

---

### Post by mc4man on 2016-05-24
Install the plugin
sudo apt-get install vlc-plugin-libde265

---

### Post by czgirb on 2016-05-24
> **mc4man said:**
> Install the plugin
sudo apt-get install vlc-plugin-libde265

installed already

```
czgirb@ubuntu:~$ sudo apt-get install vlc-plugin-libde265 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc-plugin-libde265 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic
  linux-image-3.13.0-76-generic linux-image-extra-3.13.0-76-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
czgirb@ubuntu:~$ 
```

when i open the h265 hevc, the vlc was shown ... but it just to be disappear in no more than a second
**why?**

---

### Post by mc4man on 2016-05-24
Why?,  - maybe run vlc from a terminal & see what it reports when it crashes.
also you could go here & download one of the hevc test files - see if it works. The 2nd one down would be fine
[http://jell.yfish.us/](http://jell.yfish.us/)

---

### Post by czgirb on 2016-05-24
> **mc4man said:**
> Why?,  - maybe run vlc from a terminal & see what it reports when it crashes.
also you could go here & download one of the hevc test files - see if it works. The 2nd one down would be fine
[http://jell.yfish.us/](http://jell.yfish.us/)

as requested
```
czgirb@ubuntu:~$ vlc jellyfish-3-mbps-hd-hevc.mkv
VLC media player 2.2.1 Terry Pratchett (Weatherwax) (revision 2.2.1~trusty2)
[08ea9910] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[b1a0b768] filesystem access error: cannot open file /home/czgirb/jellyfish-3-mbps-hd-hevc.mkv (No such file or directory)
[b0504e98] core input error: open of `file:///home/czgirb/jellyfish-3-mbps-hd-hevc.mkv' failed
```

terminal update
```
czgirb@ubuntu:~$ vlc jellyfish-3-mbps-hd-hevc.mkv
VLC media player 2.2.1 Terry Pratchett (Weatherwax) (revision 2.2.1~trusty2)
[09194910] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Segmentation fault (core dumped)
czgirb@ubuntu:~$ 
```


from vlc
 [COLOR=#ff0000]```

File reading failed:
```[/COLOR]```


 [COLOR=#000000]VLC could not open the file "/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv" (No such file or directory).[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'file:///home/czgirb/jellyfish-3-mbps-hd-hevc.mkv'. Check the log for details.
[/COLOR]
```

---

### Post by mc4man on 2016-05-24
Where is the file you downloaded?, your command is saying open from your home folder.

Also you said you where using vlc-2.16 but you are not. 

So - what's this show? (just a simulation
```
sudo apt-get -s dist-upgrade
```
Also run this, then try to open a hevc file in vlc, you could just open vlc > Media > Open file > browse to & pick..
```
rm ~/.config/vlc
```

---

### Post by czgirb on 2016-05-24
as requested

```
czgirb@ubuntu:~$ sudo apt-get -s dist-upgrade
[sudo] password for czgirb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic
  linux-image-3.13.0-76-generic linux-image-extra-3.13.0-76-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  apport apport-gtk audacity audacity-data bash-completion python3-apport
  python3-problem-report
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst bash-completion [1:2.1-4ubuntu0.1] (1:2.1-4ubuntu0.2 Ubuntu:14.04/trusty-updates [all])
Inst python3-problem-report [2.14.1-0ubuntu3.19] (2.14.1-0ubuntu3.20 Ubuntu:14.04/trusty-updates [all])
Inst python3-apport [2.14.1-0ubuntu3.19] (2.14.1-0ubuntu3.20 Ubuntu:14.04/trusty-updates [all])
Inst apport [2.14.1-0ubuntu3.19] (2.14.1-0ubuntu3.20 Ubuntu:14.04/trusty-updates [all])
Inst apport-gtk [2.14.1-0ubuntu3.19] (2.14.1-0ubuntu3.20 Ubuntu:14.04/trusty-updates [all])
Inst audacity [2.1.2+git20160518+r4264+19~ubuntu14.04.1] (2.1.2+git20160523+r4275+19~ubuntu14.04.1 Audacity Daily Build:14.04/trusty [i386]) []
Inst audacity-data [2.1.2+git20160518+r4264+19~ubuntu14.04.1] (2.1.2+git20160523+r4275+19~ubuntu14.04.1 Audacity Daily Build:14.04/trusty [all])
Conf bash-completion (1:2.1-4ubuntu0.2 Ubuntu:14.04/trusty-updates [all])
Conf python3-problem-report (2.14.1-0ubuntu3.20 Ubuntu:14.04/trusty-updates [all])
Conf python3-apport (2.14.1-0ubuntu3.20 Ubuntu:14.04/trusty-updates [all])
Conf apport (2.14.1-0ubuntu3.20 Ubuntu:14.04/trusty-updates [all])
Conf apport-gtk (2.14.1-0ubuntu3.20 Ubuntu:14.04/trusty-updates [all])
Conf audacity-data (2.1.2+git20160523+r4275+19~ubuntu14.04.1 Audacity Daily Build:14.04/trusty [all])
Conf audacity (2.1.2+git20160523+r4275+19~ubuntu14.04.1 Audacity Daily Build:14.04/trusty [i386])
czgirb@ubuntu:~$ 
```

vlc > media > open file > browse to pick file ... and the vlc was launched & disappeared before a minute

how to run **rm ~/.config/vlc** ??? copy and paste ???
```
czgirb@ubuntu:~$ rm ~/.config/vlc
rm: cannot remove &#8216;/home/czgirb/.config/vlc&#8217;: Is a directory
czgirb@ubuntu:~$ 
```

---

### Post by mc4man on 2016-05-24
Sorry, forgot it's a folder, so - 
```
rm -rf ~/.config/vlc
```
Otherwise you look ok

---

### Post by czgirb on 2016-05-24
> **mc4man said:**
> Sorry, forgot it's a folder, so - 
```
rm -rf ~/.config/vlc
```
Otherwise you look ok

runned, but the result still the same
Terminal
```

czgirb@ubuntu:~$ rm -rf ~/.config/vlc
czgirb@ubuntu:~$ cvlc jellyfish-3-mbps-hd-hevc.mkv
VLC media player 2.2.1 Terry Pratchett (Weatherwax) (revision 2.2.1~trusty2)
[087b2540] dummy interface: using the dummy interface module...
Segmentation fault (core dumped)
czgirb@ubuntu:~$ 
```

---

### Post by mc4man on 2016-05-24
No clue really, maybe try with a -vv option, ie - 
```
cvlc -vv  jellyfish-3-mbps-hd-hevc.mkv
```

---

### Post by czgirb on 2016-05-24
> **mc4man said:**
> No clue really, maybe try with a -vv option, ie - 
```
cvlc -vv  jellyfish-3-mbps-hd-hevc.mkv
```

as requested

```

czgirb@ubuntu:~$ cvlc -vv  jellyfish-3-mbps-hd-hevc.mkv
VLC media player 2.2.1 Terry Pratchett (Weatherwax) (revision 2.2.1~trusty2)
[0978e910] core libvlc debug: VLC media player - 2.2.1 Terry Pratchett (Weatherwax)
[0978e910] core libvlc debug: Copyright © 1996-2015 the VideoLAN team
[0978e910] core libvlc debug: revision 2.2.1~trusty2
[0978e910] core libvlc debug: configured with ./configure  '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--localstatedir=/var' '--libdir=${prefix}/lib/i386-linux-gnu' '--libexecdir=${prefix}/lib/i386-linux-gnu' '--disable-dependency-tracking' '--build=i686-linux-gnu' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--libdir=/usr/lib' '--sysconfdir=/etc' '--with-binary-version=' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-chromaprint' '--enable-dbus' '--enable-dca' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fdkaac' '--enable-fluidsynth' '--enable-freerdp' '--enable-freetype' '--enable-fribidi' '--enable-gles1' '--enable-gles2' '--enable-glx' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libmpeg2' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-pulse' '--enable-qt' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-sftp' '--enable-shine' '--enable-shout' '--enable-skins2' '--enable-smbclient' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcdx' '--enable-vorbis' '--enable-vpx' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-decklink' '--disable-dxva2' '--disable-gnomevfs' '--disable-goom' '--disable-libtar' '--disable-mfx' '--disable-opencv' '--disable-projectm' '--disable-sndio' '--disable-svgdec' '--disable-telx' '--disable-vsxu' '--disable-wasapi' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv1394' '--enable-linsys' '--enable-omxil' '--enable-udev' '--enable-oss' '--enable-vcd' '--enable-libva' '--enable-v4l2' '--enable-crystalhd' '--enable-mmx' '--enable-sse' '--disable-neon' '--disable-altivec' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'build_alias=i686-linux-gnu'
[0978e910] core libvlc debug: searching plug-in modules
[0978e910] core libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0978e910] core libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0978e910] core libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0978e910] core libvlc debug: plug-ins loaded: 461 modules
[0978e910] core libvlc debug: opening config file (/home/czgirb/.config/vlc/vlcrc)
[0978e910] core libvlc debug: translation test: code is "C"
[0978e910] core libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 FPU 
[09834da0] core input debug: Creating an input for 'Media Library'
[09834da0] core input debug: Input is a meta file: disabling unneeded options
[09834da0] core input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[09834da0] core input debug: `file/xspf-open:///home/czgirb/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/czgirb/.local/share/vlc/ml.xspf'
[09834da0] core input debug: creating demux: access='file' demux='xspf-open' location='/home/czgirb/.local/share/vlc/ml.xspf' file='/home/czgirb/.local/share/vlc/ml.xspf'
[0981d380] core demux debug: looking for access_demux module matching "file": 21 candidates
[0981d380] core demux debug: no access_demux modules matched
[09834da0] core input debug: creating access 'file' location='/home/czgirb/.local/share/vlc/ml.xspf', path='/home/czgirb/.local/share/vlc/ml.xspf'
[0981d380] core access debug: looking for access module matching "file": 25 candidates
[0981d380] filesystem access debug: opening file `/home/czgirb/.local/share/vlc/ml.xspf'
[0981d380] core access debug: using access module "filesystem"
[0981fbc8] core stream debug: Using stream method for AStream*
[0981fbc8] core stream debug: starting pre-buffering
[0981fbc8] core stream debug: received first data after 0 ms
[0981fbc8] core stream debug: pre-buffering done 296 bytes in 0s - 7812 KiB/s
[09820368] core stream debug: looking for stream_filter module matching "any": 9 candidates
[09820368] core stream debug: no stream_filter modules matched
[09820368] core stream debug: looking for stream_filter module matching "record": 9 candidates
[09820368] core stream debug: using stream_filter module "record"
[09834da0] core input debug: creating demux: access='file' demux='xspf-open' location='/home/czgirb/.local/share/vlc/ml.xspf' file='/home/czgirb/.local/share/vlc/ml.xspf'
[098233b8] core demux debug: looking for demux module matching "xspf-open": 67 candidates
[098233b8] xspf demux debug: using XSPF playlist reader
[098233b8] core demux debug: using demux module "playlist"
[098238e0] core demux meta debug: looking for meta reader module matching "any": 2 candidates
[098238e0] lua demux meta debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/reader
[098238e0] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[098238e0] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[098238e0] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[098238e0] core demux meta debug: no meta reader modules matched
[09834da0] core input debug: `file/xspf-open:///home/czgirb/.local/share/vlc/ml.xspf' successfully opened
[09826180] core xml reader debug: looking for xml reader module matching "any": 1 candidates
[09826180] core xml reader debug: using xml reader module "xml"
[098233b8] xspf demux debug: parsed 0 tracks successfully
[09834da0] core input debug: EOF reached
[098233b8] core demux debug: removing module "playlist"
[09820368] core stream debug: removing module "record"
[0981d380] core access debug: removing module "filesystem"
[0979e520] core playlist debug: creating audio output
[09829600] core audio output debug: looking for audio output module matching "any": 7 candidates
[09829600] pulse audio output debug: using library version 4.0.0
[09829600] pulse audio output debug:  (compiled with version 4.0.0, protocol 28)
[09829600] pulse audio output debug: connected locally to unix:/run/user/1000/pulse/native as client #36
[09829600] pulse audio output debug: using protocol 28, server protocol 28
[09829600] pulse audio output debug: adding sink 0: alsa_output.pci-0000_00_1b.0.analog-stereo (Built-in Audio Analog Stereo)
[09829600] core audio output debug: using audio output module "pulse"
[0979e520] core playlist debug: keeping audio output
[0979e520] core playlist debug: adding item `jellyfish-3-mbps-hd-hevc.mkv' ( file:///home/czgirb/jellyfish-3-mbps-hd-hevc.mkv )
[b19004d8] core input debug: Creating an input for 'jellyfish-3-mbps-hd-hevc.mkv'
[09836738] core interface debug: looking for interface module matching "hotkeys,none": 19 candidates
[09836738] core interface debug: using interface module "hotkeys"
[09836d50] core interface debug: looking for interface module matching "globalhotkeys,none": 19 candidates
[09836d50] core interface debug: using interface module "xcb_hotkeys"
[09837718] core interface debug: looking for interface module matching "dbus,none": 19 candidates
[09837718] dbus interface debug: listening on dbus as: org.mpris.MediaPlayer2.vlc
[09837718] core interface debug: using interface module "dbus"
[0983a5c0] core interface debug: looking for interface module matching "dummy": 19 candidates
[09837718] dbus interface debug: Getting All properties
[0983a5c0] dummy interface: using the dummy interface module...
[0983a5c0] core interface debug: using interface module "dummy"
[0979e520] core playlist debug: processing request item: null, node: Playlist, skip: 0
[0979e520] core playlist debug: rebuilding array of current - root Playlist
[0979e520] core playlist debug: rebuild done - 1 items, index -1
[0979e520] core playlist debug: starting playback of the new playlist item
[0979e520] core playlist debug: resyncing on jellyfish-3-mbps-hd-hevc.mkv
[0979e520] core playlist debug: jellyfish-3-mbps-hd-hevc.mkv is at 0
[0979e520] core playlist debug: creating new input thread
[0983b130] core input debug: Creating an input for 'jellyfish-3-mbps-hd-hevc.mkv'
[0979e520] core playlist debug: requesting art for jellyfish-3-mbps-hd-hevc.mkv
[0983b130] core input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0983b130] core input debug: `file:///home/czgirb/jellyfish-3-mbps-hd-hevc.mkv' gives access `file' demux `' path `/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv'
[0983b130] core input debug: specified demux `any'
[0983b130] core input debug: creating demux: access='file' demux='any' location='/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv' file='/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv'
[b0b00830] core demux debug: looking for access_demux module matching "file": 21 candidates
[b0b00830] core demux debug: no access_demux modules matched
[0983b130] core input debug: creating access 'file' location='/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv', path='/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv'
[b0b00830] core access debug: looking for access module matching "file": 25 candidates
[b0b00830] filesystem access debug: opening file `/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv'
[b0b00830] core access debug: using access module "filesystem"
[b0b00bb8] core stream debug: Using stream method for AStream*
[b0b00bb8] core stream debug: starting pre-buffering
[b0b00bb8] core stream debug: received first data after 0 ms
[b0b00bb8] core stream debug: pre-buffering done 1024 bytes in 0s - 52631 KiB/s
[b0b00d58] core stream debug: looking for stream_filter module matching "any": 9 candidates
[b0b00d58] core stream debug: no stream_filter modules matched
[b0b00d58] core stream debug: looking for stream_filter module matching "record": 9 candidates
[b0b00d58] core stream debug: using stream_filter module "record"
[0983b130] core input debug: creating demux: access='file' demux='any' location='/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv' file='/home/czgirb/jellyfish-3-mbps-hd-hevc.mkv'
[b0b00e58] core demux debug: looking for demux module matching "mkv": 67 candidates
[b1904930] core art finder debug: looking for meta fetcher module matching "any": 1 candidates
[b1904930] lua art finder debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/fetcher
[b1904930] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[b1904930] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[b1904930] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[b1904930] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
[b1904930] core art finder debug: no meta fetcher modules matched
[0978e910] core libvlc debug: searching art for jellyfish-3-mbps-hd-hevc.mkv
[b1904930] core art finder debug: looking for art finder module matching "any": 2 candidates
[09837718] dbus interface debug: Getting All properties
[b0b00e58] mkv demux debug: |   + Seek head
[b0b00e58] mkv demux debug: |   |   + Seek
[b0b00e58] mkv demux debug: |   - info at 282
[b0b00e58] mkv demux debug: |   + Information
[b0b00e58] mkv demux debug: |   |   + TimecodeScale=1000000
[b0b00e58] mkv demux debug: |   |   + Muxing Application=Lavf56.3.100
[b0b00e58] mkv demux debug: |   |   + Writing Application=Lavf56.3.100
[b0b00e58] mkv demux debug: |   |   + UID=511719606
[b0b00e58] mkv demux debug: |   |   + Duration=30097
[b0b00e58] mkv demux debug: |   |   + Seek
[b0b00e58] mkv demux debug: |   - tracks at 361
[b0b00e58] mkv demux debug: |   + Tracks
[b0b00e58] mkv demux debug: |   |   + Track Entry
[b0b00e58] mkv demux debug: |   |   |   + Track Number=1
[b0b00e58] mkv demux debug: |   |   |   + Track UID=1
[b0b00e58] mkv demux debug: |   |   |   + Track Lacing=0
[b0b00e58] mkv demux debug: |   |   |   + Track Language=`und'
[b0b00e58] mkv demux debug: |   |   |   + Track CodecId=V_MPEGH/ISO/HEVC
[b0b00e58] mkv demux debug: |   |   |   + Track Type=video
[b0b00e58] mkv demux debug: |   |   |   + Track Default Duration=33366700
[b0b00e58] mkv demux debug: |   |   |   + Track Video
[b0b00e58] mkv demux debug: |   |   |   |   + width=1920
[b0b00e58] mkv demux debug: |   |   |   |   + height=1080
[b0b00e58] mkv demux debug: |   |   |   + Track CodecPrivate size=110
[b0b00e58] mkv demux debug: |   |   + Seek
[b0b00e58] mkv demux debug: |   - tags at 558
[b0b00e58] mkv demux debug: |   + Tags
[b0b00e58] mkv demux debug: + Tag
[b0b00e58] mkv demux debug: |   + Targets
[b0b00e58] mkv demux debug: |   + Simple Tag 
[b0b00e58] mkv demux debug: |   |   + Meta MAJOR_BRAND: iso4
[b0b00e58] mkv demux debug: |   + Simple Tag 
[b0b00e58] mkv demux debug: |   |   + Meta MINOR_VERSION: 1
[b0b00e58] mkv demux debug: |   + Simple Tag 
[b0b00e58] mkv demux debug: |   |   + Meta COMPATIBLE_BRANDS: iso4hvc1iso6
[b0b00e58] mkv demux debug: |   + Simple Tag 
[b0b00e58] mkv demux debug: |   |   + Meta ENCODER: Lavf56.3.100
[b0b00e58] mkv demux debug: + Tag
[b0b00e58] mkv demux debug: |   + Targets
[b0b00e58] mkv demux debug: |   |   + TrackUID: 1
[b0b00e58] mkv demux debug: |   + Simple Tag 
[b0b00e58] mkv demux debug: |   |   + Meta CREATION_TIME: 2016-02-04 02:54:49
[b0b00e58] mkv demux debug: |   + Simple Tag 
[b0b00e58] mkv demux debug: |   |   + Meta LANGUAGE: und
[b0b00e58] mkv demux debug: |   + Simple Tag 
[b0b00e58] mkv demux debug: |   |   + Meta HANDLER_NAME: hevc@GPAC0.5.2-DEV-rev565-g71748d7-ab-suite
[b0b00e58] mkv demux debug: loading tags done.
[b0b00e58] mkv demux debug: |   |   + Seek
[b0b00e58] mkv demux debug: |   |   + Unknown (N7libebml8EbmlVoidE)
[b0b00e58] mkv demux debug: |   - cues at 10638884
[b0b00e58] mkv demux debug: |   + Cues
[b0b00e58] mkv demux warning: MKV/Ebml Parser: m_el[mi_level] == NULL

[b0b00e58] mkv demux warning: MKV/Ebml Parser: Up cannot escape itself
[b0b00e58] mkv demux debug: |   - loading cues done.
[b0b00e58] mkv demux debug: |   + Void
[b0b00e58] mkv demux debug: |   + Information
[b0b00e58] mkv demux debug: |   + Tracks
[b0b00e58] mkv demux debug: |   + Preload Unknown (N11libmatroska7KaxTagsE)
[b0b00e58] mkv demux debug: |   + Cluster
[b0b00e58] mkv demux debug: found 1 es
[0983b130] core input debug: selecting program id=0
[0983b130] core input debug: Buffering 0%
[b0b00e58] mkv demux debug: Starting the UI Hook
[b0b00e58] core demux debug: using demux module "mkv"
[0983b130] core input debug: looking for a subtitle file in /home/czgirb/
[afc004c0] core decoder debug: looking for decoder module matching "any": 45 candidates
[b1904930] lua art finder debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/art
[b1904930] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[b1904930] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[b1904930] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[b1904930] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[b1904930] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[b1904930] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[b1904930] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[b1904930] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[b1904930] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[b1904930] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[b1904930] core art finder debug: no art finder modules matched
[b1904930] core art finder debug: looking for meta fetcher module matching "any": 1 candidates
[b1904930] lua art finder debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/fetcher
[b1904930] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[b1904930] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[b1904930] core art finder debug: using meta fetcher module "lua"
[b1904930] core art finder debug: removing module "lua"
[0978e910] core libvlc debug: searching art for jellyfish-3-mbps-hd-hevc.mkv
[b19067e8] core art finder debug: looking for art finder module matching "any": 2 candidates
[b19067e8] lua art finder debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/art
[b19067e8] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[b19067e8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[b19067e8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[b19067e8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[b19067e8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[b19067e8] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[b19067e8] core art finder debug: no art finder modules matched
[0978e910] core libvlc debug: art not found for jellyfish-3-mbps-hd-hevc.mkv
[0979e520] core playlist debug: meta ok for (null), need to fetch art
[b19080e8] core art finder debug: looking for meta fetcher module matching "any": 1 candidates
[b19080e8] lua art finder debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/fetcher
[b19080e8] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[b19080e8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[b19080e8] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[b19080e8] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
[b19080e8] core art finder debug: no meta fetcher modules matched
[0979e520] core playlist debug: searching art for jellyfish-3-mbps-hd-hevc.mkv
[b1902fe8] core art finder debug: looking for art finder module matching "any": 2 candidates
[b1902fe8] lua art finder debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/art
[b1902fe8] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[b1902fe8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[b1902fe8] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[b1902fe8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[b1902fe8] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[b1902fe8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[b1902fe8] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[b1902fe8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[b1902fe8] lua art finder debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[b1902fe8] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[b1902fe8] core art finder debug: no art finder modules matched
[b1905f68] core art finder debug: looking for meta fetcher module matching "any": 1 candidates
[b1905f68] lua art finder debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/fetcher
[b1905f68] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[b1905f68] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[b1905f68] core art finder debug: using meta fetcher module "lua"
[b1905f68] core art finder debug: removing module "lua"
[0979e520] core playlist debug: searching art for jellyfish-3-mbps-hd-hevc.mkv
[b1902130] core art finder debug: looking for art finder module matching "any": 2 candidates
[b1902130] lua art finder debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/art
[b1902130] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[b1902130] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[b1902130] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[b1902130] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[b1902130] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[b1902130] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[b1902130] core art finder debug: no art finder modules matched
[0979e520] core playlist debug: art not found for jellyfish-3-mbps-hd-hevc.mkv
[afc004c0] de265 decoder debug: using libde265 version 1.0.2
[afc004c0] de265 decoder debug: Started 4 worker threads
[afc004c0] core decoder debug: using decoder module "de265"
[afc77968] core demux meta debug: looking for meta reader module matching "any": 2 candidates
[afc77968] lua demux meta debug: Trying Lua scripts in /home/czgirb/.local/share/vlc/lua/meta/reader
[afc77968] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[afc77968] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[afc77968] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[afc77968] core demux meta debug: no meta reader modules matched
[0983b130] core input debug: `file:///home/czgirb/jellyfish-3-mbps-hd-hevc.mkv' successfully opened
[afc004c0] de265 decoder warning: Unsupported extra data version 1, decoding may fail
[afc004c0] de265 decoder debug: Assuming packetized data (4 bytes length)
[0983b130] core input debug: Buffering 0%
[0983b130] Segmentation fault (core dumped)
czgirb@ubuntu:~$ 

```

---

### Post by czgirb on 2016-05-25
it's just a silly/dumb opinion
how about if we **uninstall it & all related component (incld all the ppa)** > **clean it all** > **restart the system** > and do a **fresh install** ???
if it's agreed ... please guide me how to do that
**thank you**

---

### Post by mc4man on 2016-05-25
> **czgirb said:**
> it's just a silly/dumb opinion
how about if we **uninstall it & all related component (incld all the ppa)** > **clean it all** > **restart the system** > and do a **fresh install** ???
if it's agreed ... please guide me how to do that
**thank you**
You could try that. i'd suggest doing like - 
```
sudo apt-get purge vlc-data vlc-plugin-libde265
```
```
sudo apt-get install ppa-purge
```
```
sudo ppa-purge ppa:mc3man/trusty-media
```
(- ppa-purge may report not being able to replace some packages, no worry,  just let it proceed

when above is done
```
sudo apt-get update
```
```
sudo apt-get install vlc
```
run vlc on any not hevc file to make sure it works, then install the plugin from the _strukturag ppa_

---

### Post by czgirb on 2016-05-25
strukturag ppa??? what it means?

---

### Post by mc4man on 2016-05-25
> **czgirb said:**
> strukturag ppa??? what it means?
The ppa you wrote about in post 1

---

### Post by Yellow Pasque on 2016-05-26
```
de265 decoder warning: Unsupported extra data version 1, decoding may fail
```

Something may be wrong with the file you're attempting to play. I would try a different one to rule out that possibility.

---

### Post by mc4man on 2016-05-26
I think it's crashing just about  when it would be setting hw decoding or a video out. If you still have 2.2 installed then open vlc > tools > preferences > Input/Codecs & disable hw decoding. Also in the Video tab set the output to something appropriate for your hardware.
At least in vlc 2.2 it sets both of these to automatic & vlc is self admittedly too stupid to pick the correct ones in many cases.
(- from my perspective vlc has become a reasonably useless app except on Windows 10

---

