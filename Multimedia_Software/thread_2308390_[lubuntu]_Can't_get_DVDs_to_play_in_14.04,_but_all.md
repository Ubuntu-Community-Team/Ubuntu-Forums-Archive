---
title: "[lubuntu] Can't get DVDs to play in 14.04, but all lib files installed - any ideas?"
date: 2016-01-02
forum: Multimedia Software
---

### Post by mark260 on 2016-01-02
Hi folks

I recently installed Lubuntu 14.04 on a Powerbook G4. I've managed to solve almost all the hardware problems barring it's ability to play DVDs. I've scoured the net for answers and done almost everything I can find, but still to no avail. Can anyone help me?

- I have successfully installed livdvdread4, libdvdnav4, and libdvdcss2 (compiled for powerpc and installed separately, as the sudo /usr/ ... install-css.sh command doesn't work) - all these packages show as installed in synaptic.
- I have also checked and the drive is a MATSHITA, set to region 2 (EU, UK, JP, etc), which all my DVDs match.
- The computer recognises the device (/dev/cdrom and as /dev/sr0), and any media player I choose will recognise whatever is in the drive, can browse the files etc, but cannot play anything.
- VLC will mount the DVD and even report the correct length of the film, but will not play or show images.
- I have tested the drive with an audio CD that works fine.

Can anyone tell me what the heck is going on, as I've been at this on and off for a month with no success.

Thanks in advance,

Mark

---

### Post by Dreamer Fithp Apprentice on 2016-01-02
> **mark260 said:**
> - The computer recognises the device (/dev/cdrom and as /dev/sr0), and any media player I choose will recognise whatever is in the drive, can browse the files etc, but cannot play anything.So it isn't just commercial style DVDs that won't play? Just to be absolutely clear, you've tried data DVDs with video files on them, and they won't play, right?

If that is the case, then, not for a solution, but for a step in troubleshooting, I'd try copying the files to a hard drive and seeing if they will play from there.

---

### Post by mark260 on 2016-01-02
Thanks for the reply.

Same result. If I copy just one of the VOB files I can get extremely distorted but real-time audio of that particular scene, but no video (specifically within MPlayer). Same with playing straight from the DVD one of such files.

I assume this means the codecs aren't functioning correctly?

---

### Post by mark260 on 2016-01-02
> **Dreamer Fithp Apprentice said:**
> So it isn't just commercial style DVDs that won't play? Just to be absolutely clear, you've tried data DVDs with video files on them, and they won't play, right?

If that is the case, then, not for a solution, but for a step in troubleshooting, I'd try copying the files to a hard drive and seeing if they will play from there.

Thanks for the extra clarification.

I have NOT tested with data DVDs with video on them. As the primary purpose of fixing this laptop was to be an entertainment system, if I can't get commercial DVDs to work then I'll give up on that aspect.

---

### Post by Dreamer Fithp Apprentice on 2016-01-02
So, it sounds like it is at least partially, maybe entirely, a codec-and/or-viewer issue. First, I'd try installing VLC.```
sudo apt-get install --install-suggests vlc
```That might even be sufficient. If not, we'll at least be following in Edison's footsteps.

---

### Post by mc4man on 2016-01-03
Try what's described here inc. deleting that folder (.dvdcss) first.
[http://ubuntuforums.org/showthread.php?t=1195303&p=7505980&viewfull=1#post7505980](http://ubuntuforums.org/showthread.php?t=1195303&p=7505980&viewfull=1#post7505980)

---

### Post by mark260 on 2016-01-03
Hey mc4man, thanks for the response and detailed instructions.

Here's the output from that file. I'm not confident I know what this implies though!

```
[0x106eb910] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.1
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: disc reports copyright information 0x1
libdvdcss debug: drive region mask 0xfd, RPC-II, region code set
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key af:d1:b3:14:96
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 81:70:58:99:76
libdvdcss debug: using CSS key cache dir: /home/markjwgraham/.dvdcss/SKYFALL-2012122012421500-8170589976/
libdvdnav: DVD Title: SKYFALL
libdvdnav: DVD Serial Number: 41946A87
libdvdnav: DVD Title (Alternative): SKYFALL
libdvdnav: Unable to find map file '/home/markjwgraham/.dvdnav/SKYFALL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00022bb0
libdvdcss debug: getting title key at block 142256 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00023515
libdvdcss debug: getting title key at block 144661 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key c4:b6:fa:03:7a
libdvdcss debug: title key is c4:b6:fa:03:7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000235fb
libdvdcss debug: getting title key at block 144891 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key c7:f5:0c:db:02
libdvdcss debug: title key is c7:f5:0c:db:02
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0002f4f6
libdvdcss debug: getting title key at block 193782 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key ca:ac:91:86:9b
libdvdcss debug: title key is ca:ac:91:86:9b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0003118a
libdvdcss debug: getting title key at block 201098 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key c0:d7:c3:51:18
libdvdcss debug: title key is c0:d7:c3:51:18
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0003300a
libdvdcss debug: getting title key at block 208906 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key d1:79:0f:f6:06
libdvdcss debug: title key is d1:79:0f:f6:06
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0003c6a6
libdvdcss debug: getting title key at block 247462 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key d1:79:0f:f6:06
libdvdcss debug: title key is d1:79:0f:f6:06
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c190f
libdvdcss debug: getting title key at block 3938575 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key c1:0b:2b:40:aa
libdvdcss debug: title key is c1:0b:2b:40:aa
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 1
[0x107b9670] main input error: ES_OUT_RESET_PCR called
[0x107b9670] main input error: ES_OUT_RESET_PCR called
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns -1
libva error: va_getDriverName() failed with unknown libva error,driver_name=(null)
[0x107108d8] vaapi generic error: Failed to initialize the VAAPI device
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0xb304b508] xcb_xv vout display error: no available XVideo adaptor
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"


