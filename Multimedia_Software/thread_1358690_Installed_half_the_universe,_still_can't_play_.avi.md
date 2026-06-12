---
title: "Installed half the universe, still can't play .avi's."
date: 2009-12-18
forum: Multimedia Software
---

### Post by viktorzk on 2009-12-18
Hello,

I've followed the sticky HowTo in this section, and I still cannot play my .avi, .mp4, and .flv files.

.avi: Movie player cannot find "DivX MPEG-4 Version 5 decoder". VLC does not support the video formats "[COLOR=#000000]DX50" and "mpga".

.mp4:  [/COLOR]Movie player cannot find [COLOR=#000000]"H.264 decoder". VLC does not support the audio or video format "avc1". Both play the music though.

.flv: [/COLOR]Movie player cannot find "[COLOR=#000000]Sorenson Spark Video decoder". [/COLOR][COLOR=#000000]VLC outputs lots of identical errors that it does not support the audio or video format "mpga".

And MPlayer does not do anything when I press the 'play' button.

I was hoping to be able to play virtually any multimedia file, like in Windows with a codec pack. Is this possible in Linux? Or at least the more common formats?

Thank you.
[/COLOR]

---

### Post by madverb on 2009-12-18
sudo aptitude install ubuntu-restricted-extras

---

### Post by viktorzk on 2009-12-18
Already installed, reinstalling it doesn't help.

---

### Post by Filipek on 2009-12-18
> **viktorzk said:**
> Hello,

I've followed the sticky HowTo in this section, and I still cannot play my .avi, .mp4, and .flv files.

.avi: Movie player cannot find "DivX MPEG-4 Version 5 decoder". VLC does not support the video formats "[COLOR=#000000]DX50" and "mpga".

.mp4:  [/COLOR]Movie player cannot find [COLOR=#000000]"H.264 decoder". VLC does not support the audio or video format "avc1". Both play the music though.

.flv: [/COLOR]Movie player cannot find "[COLOR=#000000]Sorenson Spark Video decoder". [/COLOR][COLOR=#000000]VLC outputs lots of identical errors that it does not support the audio or video format "mpga".

And MPlayer does not do anything when I press the 'play' button.

I was hoping to be able to play virtually any multimedia file, like in Windows with a codec pack. Is this possible in Linux? Or at least the more common formats?

Thank you.
[/COLOR]

I don't know what you have done mate but even installing VLC using apt should do the trick. Of course Linux is capable to play everything and it will (after install the above mentioned extras).

Could you please specify, what you did and didn't do after installation?

---

### Post by Uncle Spellbinder on 2009-12-18
```
sudo apt-get install ubuntu-restricted-extras
```

that should work, did for me.

also:

```
sudo apt-get install libdvdcss2
```

Aslo might want to add Medibuntu to your sources.list:

```
gksudo gedit /etc/apt/sources.list
```

then add Medibuntu:

```
#### Medibuntu - http://www.medibuntu.org/ 
## sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ karmic free non-free
```

---

### Post by stinger30au on 2009-12-18
after medibuntu installed install vlc

sudo apt-get install vlc

---

### Post by viktorzk on 2009-12-18
> **Filipek said:**
> I don't know what you have done mate but even installing VLC using apt should do the trick. Of course Linux is capable to play everything and it will (after install the above mentioned extras).

Could you please specify, what you did and didn't do after installation?

I did too many things to remember them all. I remember installing something whose name starts with FF, along with its plugins/codecs, also vlc and the restricted extras, then I tried to remove all multimedia-related packages, then reinstalled ubuntu-desktop and the restricted extras, then found the HowTo ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)) and followed it.

---

### Post by viktorzk on 2009-12-18
Uncle Spellbinder, Medibuntu is already in the file, enabled. All packages you suggested are already installed. (Running the commands you wrote outputs that everything is at the newest version, "0 upgraded, 0 newly installed, ..." and no errors.)

stinger30au, Output: "vlc is already the newest version".

---

### Post by mc4man on 2009-12-18
did you install any ppa's, ubuntu tweak, or libs from outside sources, ffmpeg libs in particular? (libavcodec, libavformat, libavutil, ect

you can run and post output from these if you wish
```
 cat /etc/apt/sources.list
```
```

ls /etc/apt/sources.list.d/*.list
```

---

### Post by viktorzk on 2009-12-18
Yes, I have installed many ffmpeg packages, including the ones you mentioned:
ffmpeg,libsox-fmt-ffmpeg,gstreamer0.10-ffmpeg,libavutil-extra-49,libavdevice52,libavfilter0,libpostproc-extra-51,libswscale-extra-0,libavcodec-extra-52,libavformat-extra-52,libxine1-ffmpeg

I don't know what a ppa is. No ubuntu tweaks.

```
viktor@vzknb:~$  cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main
deb http://packages.medibuntu.org/ karmic free non-free
deb http://packages.medibuntu.org/ jaunty free non-free
# deb http://packages.medibuntu.org/ karmic free non-free
``````
viktor@vzknb:~$ ls /etc/apt/sources.list.d/*.list
/etc/apt/sources.list.d/medibuntu.list
```

---

### Post by Uncle Spellbinder on 2009-12-18
> **viktorzk said:**
> Uncle Spellbinder, Medibuntu is already in the file, enabled. All packages you suggested are already installed. (Running the commands you wrote outputs that everything is at the newest version, "0 upgraded, 0 newly installed, ..." and no errors.)

stinger30au, Output: "vlc is already the newest version".

Assuming all the necessary codecs are installed, as you say. then you should have no issues playing any video or audio file.

I'm baffled.

---

### Post by Uncle Spellbinder on 2009-12-18
> **viktorzk said:**
> Yes, I have installed many ffmpeg packages, including the ones you mentioned:
ffmpeg,libsox-fmt-ffmpeg,gstreamer0.10-ffmpeg,libavutil-extra-49,libavdevice52,libavfilter0,libpostproc-extra-51,libswscale-extra-0,libavcodec-extra-52,libavformat-extra-52,libxine1-ffmpeg

I don't know what a ppa is. No ubuntu tweaks.

```

deb http://packages.medibuntu.org/ karmic free non-free
[color=#660000]**deb http://packages.medibuntu.org/ jaunty free non-free**[/color]
**[color=#660000]# deb http://packages.medibuntu.org/ karmic free non-free[/color]**
``````
viktor@vzknb:~$ ls /etc/apt/sources.list.d/*.list
/etc/apt/sources.list.d/medibuntu.list
```


You have one medibuntu commented out. It is NOT enabled. then you have a Jaunty and Karmic version both enabled. Assuming you're running Larmic, get rid of the unnecessary Jaunty repo and the duplicate medibuntu repo (the ones in red).

---

### Post by viktorzk on 2009-12-18
Done, now should I reinstall something?

```

...
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main
deb http://packages.medibuntu.org/ karmic free non-free

```So the commented out line disables the added-by-the-previous-line source? I thought commented out lines were ignored?

---

### Post by mc4man on 2009-12-18
Try opening up synaptic package manager, searching ffmpeg and mark **every** ffmpeg lib installed (green box) for removal.
Start at libavcodec52 and work your way down to libswscale0 ( 7 libs, 28 boxes possible

Then click apply. When that's done close out synaptic and run this, try again.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse vlc
```

If no go then open vlc like this aand try to play an .avi ( just drop the .avi onto vlc if you wish

```
vlc -vv
```

---

### Post by viktorzk on 2009-12-18
Doesn't work, same errors as in the beginning.

By the way, I just noticed that if I open the .avi or .flv file with "Avidemux GTK+", it plays the video.

---

### Post by mc4man on 2009-12-18
Avidemux provides it's own ffmpeg libraries, the players you've mentioned use the system installed ffmpeg libs.

If you totally removed them all and then ran the command you should have compatible libs

What is the version number of libavcodec-extra-52 as seen in synaptic (properties of the package

What does this show? (may say not installed
```
ffmpeg
```

Did you build  a shared ffmpeg to usr/local?

And finally if you wish post the output from vlc -vv when trying to play an .avi

---

### Post by viktorzk on 2009-12-18
[LEFT]libavcodec52 version 4:0.5+svn20090706-2ubuntu2

(EDIT: now it is libavcodec52, without the '-extra-')

ffmpeg not installed

> Did you build  a shared ffmpeg to usr/local?I have not build anything from source, if that is what you mean. All packages have been installed through Synaptic or apt-get.

```
viktor@vzknb:~$ vlc -vv
VLC media player 1.0.2 Goldeneye
[0x91ad140] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x91ad140] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu2' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x91ad140] main libvlc debug: translation test: code is "en_GB"
[0x91ad140] main libvlc debug: checking plugin modules
[0x91ad140] main libvlc debug: loading plugins cache file /home/viktor/.cache/vlc/plugins-04041e.dat
[0x91ad140] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so' (/usr/lib/libmad.so.0: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so' (/usr/lib/liba52-0.7.4.so: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/access/libdvdread_plugin.so' (/usr/lib/libdvdread.so.4: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/access/libdvdnav_plugin.so' (/usr/lib/libdvdnav.so.4: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libschroedinger_plugin.so' (/usr/lib/libschroedinger-1.0.so.0: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so' (/usr/lib/libgsm.so.1: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (/usr/lib/libgsm.so.1: file too short)
[0x91ad140] main libvlc debug: module bank initialized (363 modules)
[0x91ad140] main libvlc debug: opening config file (/home/viktor/.config/vlc/vlcrc)
[0x91ad140] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x91ad140] main libvlc debug: looking for memcpy module: 3 candidates
[0x91ad140] main libvlc debug: using memcpy module "memcpymmxext"
[0x9241228] main input debug: Creating an input for 'Media Library'
[0x9241228] main input debug: Input is a meta file: disabling unneeded options
[0x9241228] main input debug: using timeshift granularity of 50 MBytes
[0x9241228] main input debug: using timeshift path '/tmp'
[0x9241228] main input debug: `file/xspf-open:///home/viktor/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/viktor/.local/share/vlc/ml.xspf'
[0x9241228] main input debug: creating demux: access='file' demux='xspf-open' path='/home/viktor/.local/share/vlc/ml.xspf'
[0x923f4a0] main demux debug: looking for access_demux module: 0 candidates
[0x923f4a0] main demux debug: no access_demux module matched "file"
[0x923f4a0] main demux debug: TIMER module_need() : 0.073 ms - Total 0.073 ms / 1 intvls (Avg 0.073 ms)
[0x9241228] main input debug: creating access 'file' path='/home/viktor/.local/share/vlc/ml.xspf'
[0x923fc88] main access debug: looking for access module: 3 candidates
[0x923fc88] access_file access debug: opening file `/home/viktor/.local/share/vlc/ml.xspf'
[0x923fc88] main access debug: using access module "access_file"
[0x923fc88] main access debug: TIMER module_need() : 0.503 ms - Total 0.503 ms / 1 intvls (Avg 0.503 ms)
[0x92471d8] main stream debug: Using AStream*Stream
[0x92471d8] main stream debug: pre buffering
[0x92471d8] main stream debug: received first data after 0 ms
[0x92471d8] main stream debug: pre-buffering done 296 bytes in 0s - 10706 kbytes/s
[0x9246320] main stream debug: looking for stream_filter module: 4 candidates
[0x9246320] main stream debug: TIMER module_need() : 0.453 ms - Total 0.453 ms / 1 intvls (Avg 0.453 ms)
[0x9249168] main stream debug: looking for stream_filter module: 1 candidate
[0x9249168] main stream debug: using stream_filter module "stream_filter_record"
[0x9249168] main stream debug: TIMER module_need() : 0.224 ms - Total 0.224 ms / 1 intvls (Avg 0.224 ms)
[0x9241228] main input debug: creating demux: access='file' demux='xspf-open' path='/home/viktor/.local/share/vlc/ml.xspf'
[0x9249230] main demux debug: looking for demux module: 1 candidate
[0x9249230] playlist demux debug: using XSPF playlist reader
[0x9249230] main demux debug: using demux module "playlist"
[0x9249230] main demux debug: TIMER module_need() : 0.277 ms - Total 0.277 ms / 1 intvls (Avg 0.277 ms)
[0x9241228] main input debug: `file/xspf-open:///home/viktor/.local/share/vlc/ml.xspf' successfully opened
[0x9249470] main xml debug: looking for xml module: 2 candidates
[0x9249470] main xml debug: using xml module "xtag"
[0x9249470] main xml debug: TIMER module_need() : 0.476 ms - Total 0.476 ms / 1 intvls (Avg 0.476 ms)
[0x9249230] playlist demux debug: parsed 0 tracks successfully
[0x9249470] main xml debug: removing module "xtag"
[0x9241228] main input debug: EOF reached
[0x9249230] main demux debug: removing module "playlist"
[0x9249168] main stream debug: removing module "stream_filter_record"
[0x923fc88] main access debug: removing module "access_file"
[0x9241228] main input debug: TIMER input launching for 'Media Library' : 4.857 ms - Total 4.857 ms / 1 intvls (Avg 4.857 ms)
[0x923cde8] main playlist debug: Activated
[0x923cde8] main playlist debug: rebuilding array of current - root Playlist
[0x923cde8] main playlist debug: rebuild done - 0 items, index -1
[0x92413f0] main interface debug: looking for interface module: 1 candidate
[0x92413f0] main interface debug: using interface module "hotkeys"
[0x92413f0] main interface debug: TIMER module_need() : 0.279 ms - Total 0.279 ms / 1 intvls (Avg 0.279 ms)
[0x92413f0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x92413f0] main interface debug: thread started
[0x923e310] main interface debug: looking for interface module: 1 candidate
[0x923e310] main interface debug: using interface module "inhibit"
[0x923e310] main interface debug: TIMER module_need() : 1.262 ms - Total 1.262 ms / 1 intvls (Avg 1.262 ms)
[0x923e310] main interface debug: thread started
[0x923e310] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9246218] main interface debug: looking for interface module: 1 candidate
[0x9246218] main interface debug: using interface module "screensaver"
[0x9246218] main interface debug: TIMER module_need() : 0.202 ms - Total 0.202 ms / 1 intvls (Avg 0.202 ms)
[0x9246218] main interface debug: thread started
[0x9246218] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x91ad2d8] main interface debug: looking for interface module: 1 candidate
[0x91ad2d8] main interface debug: using interface module "signals"
[0x91ad2d8] main interface debug: TIMER module_need() : 0.199 ms - Total 0.199 ms / 1 intvls (Avg 0.199 ms)
[0x91ad2d8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x924ad68] main interface debug: looking for interface module: 0 candidates
[0x924ad68] main interface error: no interface module matched "globalhotkeys,none"
[0x924ad68] main interface debug: TIMER module_need() : 0.086 ms - Total 0.086 ms / 1 intvls (Avg 0.086 ms)
[0x924ad68] main interface error: no suitable interface module
[0x91ad140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x91ad140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x924ae10] main interface debug: looking for interface module: 4 candidates
[0x91ad2d8] main interface debug: thread started
[0x91ad2d8] main interface debug: thread ended
[0x924ae10] main interface debug: using interface module "qt4"
[0x924ae10] main interface debug: TIMER module_need() : 167.177 ms - Total 167.177 ms / 1 intvls (Avg 167.177 ms)
[0x924ae10] qt4 interface debug: Error while initializing qt-specific localization
[0x924ae10] main interface debug: thread started
[0x924ae10] main interface debug: thread ended
[0x924ae10] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x923cde8] main playlist debug: adding item `Yes Prime Minister Series 1 Episode 4 - The Key.avi' ( /media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi )
[0x924ae10] qt4 interface debug: Adding a new MRL to recent ones: /media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi
[0x923cde8] main playlist debug: rebuilding array of current - root Playlist
[0x923cde8] main playlist debug: rebuild done - 1 items, index -1
[0x923cde8] main playlist debug: processing request item Yes Prime Minister Series 1 Episode 4 - The Key.avi node null skip 0
[0x923cde8] main playlist debug: resyncing on Yes Prime Minister Series 1 Episode 4 - The Key.avi
[0x923cde8] main playlist debug: Yes Prime Minister Series 1 Episode 4 - The Key.avi is at 0
[0x923cde8] main playlist debug: starting new item
[0x923cde8] main playlist debug: creating new input thread
[0xb7401ee8] main input debug: Creating an input for 'Yes Prime Minister Series 1 Episode 4 - The Key.avi'
[0xb7401ee8] main input debug: thread started
[0xb7401ee8] main input debug: using timeshift granularity of 50 MBytes
[0xb7401ee8] main input debug: using timeshift path '/tmp'
[0xb7401ee8] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0x924ae10] qt4 interface debug: IM: Setting an input
[0xb7401ee8] main input debug: `/media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi' gives access `' demux `' path `/media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi'
[0xb7401ee8] main input debug: creating demux: access='' demux='' path='/media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi'
[0x946a698] main demux debug: looking for access_demux module: 6 candidates
[0x924ae10] qt4 interface debug: Updating the geometry
[0x946a698] main demux debug: TIMER module_need() : 3.872 ms - Total 3.872 ms / 1 intvls (Avg 3.872 ms)
[0xb7401ee8] main input debug: creating access '' path='/media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi'
[0x9484e50] main access debug: looking for access module: 7 candidates
[0x9484e50] vcd access debug: trying .cue file: /media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.cue
[0x9484e50] vcd access debug: could not find .cue file
[0x9484e50] access_file access debug: opening file `/media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi'
[0x9484e50] main access debug: using access module "access_file"
[0x9484e50] main access debug: TIMER module_need() : 6.147 ms - Total 6.147 ms / 1 intvls (Avg 6.147 ms)
[0x9484238] main stream debug: Using AStream*Stream
[0x9484238] main stream debug: pre buffering
[0x9484238] main stream debug: received first data after 0 ms
[0x9484238] main stream debug: pre-buffering done 1024 bytes in 0s - 25641 kbytes/s
[0x9485e98] main stream debug: looking for stream_filter module: 4 candidates
[0x9485e98] main stream debug: TIMER module_need() : 0.165 ms - Total 0.165 ms / 1 intvls (Avg 0.165 ms)
[0x9485e88] main stream debug: looking for stream_filter module: 1 candidate
[0x9485e88] main stream debug: using stream_filter module "stream_filter_record"
[0x9485e88] main stream debug: TIMER module_need() : 0.168 ms - Total 0.168 ms / 1 intvls (Avg 0.168 ms)
[0xb7401ee8] main input debug: creating demux: access='' demux='' path='/media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi'
[0x94860a8] main demux debug: looking for demux module: 50 candidates
[0x9485e88] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:244547174 pos:0
[0x9485e88] avi stream debug: found LIST chunk: 'AVI '
[0x9485e88] avi stream debug: <list 'AVI '>
[0x9485e88] avi stream debug: found Chunk fourcc:5453494c (LIST) size:8830 pos:12
[0x9485e88] avi stream debug: found LIST chunk: 'hdrl'
[0x9485e88] avi stream debug: <list 'hdrl'>
[0x9485e88] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24
[0x9485e88] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 512x384
[0x9485e88] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4244 pos:88
[0x9485e88] avi stream debug: found LIST chunk: 'strl'
[0x9485e88] avi stream debug: <list 'strl'>
[0x9485e88] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100
[0x9485e88] avi stream debug: strh: type:vids handler:0x64697678 samplesize:0 25.00fps
[0x9485e88] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164
[0x9485e88] avi stream debug: strf: video:XVID 512x384 planes:1 12bpp
[0x9485e88] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:212
[0x9485e88] avi stream debug: </list 'strl'>
[0x9485e88] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4234 pos:4340
[0x9485e88] avi stream debug: found LIST chunk: 'strl'
[0x9485e88] avi stream debug: <list 'strl'>
[0x9485e88] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:4352
[0x9485e88] avi stream debug: strh: type:auds handler:0x00000000 samplesize:0 41.67fps
[0x9485e88] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:4416
[0x9485e88] avi stream debug: strf: audio:0x0055 channels:2 48000Hz 0bits/sample 132kb/s
[0x9485e88] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:4454
[0x9485e88] avi stream debug: </list 'strl'>
[0x9485e88] avi stream debug: found Chunk fourcc:5453494c (LIST) size:260 pos:8582
[0x9485e88] avi stream debug: found LIST chunk: 'odml'
[0x9485e88] avi stream debug: <list 'odml'>
[0x9485e88] avi stream debug: found Chunk fourcc:686c6d64 (dmlh) size:248 pos:8594
[0x9485e88] avi stream warning: unknown chunk (not loaded)
[0x9485e88] avi stream debug: </list 'odml'>
[0x9485e88] avi stream debug: </list 'hdrl'>
[0x9485e88] avi stream debug: found Chunk fourcc:5453494c (LIST) size:72 pos:8850
[0x9485e88] avi stream debug: found LIST chunk: 'INFO'
[0x9485e88] avi stream debug: <list 'INFO'>
[0x9485e88] avi stream debug: found Chunk fourcc:54465349 (ISFT) size:43 pos:8862
[0x9485e88] avi stream debug: ISFT: software : VirtualDubMod 1.5.4.1 (build 2178/release)
[0x9485e88] avi stream debug: found Chunk fourcc:31534149 (IAS1) size:8 pos:8914
[0x9485e88] avi stream warning: unknown chunk (not loaded)
[0x9485e88] avi stream debug: </list 'INFO'>
[0x9485e88] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1302 pos:8930
[0x9485e88] avi stream debug: found Chunk fourcc:5453494c (LIST) size:242650750 pos:10240
[0x9485e88] avi stream debug: skipping movi chunk
[0x9485e88] avi stream debug: found Chunk fourcc:31786469 (idx1) size:1886176 pos:242660998
[0x924ae10] qt4 interface debug: Updating the geometry
[0x9485e88] avi stream debug: idx1: index entry:117886
[0x9485e88] avi stream debug: </list 'AVI '>
[0x9485e88] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:394 pos:244547182
[0x9485e88] avi stream debug: * LIST-root size:244547584 pos:0
[0x9485e88] avi stream debug:      + RIFF-AVI  size:244547174 pos:0
[0x9485e88] avi stream debug:      |    + LIST-hdrl size:8830 pos:12
[0x9485e88] avi stream debug:      |    |    + avih size:56 pos:24
[0x9485e88] avi stream debug:      |    |    + LIST-strl size:4244 pos:88
[0x9485e88] avi stream debug:      |    |    |    + strh size:56 pos:100
[0x9485e88] avi stream debug:      |    |    |    + strf size:40 pos:164
[0x9485e88] avi stream debug:      |    |    |    + JUNK size:4120 pos:212
[0x9485e88] avi stream debug:      |    |    + LIST-strl size:4234 pos:4340
[0x9485e88] avi stream debug:      |    |    |    + strh size:56 pos:4352
[0x9485e88] avi stream debug:      |    |    |    + strf size:30 pos:4416
[0x9485e88] avi stream debug:      |    |    |    + JUNK size:4120 pos:4454
[0x9485e88] avi stream debug:      |    |    + LIST-odml size:260 pos:8582
[0x9485e88] avi stream debug:      |    |    |    + dmlh size:248 pos:8594
[0x9485e88] avi stream debug:      |    + LIST-INFO size:72 pos:8850
[0x9485e88] avi stream debug:      |    |    + ISFT size:43 pos:8862
[0x9485e88] avi stream debug:      |    |    + IAS1 size:8 pos:8914
[0x9485e88] avi stream debug:      |    + JUNK size:1302 pos:8930
[0x9485e88] avi stream debug:      |    + LIST-movi size:242650750 pos:10240
[0x9485e88] avi stream debug:      |    + idx1 size:1886176 pos:242660998
[0x9485e88] avi stream debug:      + JUNK size:394 pos:244547182
[0x94860a8] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED 
[0x94860a8] avi demux debug: stream[0] rate:25 scale:1 samplesize:0
[0x94860a8] avi demux debug: stream[0] video(XVID) 512x384 12bpp 25.000000fps
[0xb7401ee8] main input debug: selecting program id=0
[0x94860a8] avi demux debug: stream[1] rate:48000 scale:1152 samplesize:0
[0x94860a8] avi demux debug: stream[1] audio(0x55) 2 channels 48000Hz 0bits
[0x94860a8] avi demux debug: stream[0] created 44251 index entries
[0x94860a8] avi demux debug: stream[1] created 73635 index entries
[0x94860a8] avi demux debug: stream[0] length:1770 (based on index)
[0x94860a8] avi demux debug: stream[1] length:1767 (based on index)
[0x94860a8] main demux debug: using demux module "avi"
[0x94860a8] main demux debug: TIMER module_need() : 28.717 ms - Total 28.717 ms / 1 intvls (Avg 28.717 ms)
[0xb7401ee8] main input debug: looking for a subtitle file in /media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/
[0xb7403c88] main decoder debug: looking for decoder module: 29 candidates
[0xb7403c88] main decoder debug: TIMER module_need() : 6.096 ms - Total 6.096 ms / 1 intvls (Avg 6.096 ms)
[0xb7403c88] main decoder error: no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.
[0xb7403c88] main decoder debug: killing decoder fourcc `XVID', 0 PES in FIFO
[0x9498d20] main decoder debug: looking for decoder module: 29 candidates
[0x9498d20] main decoder debug: TIMER module_need() : 0.338 ms - Total 0.338 ms / 1 intvls (Avg 0.338 ms)
[0x9498d20] main decoder error: no suitable decoder module for fourcc `mpga'.
VLC probably does not support this sound or video format.
[0x9498d20] main decoder debug: killing decoder fourcc `mpga', 0 PES in FIFO
[0xb7401ee8] main input debug: `/media/Data/Movies/Yes (Prime) Minister/Yes Prime Minister Series 1/Yes Prime Minister Series 1 Episode 4 - The Key.avi' successfully opened
[0x924ae10] qt4 interface debug: Updating the geometry
[0x924ae10] qt4 interface debug: Updating the geometry
[0x924ae10] qt4 interface debug: Updating the geometry
[0x924ae10] qt4 interface debug: Updating the geometry
[0x924ae10] qt4 interface debug: Updating the geometry
[0x924ae10] qt4 interface debug: Updating the geometry
[0xb7401ee8] main input debug: EOF reached
[0x9485e88] avi stream debug: free chunk avih
[0x9485e88] avi stream debug: free chunk strh
[0x9485e88] avi stream debug: free chunk strf
[0x9485e88] avi stream debug: free chunk JUNK
[0x9485e88] avi stream debug: free chunk LIST
[0x9485e88] avi stream debug: free chunk strh
[0x9485e88] avi stream debug: free chunk strf
[0x9485e88] avi stream debug: free chunk JUNK
[0x9485e88] avi stream debug: free chunk LIST
[0x9485e88] avi stream warning: unknown chunk (not unloaded)
[0x9485e88] avi stream debug: free chunk LIST
[0x9485e88] avi stream debug: free chunk LIST
[0x9485e88] avi stream debug: free chunk ISFT
[0x9485e88] avi stream warning: unknown chunk (not unloaded)
[0x9485e88] avi stream debug: free chunk LIST
[0x9485e88] avi stream debug: free chunk JUNK
[0x9485e88] avi stream debug: free chunk LIST
[0x9485e88] avi stream debug: free chunk idx1
[0x9485e88] avi stream debug: free chunk RIFF
[0x9485e88] avi stream debug: free chunk JUNK
[0x9485e88] avi stream debug: free chunk LIST
[0x94860a8] main demux debug: removing module "avi"
[0x9485e88] main stream debug: removing module "stream_filter_record"
[0x9484e50] main access debug: removing module "access_file"
[0xb7401ee8] main input debug: Program doesn't contain anymore ES
[0xb7401ee8] main input debug: thread ended
[0x923cde8] main playlist debug: dead input
[0x923cde8] main playlist debug: changing item without a request (current 0/1)
[0x923cde8] main playlist debug: nothing to play
[0x924ae10] qt4 interface debug: IM: Deleting the input
[0x924ae10] qt4 interface debug: Updating the geometry
[0x924ae10] qt4 interface debug: Updating the geometry
[0xb7401ee8] main input debug: TIMER input launching for 'Yes Prime Minister Series 1 Episode 4 - The Key.avi' : 55.015 ms - Total 55.015 ms / 1 intvls (Avg 55.015 ms)
[0x91ad140] main libvlc debug: deactivating the playlist
[0x923cde8] main playlist debug: Deactivate
[0x923cde8] main playlist debug: saving Media Library to file /home/viktor/.local/share/vlc/ml.xspf
[0x923cde8] main playlist debug: looking for playlist export module: 1 candidate
[0x923cde8] main playlist debug: using playlist export module "export"
[0x923cde8] main playlist debug: TIMER module_need() : 0.619 ms - Total 0.619 ms / 1 intvls (Avg 0.619 ms)
[0x923cde8] main playlist debug: removing module "export"
[0x923cde8] main playlist debug: Deactivated
[0x91ad140] main libvlc debug: removing all services discovery tasks
[0x91ad140] main libvlc debug: removing all interfaces
[0x924ae10] qt4 interface debug: Quitting the Qt4 Interface
[0x924ae10] qt4 interface debug: destroying the main Qt4 interface
[0x924ae10] qt4 interface debug: Destroying the main interface
[0x924ae10] main interface debug: removing module "qt4"
[0x91ad2d8] main interface debug: removing module "signals"
[0x9246218] main interface debug: removing module "screensaver"
[0x923e310] main interface debug: removing module "inhibit"
[0x92413f0] main interface debug: removing module "hotkeys"
[0x91ad140] main libvlc debug: removing playlist
[0x923cde8] main playlist debug: Destroyed
[0x91ad140] main libvlc debug: TIMER ML Load : Total 5.576 ms / 1 intvls (Avg 5.576 ms)
[0x91ad140] main libvlc debug: TIMER Items array build : Total 0.086 ms / 2 intvls (Avg 0.043 ms)
[0x91ad140] main libvlc debug: TIMER ML Dump : Total 0.885 ms / 1 intvls (Avg 0.885 ms)
[0x91ad140] main libvlc debug: removing stats
[0x91ad140] main libvlc debug: removing module "memcpymmxext"
[0x91ad140] main libvlc debug: opening config file (/home/viktor/.config/vlc/vlcrc)
[0x91ad140] main libvlc debug: writing plugins cache /home/viktor/.cache/vlc/plugins-04041e.dat

```[/LEFT]

---

### Post by mc4man on 2009-12-18
This means that vlc isn't going to play virtually anything, the reason why the modules are borked is a bit unclear from what you've posted
> 
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so' (/usr/lib/libmad.so.0: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so' (/usr/lib/liba52-0.7.4.so: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/access/libdvdread_plugin.so' (/usr/lib/libdvdread.so.4: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/access/libdvdnav_plugin.so' (/usr/lib/libdvdnav.so.4: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libschroedinger_plugin.so' (/usr/lib/libschroedinger-1.0.so.0: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so' (/usr/lib/libgsm.so.1: file too short)
[0x91ad140] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (/usr/lib/libgsm.so.1: file too short)


I'd search vlc in synaptic and like you did with ffmpeg remove everything installed starting with libvlc and ending with any of the plugins. (5-6+

After removing then in terminal
```
sudo apt-get update && sudo apt-get install vlc
```

Then start vlc the first time as such

```
vlc --reset-config --reset-plugins-cache
```

Edit: this may have been a better com. to use after completely removing vlc (forces vlc to be downloaded rather than retrieving from apt archives

```
sudo apt-get clean && sudo apt-get update && sudo apt-get install vlc
```

---

### Post by viktorzk on 2009-12-18
Packages starting with libvlc: Installed: libvlccore2, libvlc2; Not installed: libvlc-dev,libvlccore-dev;
Installed packages starting with vlc: vlc, vlc-nox, vlc-data, vlc-plugin-pulse, libvlccore2, libvlc2, libvcdinfo0

Reloading in Synaptic doesn't produce more results.

Still the same errors after following the instructions. (That was before you edited them) (Same errors after following the new instructions)

---

### Post by mc4man on 2009-12-18
Maybe take a look at the libs mentioned, search them out in synaptic and mark them for re-install.
( if you remove libgsm you'll need to start over as far as plugins, ffmpeg libs, vlc ect. - may not be the worst thing to just remove them all

The libs mentioned
libgsm
libmad
libschroedinger
libdvdnav
libdvdread
liba52


Edit: Quote from error info page
> error = file too short
 comes from libc's shared object loading code.  It tries to read some
header object from the file.  If read() returns fewer bytes than the
size of the header, that's the message it prints.  ..............
your file(s) got truncated or otherwise corrupted.

---

### Post by Extract_Here on 2009-12-18
Gstreamer get it out of add/remove

---

### Post by viktorzk on 2009-12-18
> **mc4man said:**
> Maybe take a look at the libs mentioned, search them out in synaptic and mark them for re-install.
( if you remove libgsm you'll need to start over as far as plugins, ffmpeg libs, vlc ect. - may not be the worst thing to just remove them all

The libs mentioned
libgsm
libmad
libschroedinger
libdvdnav
libdvdread
liba52

This fixed it. Thank you very much for the help!

---

### Post by mc4man on 2009-12-18
You probably missed my last edit - description of the 'error', in case it comes up again, (though I'd never seen it in vlc before

---