```

And in case it's helpful... output from sudo lshw -C disk

```

  *-cdrom
       description: DVD reader
       product: CD-RW  CW-8123
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       logical name: /media/markjwgraham/SKYFALL
       version: CA0T
       serial: [
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/markjwgraham/SKYFALL
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted


```

And from regionset /dev/sr0

```

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD

```

---

### Post by mark260 on 2016-01-03
And the output from vlc -vv command:

```

VLC media player 2.1.6 Rincewind (revision 2.1.6-0-gea01d28)
[0x1042a910] main libvlc debug: VLC media player - 2.1.6 Rincewind
[0x1042a910] main libvlc debug: Copyright © 1996-2015 the VideoLAN team
[0x1042a910] main libvlc debug: revision 2.1.6-0-gea01d28
[0x1042a910] main libvlc debug: configured with ./configure  '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--localstatedir=/var' '--libdir=${prefix}/lib/powerpc-linux-gnu' '--libexecdir=${prefix}/lib/powerpc-linux-gnu' '--disable-dependency-tracking' '--build=powerpc-linux-gnu' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--libdir=/usr/lib' '--sysconfdir=/etc' '--with-binary-version=0ubuntu14.04.1' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-chromaprint' '--enable-dbus' '--enable-dca' '--enable-dirac' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libfreerdp' '--enable-libmpeg2' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-oss' '--enable-pulse' '--enable-qt' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-sftp' '--enable-shout' '--enable-skins2' '--enable-smbclient' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-decklink' '--disable-dxva2' '--disable-fdkaac' '--disable-gnomevfs' '--disable-goom' '--disable-libvnc' '--disable-opencv' '--disable-projectm' '--disable-quicksync' '--disable-sndio' '--disable-telx' '--disable-vsxu' '--disable-wasapi' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv1394' '--enable-linsys' '--enable-omxil' '--enable-udev' '--enable-libva' '--enable-v4l2' '--disable-crystalhd' '--disable-mmx' '--disable-sse' '--disable-neon' '--enable-altivec' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'build_alias=powerpc-linux-gnu'
[0x1042a910] main libvlc debug: searching plug-in modules
[0x1042a910] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x1042a910] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x1042a910] main libvlc warning: cannot load module `/usr/lib/vlc/plugins/video_filter/libpostproc_plugin.so' (/usr/lib/libpostproc.so.52: R_PPC_REL24 relocation at 0x0d16d1c4 for symbol `memcpy' out of range)
[0x1042a910] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x1042a910] main libvlc debug: plug-ins loaded: 419 modules
[0x1042a910] main libvlc debug: opening config file (/home/markjwgraham/.config/vlc/vlcrc)
[0x1042a910] main libvlc debug: translation test: code is "C"
[0x1042a910] main libvlc debug: CPU has capabilities FPU 
[0x104c5458] main input debug: Creating an input for 'Media Library'
[0x104c5458] main input debug: Input is a meta file: disabling unneeded options
[0x104c5458] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x104c5458] main input debug: `file/xspf-open:///home/markjwgraham/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x104c5458] main input debug: creating demux: access='file' demux='xspf-open' location='/home/markjwgraham/.local/share/vlc/ml.xspf' file='/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x1043bfa8] main demux debug: looking for access_demux module matching "file": 20 candidates
[0x1043bfa8] main demux debug: no access_demux modules matched
[0x104c5458] main input debug: creating access 'file' location='/home/markjwgraham/.local/share/vlc/ml.xspf', path='/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x104c5d28] main access debug: looking for access module matching "file": 25 candidates
[0x104c5d28] filesystem access debug: opening file `/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x104c5d28] main access debug: using access module "filesystem"
[0x104c6b90] main stream debug: Using stream method for AStream*
[0x104c6b90] main stream debug: starting pre-buffering
[0x104c6b90] main stream debug: received first data after 25 ms
[0x104c6b90] main stream debug: pre-buffering done 296 bytes in 0s - 11 KiB/s
[0x104c6518] main stream debug: looking for stream_filter module matching "any": 9 candidates
[0x104c6518] main stream debug: no stream_filter modules matched
[0x104c6518] main stream debug: looking for stream_filter module matching "record": 9 candidates
[0x104c6518] main stream debug: using stream_filter module "record"
[0x104c5458] main input debug: creating demux: access='file' demux='xspf-open' location='/home/markjwgraham/.local/share/vlc/ml.xspf' file='/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x104c7960] main demux debug: looking for demux module matching "xspf-open": 63 candidates
[0x104c7960] playlist demux debug: using XSPF playlist reader
[0x104c7960] main demux debug: using demux module "playlist"
[0x104c7af8] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x104c7af8] lua demux meta debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/meta/reader
[0x104c7af8] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x104c7af8] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x104c7af8] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x104c7af8] main demux meta debug: no meta reader modules matched
[0x104c5458] main input debug: `file/xspf-open:///home/markjwgraham/.local/share/vlc/ml.xspf' successfully opened
[0x104bdb98] main xml reader debug: looking for xml reader module matching "any": 1 candidates
[0x104bdb98] main xml reader debug: using xml reader module "xml"
[0x104c7960] playlist demux debug: parsed 0 tracks successfully
[0x104c5458] main input debug: EOF reached
[0x104c7960] main demux debug: removing module "playlist"
[0x104c6518] main stream debug: removing module "record"
[0x104c5d28] main access debug: removing module "filesystem"
[0x1043ab08] main playlist debug: creating audio output
[0x104bd080] main audio output debug: looking for audio output module matching "any": 6 candidates
[0x104bd080] pulse audio output debug: using library version 4.0.0
[0x104bd080] pulse audio output debug:  (compiled with version 4.0.0, protocol 28)
[0x104bd080] pulse audio output debug: connected locally to unix:/run/user/1000/pulse/native as client #8
[0x104bd080] pulse audio output debug: using protocol 28, server protocol 28
[0x104bd080] main audio output debug: using audio output module "pulse"
[0x1043ab08] main playlist debug: keeping audio output
[0x1058d9c8] main interface debug: looking for interface module matching "hotkeys,none": 19 candidates
[0x1058d9c8] main interface debug: using interface module "hotkeys"
[0x104b5988] main interface debug: looking for interface module matching "globalhotkeys,none": 19 candidates
[0x104b5988] main interface debug: using interface module "globalhotkeys"
[0x104bd080] pulse audio output debug: adding sink 0: alsa_output.pci-0001_10_17.0.analog-stereo (KeyLargo/Intrepid Mac I/O Analog Stereo)
[0x104bd588] main interface debug: looking for interface module matching "dbus,none": 19 candidates
[0x104bd588] dbus interface debug: listening on dbus as: org.mpris.MediaPlayer2.vlc.instance2683
[0x104bd588] main interface debug: using interface module "dbus"
[0x1042a910] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x104bed28] main interface debug: looking for interface module matching "any": 19 candidates
[0xb2f9d0d0] main generic debug: looking for extension module matching "any": 1 candidates
[0xb2f9d0d0] lua generic debug: Opening Lua Extension module
[0xb2f9d0d0] lua generic debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/extensions
[0xb2f9d0d0] lua generic debug: Trying Lua scripts in /usr/lib/vlc/lua/extensions
[0xb2f9d0d0] lua generic debug: Trying Lua playlist script /usr/lib/vlc/lua/extensions/VLSub.luac
[0xb2f9d0d0] lua generic debug: Scanning Lua script /usr/lib/vlc/lua/extensions/VLSub.luac
[0xb2f9d0d0] lua generic debug: Script /usr/lib/vlc/lua/extensions/VLSub.luac has the following capability flags: 0x5
[0xb2f9d0d0] lua generic debug: Trying Lua scripts in /usr/share/vlc/lua/extensions
[0xb2f9d0d0] main generic debug: using extension module "lua"
[0x104bed28] main interface debug: using interface module "qt4"
[0x1043ab08] main playlist debug: adding item `sr0' ( dvdsimple:///dev/sr0 )
[0x104bed28] qt4 interface debug: Adding a new MRL to recent ones: dvdsimple:///dev/sr0
[0x1043ab08] main playlist debug: processing request item: sr0, node: null, skip: 0
[0x1043ab08] main playlist debug: rebuilding array of current - root Playlist
[0x1043ab08] main playlist debug: rebuild done - 1 items, index 0
[0x1043ab08] main playlist debug: starting playback of the new playlist item
[0x1043ab08] main playlist debug: resyncing on sr0
[0x1043ab08] main playlist debug: sr0 is at 0
[0x1043ab08] main playlist debug: creating new input thread
[0x104f8710] main input debug: Creating an input for 'sr0'
[0xb28838a0] main input debug: Creating an input for 'sr0'
[0x104f8710] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x104f8710] main input debug: `dvdsimple:///dev/sr0' gives access `dvdsimple' demux `' path `/dev/sr0'
[0x1043ab08] main playlist debug: meta ok for (null), need to fetch art
[0x104f8710] main input debug: creating demux: access='dvdsimple' demux='' location='/dev/sr0' file='/dev/sr0'
[0x104c2440] main demux debug: looking for access_demux module matching "dvdsimple": 20 candidates
[0xb289e0a8] main demux meta debug: looking for meta fetcher module matching "any": 1 candidates
[0x104bed28] qt4 interface debug: IM: Setting an input
[0xb289e0a8] lua demux meta debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/meta/fetcher
[0xb289e0a8] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[0xb289e0a8] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[0xb289e0a8] main demux meta debug: using meta fetcher module "lua"
[0xb289e0a8] main demux meta debug: removing module "lua"
[0x1043ab08] main playlist debug: searching art for sr0
[0xb289d878] main art finder debug: looking for art finder module matching "any": 2 candidates
[0xb289d878] lua art finder debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/meta/art
[0xb289d878] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[0xb289d878] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[0xb289d878] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[0xb289d878] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[0xb289d878] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[0xb289d878] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[0xb289d878] main art finder debug: no art finder modules matched
[0x1043ab08] main playlist debug: art not found for sr0
[0x104c2440] dvdread demux debug: VMG opened
[0x104c2440] dvdread demux debug: number of titles: 14
[0x104c2440] dvdread demux debug: title 0 has 33 chapters
[0x104c2440] dvdread demux debug: title 1 has 5 chapters
[0x104c2440] dvdread demux debug: title 2 has 2 chapters
[0x104c2440] dvdread demux debug: title 3 has 2 chapters
[0x104c2440] dvdread demux debug: title 4 has 2 chapters
[0x104c2440] dvdread demux debug: title 5 has 2 chapters
[0x104c2440] dvdread demux debug: title 6 has 2 chapters
[0x104c2440] dvdread demux debug: title 7 has 2 chapters
[0x104c2440] dvdread demux debug: title 8 has 2 chapters
[0x104c2440] dvdread demux debug: title 9 has 2 chapters
[0x104c2440] dvdread demux debug: title 10 has 2 chapters
[0x104c2440] dvdread demux debug: title 11 has 2 chapters
[0x104c2440] dvdread demux debug: title 12 has 1 chapters
[0x104c2440] dvdread demux debug: title 13 has 1 chapters
[0x104c2440] dvdread demux debug: open VTS 5, for title 1
[0x104c2440] dvdread demux debug: title 1 vts_title 1 pgc 1 pgn 1 start 0 end 3691043 blocks: 3691044

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00022bb0
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00023515
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000235fb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0002f4f6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0003118a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0003300a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0003c6a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c190f
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 1
[0x104f8710] main input error: ES_OUT_RESET_PCR called
[0x104f8710] main input debug: selecting program id=0
[0x104c2440] dvdread demux debug: audio position  0
[0x104c2440] dvdread demux debug: audio position  1
[0x104c2440] dvdread demux debug: audio position  2
[0x104c2440] dvdread demux debug: audio position  3
[0x104c2440] dvdread demux debug: audio position  4
[0x104c2440] dvdread demux debug: audio position  5
[0x104c2440] dvdread demux debug: spu 1 0x80000000
[0x104c2440] dvdread demux debug: spu 2 0x80010100
[0x104c2440] dvdread demux debug: spu 3 0x80020200
[0x104c2440] dvdread demux debug: spu 4 0x80030300
[0x104c2440] dvdread demux debug: spu 5 0x80040400
[0x104c2440] dvdread demux debug: spu 6 0x80050500
[0x104c2440] dvdread demux debug: spu 7 0x80060600
[0x104c2440] dvdread demux debug: spu 8 0x80070700
[0x104c2440] dvdread demux debug: spu 9 0x80080800
[0x104c2440] dvdread demux debug: spu 10 0x80090900
[0x104c2440] dvdread demux debug: spu 11 0x800a0a00
[0x104c2440] dvdread demux debug: spu 12 0x800b0b00
[0x104c2440] dvdread demux debug: spu 13 0x800c0c00
[0x104c2440] dvdread demux debug: spu 14 0x800d0d00
[0x104c2440] dvdread demux debug: spu 15 0x800e0e00
[0x104c2440] dvdread demux debug: spu 16 0x800f0f00
[0x104c2440] dvdread demux debug: spu 17 0x80101000
[0x104c2440] dvdread demux debug: spu 18 0x80111100
[0x104c2440] dvdread demux debug: spu 19 0x80121200
[0x104c2440] main demux debug: using access_demux module "dvdread"
[0x104a95c0] main decoder debug: looking for decoder module matching "any": 38 candidates
[0x104a95c0] avcodec decoder debug: trying to use direct rendering
[0x104a95c0] avcodec decoder debug: allowing 1 thread(s) for decoding
[0x104a95c0] avcodec decoder warning: threaded frame decoding is not compatible with avcodec-hw, disabled
[0x104a95c0] avcodec decoder warning: threaded slice decoding is not compatible with avcodec-hw, disabled
[0x104a95c0] avcodec decoder debug: avcodec codec (MPEG-1/2 Video) started
[0x104a95c0] main decoder debug: using decoder module "avcodec"
[0x10592630] main packetizer debug: looking for packetizer module matching "any": 21 candidates
[0x10592630] main packetizer debug: using packetizer module "packetizer_mpegvideo"
[0x10593db8] main decoder debug: looking for decoder module matching "any": 38 candidates
[0x10593db8] main decoder debug: using decoder module "a52"
[0x105946e0] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x105946e0] lua demux meta debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/meta/reader
[0x105946e0] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x105946e0] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x105946e0] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x105946e0] main demux meta debug: no meta reader modules matched
[0x104f8710] main input debug: `dvdsimple:///dev/sr0' successfully opened
[0x104f8710] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[0x104f8710] main input debug: Buffering 0%
[0x10592630] packetizer_mpegvideo packetizer debug: size 720x576 fps=25.000
[0x104f8710] main input debug: Buffering 0%
[0x104f8710] main input debug: Buffering 1%
[0x104f8710] main input debug: Buffering 1%
[0x104f8710] main input debug: Buffering 2%
[0x104f8710] main input debug: Buffering 2%
[0x104f8710] main input debug: Buffering 3%
[0x104f8710] main input debug: Buffering 3%
[0x104f8710] main input debug: Buffering 4%
[0x104f8710] main input debug: Buffering 4%
[0x104f8710] main input debug: Buffering 5%
[0x104f8710] main input debug: Buffering 5%
[0x104f8710] main input debug: Buffering 6%
[0x104f8710] main input debug: Buffering 7%
[0x104f8710] main input debug: Buffering 7%
[0x104f8710] main input debug: Buffering 8%
[0x104f8710] main input debug: Buffering 8%
[0x104f8710] main input debug: Buffering 9%
[0x104f8710] main input debug: Buffering 9%
[0x104f8710] main input debug: Buffering 10%
[0x104f8710] main input debug: Buffering 10%
[0x104f8710] main input debug: Buffering 11%
[0x104f8710] main input debug: Buffering 11%
[0x104f8710] main input debug: Buffering 12%
[0xb28a8b60] main generic debug: looking for hw decoder module matching "vaapi": 1 candidates
[0x104f8710] main input debug: Buffering 13%
[0x104f8710] main input debug: Buffering 13%
[0x104f8710] main input debug: Buffering 14%
[0x104f8710] main input debug: Buffering 14%
[0x104f8710] main input debug: Buffering 15%
[0x104f8710] main input debug: Buffering 15%
[0x104f8710] main input debug: Buffering 16%
[0x104f8710] main input debug: Buffering 16%
[0x104f8710] main input debug: Buffering 17%
[0x104f8710] main input debug: Buffering 52%
[0x10593db8] a52 decoder debug: A/52 channels:6 samplerate:48000 bitrate:448000
[0x1043ab08] main playlist debug: reusing audio output
[0x104f8710] main input debug: Buffering 55%
[0x104f8710] main input debug: Buffering 57%
[0x104f8710] main input debug: Buffering 59%
[0x104f8710] main input debug: Buffering 61%
[0x104f8710] main input debug: Buffering 64%
[0x104f8710] main input debug: Buffering 66%
[0x104f8710] main input debug: Buffering 68%
[0x104f8710] main input debug: Buffering 71%
[0x104f8710] main input debug: Buffering 72%
[0x104f8710] main input debug: Buffering 73%
[0x104f8710] main input debug: Buffering 75%
[0x104f8710] main input debug: Buffering 77%
[0x104f8710] main input debug: Buffering 86%
[0x104f8710] main input debug: Buffering 87%
[0x104f8710] main input debug: Buffering 87%
[0x104f8710] main input debug: Buffering 88%
[0x104f8710] main input debug: Buffering 89%
[0x104f8710] main input debug: Buffering 91%
[0x104f8710] main input debug: Buffering 97%
[0x104f8710] main input debug: Buffering 98%
[0x104f8710] main input debug: Buffering 98%
[0x104f8710] main input debug: Stream buffering done (301 ms in 63 ms)
libva info: VA-API version 0.35.0
[0x104bd080] pulse audio output debug: using surround-51 channel map
libva info: va_getDriverName() returns -1
libva error: va_getDriverName() failed with unknown libva error,driver_name=(null)
[0xb28a8b60] vaapi generic error: Failed to initialize the VAAPI device
[0xb28a8b60] main generic debug: no hw decoder modules matched
[0xb28e0570] main spu text debug: looking for text renderer module matching "any": 2 candidates
[0xb28e0570] freetype spu text debug: Building font databases.
[0xb28e0570] freetype spu text debug: Took 1 microseconds
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0xb28e0570] freetype spu text debug: Using Serif Bold as font from file /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
[0xb28e0570] freetype spu text debug: using fontsize: 2
[0xb28e0570] main spu text debug: using text renderer module "freetype"
[0xb28e1990] main scale debug: looking for video filter2 module matching "any": 49 candidates
[0xb28e1990] swscale scale debug: 32x32 chroma: YUVA -> 16x16 chroma: RGBA with scaling using Bicubic (good quality)
[0xb28e1990] main scale debug: using video filter2 module "swscale"
[0xb28f8af8] main scale debug: looking for video filter2 module matching "any": 49 candidates
[0xb28f8af8] yuvp scale debug: YUVP to YUVA converter
[0xb28f8af8] main scale debug: using video filter2 module "yuvp"
[0xb28aecd0] main video output debug: Deinterlacing available
[0xb28aecd0] main video output debug: deinterlace -1, mode blend, is_needed 0
[0xb28aecd0] main video output debug: Opening vout display wrapper
[0xb3403440] main vout display debug: looking for vout display module matching "any": 12 candidates
[0xb3404368] main window debug: looking for vout window xid module matching "qt4,any": 4 candidates
[0xb3404368] qt4 window debug: requesting video window...
[0x104bed28] qt4 interface debug: Video was requested 0, 0
[0xb3404368] main window debug: using vout window xid module "qt4"
[0xb34035c0] main inhibit debug: looking for inhibit module matching "any": 2 candidates
[0xb34035c0] dbus_screensaver inhibit debug: cannot find service org.freedesktop.ScreenSaver
[0xb34035c0] dbus_screensaver inhibit debug: cannot find service org.freedesktop.PowerManagement.Inhibit
[0xb34035c0] dbus_screensaver inhibit debug: cannot find service org.mate.SessionManager
[0xb34035c0] dbus_screensaver inhibit debug: cannot find service org.gnome.SessionManager
[0xb34035c0] main inhibit debug: using inhibit module "xdg_screensaver"
[0xb3403440] xcb_xv vout display debug: connected to X11.0 server
[0xb3403440] xcb_xv vout display debug:  vendor : The X.Org Foundation
[0xb3403440] xcb_xv vout display debug:  version: 11501000
[0x104bd080] pulse audio output debug: digital pass-through not available
[0x104bd080] pulse audio output debug: changed buffer metrics: maxlength=4194312, tlength=138240, prebuf=0, minreq=46080
[0x104bd080] pulse audio output debug: connected to sink alsa_output.pci-0001_10_17.0.analog-stereo
[0x104bd080] main audio output debug: output 'f32b' 48000 Hz 3F2R/LFE frame=1 samples/24 bytes
[0xb288f550] main volume debug: looking for audio volume module matching "any": 2 candidates
[0x104bd080] pulse audio output debug: base volume: 65536
[0x104bd080] pulse audio output debug: changing sink 0: alsa_output.pci-0001_10_17.0.analog-stereo (KeyLargo/Intrepid Mac I/O Analog Stereo)
[0xb3403440] xcb_xv vout display debug: using screen 0xe1
[0xb288f550] main volume debug: using audio volume module "float_mixer"
[0x104bd080] main audio output debug: input 'a52 ' 48000 Hz 3F2R/LFE frame=1536 samples/1792 bytes
[0xb2000088] main audio filter debug: looking for audio filter module matching "scaletempo": 14 candidates
[0xb2000088] scaletempo audio filter debug: format: 48000 rate, 6 nch, 4 bps, fl32
[0xb2000088] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0xb2000088] scaletempo audio filter debug: 1.000 scale, 1440.000 stride_in, 1440 stride_out, 1152 standing, 288 overlap, 672 search, 2400 queue, fl32 mode
[0xb2000088] main audio filter debug: using audio filter module "scaletempo"
[0x104bd080] main audio output debug: conversion: 'a52 '->'f32b' 48000 Hz->48000 Hz 3F2R/LFE->3F2R/LFE
[0xb2015700] main audio converter debug: looking for audio converter module matching "any": 12 candidates
[0xb3403440] xcb_xv vout display debug: using XVideo extension v2.2
[0xb3403440] xcb_xv vout display error: no available XVideo adaptor
[0xb28aecd0] main video output debug: Reusing previous vout window
[0xb3403440] xcb_glx vout display debug: connected to X11.0 server
[0xb3403440] xcb_glx vout display debug:  vendor : The X.Org Foundation
[0xb3403440] xcb_glx vout display debug:  version: 11501000
[0xb3403440] xcb_glx vout display debug: using screen 0xe1
[0xb2015700] main audio converter debug: no audio converter modules matched
[0xb2015700] main audio converter debug: looking for audio converter module matching "any": 12 candidates
[0xb2015700] main audio converter debug: using audio converter module "a52tofloat32"
[0x104bd080] main audio output debug: conversion pipeline complete
[0x104bd080] main audio output debug: conversion: 'f32b'->'f32b' 48000 Hz->48000 Hz 3F2R/LFE->3F2R/LFE
[0x104bd080] main audio output debug: conversion pipeline complete
[0xb201dab8] main audio resampler debug: looking for audio resampler module matching "any": 3 candidates
[0xb201dab8] main audio resampler debug: using audio resampler module "samplerate"
[0x10593db8] main decoder debug: End of audio preroll
[0xb3403440] xcb_glx vout display debug: using GLX extension version 1.4
[0xb3403440] xcb_glx vout display debug: using X11 window 02a00000
[0xb3403440] main vout display debug: VoutDisplayEvent 'fullscreen' 0
[0xb3403440] main vout display debug: VoutDisplayEvent 'resize' 1024x576 window
[0xb3403440] main vout display debug: using vout display module "xcb_glx"
[0xb28aecd0] main video output debug: original format sz 720x576, of (0,0), vsz 720x576, 4cc I420, sar 64:45, msk r0x0 g0x0 b0x0
[0xb28e0570] main spu text debug: removing module "freetype"
[0xb28e0570] main spu text debug: looking for text renderer module matching "any": 2 candidates
[0xb28e0570] freetype spu text debug: Building font databases.
[0xb28e0570] freetype spu text debug: Took 0 microseconds
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0xb28e0570] freetype spu text debug: Using Serif Bold as font from file /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
[0xb28e0570] freetype spu text debug: using fontsize: 2
[0xb28e0570] main spu text debug: using text renderer module "freetype"
[0x104a95c0] avcodec decoder debug: using direct rendering
[0xb3403440] xcb_glx vout display debug: display is visible
[0xb3403440] main vout display debug: auto hiding mouse cursor
[0x104a95c0] main decoder debug: End of video preroll
[0xb3403440] main vout display error: Failed to resize display
[0x104a95c0] main decoder debug: Received first picture
[0x104bd080] pulse audio output debug: suspended
[0x104bd080] pulse audio output debug: changing sink 0: alsa_output.pci-0001_10_17.0.analog-stereo (KeyLargo/Intrepid Mac I/O Analog Stereo)
^C[0x1042a910] main libvlc debug: removing all interfaces
[0x1042a910] main libvlc debug: exiting
[0x104bed28] main interface debug: removing module "qt4"
[0x1043ab08] main playlist debug: deactivating the playlist
[0x1043ab08] main playlist debug: incoming request - stopping current input
[0x1042a910] main libvlc debug: exiting

```

---

### Post by mc4man on 2016-01-03
For vlc - 
by default it sets hwdec to automatic which can cause issues. So try - 
open vlc
go > Tools > Preferences > Input/Codecs & set "Hardware-accelerated decoding" to Disable. Then click _save_, close, reopen vlc & try your dvd again

---

### Post by brian-mccumber on 2016-01-03
I followed the quide at this link to get dvd's to start playing on both my computers - [https://help.ubuntu.com/stable/ubuntu-help/video-dvd-restricted.html](https://help.ubuntu.com/stable/ubuntu-help/video-dvd-restricted.html)

It says to install a couple gstreamer packages along with the packages you have already installed. maybe this is keeping you from being able to run the install-css line which is what I had to do in order to get the dvd's to finally start playing after installing using that guide in the link.

I have never had to download vlc to watch videos, I use the videos apps that came with Ubuntu so I didn't have to configure vlc to playback dvd's but maybe Lubuntu does not come with thevideo player app pre-installed but I am not sure since I use Ubuntu but since they are basically the same in alot of ways maybe this will work for you.

---

### Post by mark260 on 2016-01-03
m4cman, thanks for the suggestion. Sadly it didn't work. I've run the output code from 2 attempts as per your earlier instructions in case that helps at all.

From outputting a file from the command line:
```

[0x1042b910] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.1
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: disc reports copyright information 0x1
libdvdcss debug: drive region mask 0xfd, RPC-II, region code set
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key af:d1:b3:14:96
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 81:70:58:99:76
libdvdcss debug: using CSS key cache dir: /home/markjwgraham/.dvdcss/SKYFALL-2012122012421500-8170589976/
libdvdnav: DVD Title: SKYFALL
libdvdnav: DVD Serial Number: 41946A87
libdvdnav: DVD Title (Alternative): SKYFALL
libdvdnav: Unable to find map file '/home/markjwgraham/.dvdnav/SKYFALL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00022bb0
libdvdcss debug: getting title key at block 142256 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00023515
libdvdcss debug: getting title key at block 144661 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key c4:b6:fa:03:7a
libdvdcss debug: title key is c4:b6:fa:03:7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000235fb
libdvdcss debug: getting title key at block 144891 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key c7:f5:0c:db:02
libdvdcss debug: title key is c7:f5:0c:db:02
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0002f4f6
libdvdcss debug: getting title key at block 193782 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key ca:ac:91:86:9b
libdvdcss debug: title key is ca:ac:91:86:9b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0003118a
libdvdcss debug: getting title key at block 201098 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key c0:d7:c3:51:18
libdvdcss debug: title key is c0:d7:c3:51:18
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0003300a
libdvdcss debug: getting title key at block 208906 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key d1:79:0f:f6:06
libdvdcss debug: title key is d1:79:0f:f6:06
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0003c6a6
libdvdcss debug: getting title key at block 247462 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key d1:79:0f:f6:06
libdvdcss debug: title key is d1:79:0f:f6:06
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c190f
libdvdcss debug: getting title key at block 3938575 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 81:70:58:99:76
libdvdcss debug: decrypted title key c1:0b:2b:40:aa
libdvdcss debug: title key is c1:0b:2b:40:aa
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 4
[0x104f9670] main input error: ES_OUT_RESET_PCR called
[0x104f9670] main input error: ES_OUT_RESET_PCR called
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0xb2353030] xcb_xv vout display error: no available XVideo adaptor
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"

```

From the vlc -vv execution:

```

VLC media player 2.1.6 Rincewind (revision 2.1.6-0-gea01d28)
[0x100ec910] main libvlc debug: VLC media player - 2.1.6 Rincewind
[0x100ec910] main libvlc debug: Copyright © 1996-2015 the VideoLAN team
[0x100ec910] main libvlc debug: revision 2.1.6-0-gea01d28
[0x100ec910] main libvlc debug: configured with ./configure  '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--localstatedir=/var' '--libdir=${prefix}/lib/powerpc-linux-gnu' '--libexecdir=${prefix}/lib/powerpc-linux-gnu' '--disable-dependency-tracking' '--build=powerpc-linux-gnu' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--libdir=/usr/lib' '--sysconfdir=/etc' '--with-binary-version=0ubuntu14.04.1' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-chromaprint' '--enable-dbus' '--enable-dca' '--enable-dirac' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libfreerdp' '--enable-libmpeg2' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-oss' '--enable-pulse' '--enable-qt' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-sftp' '--enable-shout' '--enable-skins2' '--enable-smbclient' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-decklink' '--disable-dxva2' '--disable-fdkaac' '--disable-gnomevfs' '--disable-goom' '--disable-libvnc' '--disable-opencv' '--disable-projectm' '--disable-quicksync' '--disable-sndio' '--disable-telx' '--disable-vsxu' '--disable-wasapi' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv1394' '--enable-linsys' '--enable-omxil' '--enable-udev' '--enable-libva' '--enable-v4l2' '--disable-crystalhd' '--disable-mmx' '--disable-sse' '--disable-neon' '--enable-altivec' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'build_alias=powerpc-linux-gnu'
[0x100ec910] main libvlc debug: searching plug-in modules
[0x100ec910] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x100ec910] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x100ec910] main libvlc warning: cannot load module `/usr/lib/vlc/plugins/video_filter/libpostproc_plugin.so' (/usr/lib/libpostproc.so.52: R_PPC_REL24 relocation at 0x0d16d1c4 for symbol `memcpy' out of range)
[0x100ec910] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x100ec910] main libvlc debug: plug-ins loaded: 419 modules
[0x100ec910] main libvlc debug: opening config file (/home/markjwgraham/.config/vlc/vlcrc)
[0x100ec910] main libvlc debug: translation test: code is "C"
[0x100ec910] main libvlc debug: CPU has capabilities FPU 
[0x10187458] main input debug: Creating an input for 'Media Library'
[0x10187458] main input debug: Input is a meta file: disabling unneeded options
[0x10187458] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x10187458] main input debug: `file/xspf-open:///home/markjwgraham/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x10187458] main input debug: creating demux: access='file' demux='xspf-open' location='/home/markjwgraham/.local/share/vlc/ml.xspf' file='/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x100fdfa8] main demux debug: looking for access_demux module matching "file": 20 candidates
[0x100fdfa8] main demux debug: no access_demux modules matched
[0x10187458] main input debug: creating access 'file' location='/home/markjwgraham/.local/share/vlc/ml.xspf', path='/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x10187d28] main access debug: looking for access module matching "file": 25 candidates
[0x10187d28] filesystem access debug: opening file `/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x10187d28] main access debug: using access module "filesystem"
[0x10188b90] main stream debug: Using stream method for AStream*
[0x10188b90] main stream debug: starting pre-buffering
[0x10188b90] main stream debug: received first data after 0 ms
[0x10188b90] main stream debug: pre-buffering done 296 bytes in 0s - 2388 KiB/s
[0x10188518] main stream debug: looking for stream_filter module matching "any": 9 candidates
[0x10188518] main stream debug: no stream_filter modules matched
[0x10188518] main stream debug: looking for stream_filter module matching "record": 9 candidates
[0x10188518] main stream debug: using stream_filter module "record"
[0x10187458] main input debug: creating demux: access='file' demux='xspf-open' location='/home/markjwgraham/.local/share/vlc/ml.xspf' file='/home/markjwgraham/.local/share/vlc/ml.xspf'
[0x10189960] main demux debug: looking for demux module matching "xspf-open": 63 candidates
[0x10189960] playlist demux debug: using XSPF playlist reader
[0x10189960] main demux debug: using demux module "playlist"
[0x10189af8] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x10189af8] lua demux meta debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/meta/reader
[0x10189af8] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x10189af8] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x10189af8] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x10189af8] main demux meta debug: no meta reader modules matched
[0x10187458] main input debug: `file/xspf-open:///home/markjwgraham/.local/share/vlc/ml.xspf' successfully opened
[0x1017fb98] main xml reader debug: looking for xml reader module matching "any": 1 candidates
[0x1017fb98] main xml reader debug: using xml reader module "xml"
[0x10189960] playlist demux debug: parsed 0 tracks successfully
[0x10187458] main input debug: EOF reached
[0x10189960] main demux debug: removing module "playlist"
[0x10188518] main stream debug: removing module "record"
[0x10187d28] main access debug: removing module "filesystem"
[0x100fcb08] main playlist debug: creating audio output
[0x1017f080] main audio output debug: looking for audio output module matching "any": 6 candidates
[0x1017f080] pulse audio output debug: using library version 4.0.0
[0x1017f080] pulse audio output debug:  (compiled with version 4.0.0, protocol 28)
[0x1017f080] pulse audio output debug: connected locally to unix:/run/user/1000/pulse/native as client #10
[0x1017f080] pulse audio output debug: using protocol 28, server protocol 28
[0x1017f080] pulse audio output debug: adding sink 0: alsa_output.pci-0001_10_17.0.analog-stereo (KeyLargo/Intrepid Mac I/O Analog Stereo)
[0x1017f080] main audio output debug: using audio output module "pulse"
[0x100fcb08] main playlist debug: keeping audio output
[0x10177988] main interface debug: looking for interface module matching "hotkeys,none": 19 candidates
[0x10177988] main interface debug: using interface module "hotkeys"
[0x1017f4d8] main interface debug: looking for interface module matching "globalhotkeys,none": 19 candidates
[0x1017f4d8] main interface debug: using interface module "globalhotkeys"
[0x1010c638] main interface debug: looking for interface module matching "dbus,none": 19 candidates
[0x1010c638] dbus interface debug: listening on dbus as: org.mpris.MediaPlayer2.vlc.instance2009
[0x1010c638] main interface debug: using interface module "dbus"
[0x100ec910] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x10180e80] main interface debug: looking for interface module matching "any": 19 candidates
[0xb299d230] main generic debug: looking for extension module matching "any": 1 candidates
[0xb299d230] lua generic debug: Opening Lua Extension module
[0xb299d230] lua generic debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/extensions
[0xb299d230] lua generic debug: Trying Lua scripts in /usr/lib/vlc/lua/extensions
[0xb299d230] lua generic debug: Trying Lua playlist script /usr/lib/vlc/lua/extensions/VLSub.luac
[0xb299d230] lua generic debug: Scanning Lua script /usr/lib/vlc/lua/extensions/VLSub.luac
[0xb299d230] lua generic debug: Script /usr/lib/vlc/lua/extensions/VLSub.luac has the following capability flags: 0x5
[0xb299d230] lua generic debug: Trying Lua scripts in /usr/share/vlc/lua/extensions
[0xb299d230] main generic debug: using extension module "lua"
[0x10180e80] main interface debug: using interface module "qt4"
[0x100fcb08] main playlist debug: adding item `sr0' ( dvd:///dev/sr0 )
[0x100fcb08] main playlist debug: processing request item: sr0, node: null, skip: 0
[0x100fcb08] main playlist debug: rebuilding array of current - root Playlist
[0x100fcb08] main playlist debug: rebuild done - 1 items, index 0
[0x100fcb08] main playlist debug: starting playback of the new playlist item
[0x100fcb08] main playlist debug: resyncing on sr0
[0x100fcb08] main playlist debug: sr0 is at 0
[0x100fcb08] main playlist debug: creating new input thread
[0x10182198] main input debug: Creating an input for 'sr0'
[0x10180e80] qt4 interface debug: Adding a new MRL to recent ones: dvd:///dev/sr0
[0x10182198] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x10182198] main input debug: `dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0'
[0x10182198] main input debug: creating demux: access='dvd' demux='' location='/dev/sr0' file='/dev/sr0'
[0xb2e02f68] main demux debug: looking for access_demux module matching "dvd": 20 candidates
libdvdnav: Using dvdnav version 4.2.1
[0x10180c60] main input debug: Creating an input for 'sr0'
[0x100fcb08] main playlist debug: meta ok for (null), need to fetch art
[0x10180e80] qt4 interface debug: IM: Setting an input
[0x1010f998] main demux meta debug: looking for meta fetcher module matching "any": 1 candidates
[0x1010f998] lua demux meta debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/meta/fetcher
[0x1010f998] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[0x1010f998] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
libdvdnav: DVD Title: SKYFALL
libdvdnav: DVD Serial Number: 41946A87
libdvdnav: DVD Title (Alternative): SKYFALL
libdvdnav: Unable to find map file '/home/markjwgraham/.dvdnav/SKYFALL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00022bb0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00023515
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000235fb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0002f4f6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0003118a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0003300a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0003c6a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c190f
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
[0xb2e02f68] dvdnav demux debug: trying to go to dvd menu
[0x1010f998] main demux meta debug: using meta fetcher module "lua"
[0x1010f998] main demux meta debug: removing module "lua"
[0x100fcb08] main playlist debug: searching art for sr0
[0x10110898] main art finder debug: looking for art finder module matching "any": 2 candidates
[0xb2e02f68] main demux debug: using access_demux module "dvdnav"
[0xb2e433a8] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0x10110898] lua art finder debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/meta/art
[0x10110898] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[0x10110898] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[0xb2e433a8] lua demux meta debug: Trying Lua scripts in /home/markjwgraham/.local/share/vlc/lua/meta/reader
[0xb2e433a8] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0xb2e433a8] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x10110898] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[0xb2e433a8] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0xb2e433a8] main demux meta debug: no meta reader modules matched
[0x10182198] main input debug: `dvd:///dev/sr0' successfully opened
[0xb2e02f68] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[0x10182198] main input error: ES_OUT_RESET_PCR called
[0xb2e02f68] dvdnav demux debug: DVDNAV_VTS_CHANGE
[0xb2e02f68] dvdnav demux debug:      - vtsN=5
[0xb2e02f68] dvdnav demux debug:      - domain=8
[0x10182198] main input error: ES_OUT_RESET_PCR called
[0xb2e02f68] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0xb2e02f68] dvdnav demux debug:      - cellN=1
[0xb2e02f68] dvdnav demux debug:      - pgN=1
[0xb2e02f68] dvdnav demux debug:      - cell_length=6901200
[0xb2e02f68] dvdnav demux debug:      - pg_length=6901200
[0xb2e02f68] dvdnav demux debug:      - pgc_length=6901200
[0xb2e02f68] dvdnav demux debug:      - cell_start=0
[0xb2e02f68] dvdnav demux debug:      - pg_start=0
[0xb2e02f68] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0xb2e02f68] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0xb2e02f68] dvdnav demux debug:      - physical_wide=0
[0xb2e02f68] dvdnav demux debug:      - physical_letterbox=0
[0xb2e02f68] dvdnav demux debug:      - physical_pan_scan=1
[0xb2e02f68] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0x10182198] main input debug: selecting program id=0
[0xb2e43490] main decoder debug: looking for decoder module matching "any": 38 candidates
[0x10110898] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[0xb2e43490] main decoder debug: using decoder module "spudec"
[0xb2e43490] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0xb2e43490] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0xb2e02f68] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0xb2e02f68] dvdnav demux debug:      - physical=0
[0x10182198] main input debug: Buffering 0%
[0xb2e02f68] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0x10182198] main input debug: Buffering 0%
[0xb2e4b938] main decoder debug: looking for decoder module matching "any": 38 candidates
[0x10110898] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[0x10110898] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[0x10110898] main art finder debug: no art finder modules matched
[0x100fcb08] main playlist debug: art not found for SKYFALL
[0xb2e4b938] avcodec decoder debug: trying to use direct rendering
[0xb2e4b938] avcodec decoder debug: allowing 1 thread(s) for decoding
[0xb2e4b938] avcodec decoder debug: avcodec codec (MPEG-1/2 Video) started
[0xb2e4b938] main decoder debug: using decoder module "avcodec"
[0xb2e52cd0] main packetizer debug: looking for packetizer module matching "any": 21 candidates
[0xb2e52cd0] main packetizer debug: using packetizer module "packetizer_mpegvideo"
[0xb2e02f68] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0x10182198] main input debug: Buffering 1%
[0x10182198] main input debug: Buffering 1%
[0x10182198] main input debug: Buffering 2%
[0x10182198] main input debug: Buffering 2%
[0x10182198] main input debug: Buffering 3%
[0x10182198] main input debug: Buffering 3%
[0x10182198] main input debug: Buffering 4%
[0xb2e52cd0] packetizer_mpegvideo packetizer debug: size 720x576 fps=25.000
[0x10115328] main spu text debug: looking for text renderer module matching "any": 2 candidates
[0x10115328] freetype spu text debug: Building font databases.
[0x10182198] main input debug: Buffering 4%
[0x10182198] main input debug: Buffering 5%
[0x10182198] main input debug: Buffering 5%
[0x10182198] main input debug: Buffering 6%
[0x10182198] main input debug: Buffering 7%
[0x10182198] main input debug: Buffering 35%
[0x10182198] main input debug: Buffering 53%
[0xb2e7a0e8] main decoder debug: looking for decoder module matching "any": 38 candidates
[0xb2e7a0e8] main decoder debug: using decoder module "a52"
[0x10115328] freetype spu text debug: Took 1 microseconds
Fontconfig warning: FcPattern object size does not accept value "0"
[0x10182198] main input debug: Buffering 81%
[0x10182198] main input debug: Buffering 88%
[0x10182198] main input debug: Stream buffering done (328 ms in 136 ms)
[0xb2e7a0e8] a52 decoder debug: A/52 channels:2 samplerate:48000 bitrate:192000
Fontconfig warning: FcPattern object size does not accept value "0"
[0x10115328] freetype spu text debug: Using Serif Bold as font from file /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
[0x10115328] freetype spu text debug: using fontsize: 2
[0x10115328] main spu text debug: using text renderer module "freetype"
[0x10116598] main scale debug: looking for video filter2 module matching "any": 49 candidates
[0x10116598] swscale scale debug: 32x32 chroma: YUVA -> 16x16 chroma: RGBA with scaling using Bicubic (good quality)
[0x10116598] main scale debug: using video filter2 module "swscale"
[0x1013c368] main scale debug: looking for video filter2 module matching "any": 49 candidates
[0x1013c368] yuvp scale debug: YUVP to YUVA converter
[0x1013c368] main scale debug: using video filter2 module "yuvp"
[0x10110fd0] main video output debug: Deinterlacing available
[0x10110fd0] main video output debug: deinterlace -1, mode blend, is_needed 0
[0x10110fd0] main video output debug: Opening vout display wrapper
[0xb214cd68] main vout display debug: looking for vout display module matching "any": 12 candidates
[0xb211b040] main window debug: looking for vout window xid module matching "qt4,any": 4 candidates
[0xb211b040] qt4 window debug: requesting video window...
[0x10180e80] qt4 interface debug: Video was requested 0, 0
[0xb211b040] main window debug: using vout window xid module "qt4"
[0xb2151118] main inhibit debug: looking for inhibit module matching "any": 2 candidates
[0xb2151118] dbus_screensaver inhibit debug: cannot find service org.freedesktop.ScreenSaver
[0xb2151118] dbus_screensaver inhibit debug: cannot find service org.freedesktop.PowerManagement.Inhibit
[0xb2151118] dbus_screensaver inhibit debug: cannot find service org.mate.SessionManager
[0xb2151118] dbus_screensaver inhibit debug: cannot find service org.gnome.SessionManager
[0xb2151118] main inhibit debug: using inhibit module "xdg_screensaver"
[0xb214cd68] xcb_xv vout display debug: connected to X11.0 server
[0xb214cd68] xcb_xv vout display debug:  vendor : The X.Org Foundation
[0xb214cd68] xcb_xv vout display debug:  version: 11501000
[0xb214cd68] xcb_xv vout display debug: using screen 0xe1
[0xb214cd68] xcb_xv vout display debug: using XVideo extension v2.2
[0xb214cd68] xcb_xv vout display error: no available XVideo adaptor
[0x10110fd0] main video output debug: Reusing previous vout window
[0xb214cd68] xcb_glx vout display debug: connected to X11.0 server
[0xb214cd68] xcb_glx vout display debug:  vendor : The X.Org Foundation
[0xb214cd68] xcb_glx vout display debug:  version: 11501000
[0xb214cd68] xcb_glx vout display debug: using screen 0xe1
[0xb214cd68] xcb_glx vout display debug: using GLX extension version 1.4
[0xb214cd68] xcb_glx vout display debug: using X11 window 02a00000
[0xb214cd68] main vout display debug: VoutDisplayEvent 'fullscreen' 0
[0xb214cd68] main vout display debug: VoutDisplayEvent 'resize' 1024x576 window
[0xb214cd68] main vout display debug: using vout display module "xcb_glx"
[0x10110fd0] main video output debug: original format sz 720x576, of (0,0), vsz 720x576, 4cc I420, sar 64:45, msk r0x0 g0x0 b0x0
[0x10115328] main spu text debug: removing module "freetype"
[0x10115328] main spu text debug: looking for text renderer module matching "any": 2 candidates
[0x10115328] freetype spu text debug: Building font databases.
[0x10115328] freetype spu text debug: Took 1 microseconds
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x10115328] freetype spu text debug: Using Serif Bold as font from file /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
[0x10115328] freetype spu text debug: using fontsize: 2
[0x10115328] main spu text debug: using text renderer module "freetype"
[0x100fcb08] main playlist debug: reusing audio output
[0x1017f080] pulse audio output debug: using stereo channel map
[0x1017f080] pulse audio output debug: digital pass-through not available
[0x1017f080] pulse audio output debug: changed buffer metrics: maxlength=4194304, tlength=46080, prebuf=0, minreq=15360
[0x1017f080] pulse audio output debug: connected to sink alsa_output.pci-0001_10_17.0.analog-stereo
[0x1017f080] main audio output debug: output 'f32b' 48000 Hz Stereo frame=1 samples/8 bytes
[0xb2e7fa40] main volume debug: looking for audio volume module matching "any": 2 candidates
[0xb2e7fa40] main volume debug: using audio volume module "float_mixer"
[0x1017f080] pulse audio output debug: base volume: 65536
[0x1017f080] pulse audio output debug: changing sink 0: alsa_output.pci-0001_10_17.0.analog-stereo (KeyLargo/Intrepid Mac I/O Analog Stereo)
[0x1017f080] main audio output debug: input 'a52 ' 48000 Hz Stereo frame=1536 samples/768 bytes
[0xb2e81860] main audio filter debug: looking for audio filter module matching "scaletempo": 14 candidates
[0xb2e81860] scaletempo audio filter debug: format: 48000 rate, 2 nch, 4 bps, fl32
[0xb2e4b938] avcodec decoder debug: using direct rendering
[0xb2e81860] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0xb2e81860] scaletempo audio filter debug: 1.000 scale, 1440.000 stride_in, 1440 stride_out, 1152 standing, 288 overlap, 672 search, 2400 queue, fl32 mode
[0xb2e81860] main audio filter debug: using audio filter module "scaletempo"
[0x1017f080] main audio output debug: conversion: 'a52 '->'f32b' 48000 Hz->48000 Hz Stereo->Stereo
[0xb2e81240] main audio converter debug: looking for audio converter module matching "any": 12 candidates
[0xb214cd68] xcb_glx vout display debug: display is visible
[0xb2e81240] main audio converter debug: no audio converter modules matched
[0xb2e81240] main audio converter debug: looking for audio converter module matching "any": 12 candidates
[0xb2e81240] main audio converter debug: using audio converter module "a52tofloat32"
[0x1017f080] main audio output debug: conversion pipeline complete
[0x1017f080] main audio output debug: conversion: 'f32b'->'f32b' 48000 Hz->48000 Hz Stereo->Stereo
[0x1017f080] main audio output debug: conversion pipeline complete
[0xb2e917d8] main audio resampler debug: looking for audio resampler module matching "any": 3 candidates
[0xb2e917d8] main audio resampler debug: using audio resampler module "samplerate"
[0xb2e7a0e8] main decoder debug: End of audio preroll
[0xb2e4b938] main decoder debug: End of video preroll
[0xb214cd68] main vout display error: Failed to resize display
[0xb2e4b938] main decoder debug: Received first picture
[0x1017f080] pulse audio output debug: suspended
[0x1017f080] pulse audio output debug: changing sink 0: alsa_output.pci-0001_10_17.0.analog-stereo (KeyLargo/Intrepid Mac I/O Analog Stereo)

```

---

### Post by mark260 on 2016-01-03
Hey Brian, thanks for chipping in. I've actually got those installed already - sorry! Hence why this has been giving me grief for over a month now. I've read almost every thread I can find on the subject and still seem no closer to finding a solution.

---

### Post by brian-mccumber on 2016-01-03
> 
[COLOR=#000000]- I have successfully installed livdvdread4, libdvdnav4, and libdvdcss2
[/COLOR][COLOR=#000000]

I don't see anything in here that says you installed the ugly gstreamer packages from that link I sent.[/COLOR]

---

### Post by mark260 on 2016-01-03
You're right, I didn't list them in my initial post, but nevertheless I can assure you they are installed!

---

### Post by brian-mccumber on 2016-01-03
This line - ```
 sudo /usr/share/doc/libdvdread4/install-css.sh
``` was required to run in terminal before my desktop computer would start playing videos. Maybe since you apparently compiled a package specific to powerbook it put this in another place then running that line would not work. If the custom powerbook compilation put that directory in a different place you could find this directory and substitute   /usr/share/doc/libdvdread4 with the path where you found libdvdread4 folder and then try to run that line again.

---

### Post by mc4man on 2016-01-03
```
 xcb_xv vout display error: no available XVideo adaptor
```
Open vlc again, > Tools > Pref's (leaving hwdec disabled )
go > Clicking on the Video tab > Output. Change from automatic to something else. 
Try OpenGL Glx video output (xcb) first.
(click save, try again on dvd or any local video file.
If that doesn't work try X11 though OpenGl should work

---

### Post by mark260 on 2016-01-03
mc4man, looks like we're getting somewhere! OpenGL GLX wasn't happy at all (it was already set to that), but X11 did the trick.

I'm now getting flawless audio, but still no video.

```

[0x105f9670] main input error: ES_OUT_RESET_PCR called
[0x105f9670] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0xb2147fa0] main vout display error: Failed to resize display


```

Those are the only errors flagging up from running VLC from the terminal. Any thoughts?

---

### Post by mc4man on 2016-01-04
You should probably post some info on hardware - 
inxi -b
sudo lshw -c display

Do you have a local video you can try to play?
xv should work, what's this show?
xvinfo

You could also try deleting ~/.config/vlc

---

### Post by mark260 on 2016-01-04
Thanks for the continued help mc4man, it's very much appreciated.

1. inxi -b
```

System:    Host: lubuntu-laptop Kernel: 3.13.0-74-powerpc-smp ppc (32 bit) 
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 14.04 trusty
Machine:   No /sys/class/dmi machine data: try newer kernel, or install dmidecode
CPU:       Single core 7447/7457 altivec supported (-UP-) clocked at 999.99.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV350/M10 [Mobility Radeon 9600 PRO Turbo] 
           X.Org: 1.15.1 drivers: fbdev,ati,radeon Resolution: 1280x854@60.0hz 
           GLX Renderer: Rasterizer GLX Version: 2.1 Mesa 10.1.3
Network:   Card-1: Broadcom BCM4306 802.11b/g Wireless LAN Controller driver: b43-pci-bridge 
           Card-2: Apple UniNorth 2 GMAC (Sun GEM) driver: gem 
Drives:    HDD Total Size: 60.0GB (8.2% used)
Info:      Processes: 135 Uptime: 9 min Memory: 230.3/494.6MB Client: Shell (bash) inxi: 1.9.17 

```

sudo lshw -c display
```

 *-display               
       description: VGA compatible controller
       product: RV350/M10 [Mobility Radeon 9600 PRO Turbo]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeonfb latency=255 mingnt=8
       resources: irq:48 memory:b8000000-bfffffff ioport:400(size=256) memory:b0000000-b000ffff memory:b0020000-b003ffff

```


2. xvinfo = interesting result!

```

X-Video Extension version 2.2
screen #0
 no adaptors present

```

Am now scouring the net for how to remedy this.
3. deleting .config/vlc = no change

---

### Post by mc4man on 2016-01-04
Unfortunately i've no experience with radeon adapters let alone powerpc
It would appear your hardware  is somewhat aged, with no xv & x11 not working not sure what you can do. 
Suffice to say the issue has nothing to do with dvd's per se, more about getting a useable video output, either in general or for vlc.

Maybe try installing the vlc-plugin-sdl package, then in vlc's pref's  Video section choose "Simple DirectMedia Layer.."  for Output.

---

### Post by mark260 on 2016-01-04
No worries sir, you've been most helpful!I looked in the Apple Hardware support area and found this thread --> [http://ubuntuforums.org/showthread.php?t=2294789](http://ubuntuforums.org/showthread.php?t=2294789)That helpful gentleman created an archive of debs that fixed the hardware decoding problems, so now everything is running perfectly.For anyone scouring the net for answers to this one, try visiting that thread and following the instructions there.

---

