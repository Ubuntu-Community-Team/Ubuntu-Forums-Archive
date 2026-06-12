---
title: "dvds stopped working VLC and Totem"
date: 2009-03-02
forum: Multimedia Software
---

### Post by jubop on 2009-03-02
so I'm running Ubuntu on a Lenovo 3000 N100 (in case that helps). I used to be able to play dvd's fine but suddenly it stops working, when I insert the dvd Totem wil automatically open and then shut down right away with no error message, if I try to open it by right clicking and choosing open with movie player then totem will freeze. 
I tried using VLC but it does the same, or it displays an error message that VLC cannot read video title (I can't get the exact message because it displays it for 1 second then shuts down right away).
If I switch into my guest account then Ubuntu says it cannot mount the volume or unmount it if I go to eject but in my user account it can be unmounted.
yes I have all the necessray plugins including css, and as I've said I played dvds before, I even tried playing the same dvd I did before and it's no longer working. I also tried playing an audio CD and it works just fine, so I don't think it's the hardware.

I checked the forums and anything similar seems to have gone unanswered or the solution was downloading the plugins and I verified that all of them were installed just in case. I'm getting really frustrated please help :)

---

### Post by covertops808 on 2009-03-02
I was one of the guys who had the same problem. I first fixed it in VLC only by going into the VLC Preferences, and changing the display output to X11. That fixed VLC but not totem. But than later when I went to add a new user to the system. I came across the USER PRIVILEGES menu that enables or disables what features of the system each user can operate. Things like enable access to webcam, and enable access to DVD/CD. Once I enabled that. That took care of DVD playing for both Totem and VLC. 

Good Luck!

---

### Post by jubop on 2009-03-03
changed the output in vlc to X11 but no change, i'll try and find the preferences for accounts but I can't imagine that being the problem because I used to be able to watch dvds and I haven't changed those settings since. The only changes I've done to the system are the system updates, I downloaded vlc since then but tried uninstalling it and totem still didn't work so i reinstalled it, also installed avast for linux (there was a virus going around on my friends' flash drives and I wanted to check my system).

I don't see how that could cause a problem but I did have it check all drives, so maybe something got messed up???? Any ideas?

---

### Post by jubop on 2009-03-03
i checked the profile prvieleges and i do have acces to cd-rom drive.

Thanks for the help but still stuck with the same problem.

---

### Post by mc4man on 2009-03-03
You may be able to get some useful info by..
start vlc from a terminal with this, try to play dvd and see what shows up

```
vlc -vvv
```

to check on vlc and libdvdcss2 do this from terminal 

```
export DVDCSS_VERBOSE=2
```

followed by

```
vlc > vlc_output 2>&1
```

Once vlc pops up try to play your dvd, then look in home folder for vlc_output file

---

### Post by jubop on 2009-03-03
if i do vlc -vvv n terminal I get this:
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc debug: checking builtin modules
[00000001] main libvlc debug: checking plugin modules
[00000001] main libvlc debug: loading plugins cache file /home/pamela/.cache/vlc/plugins-04041e.dat
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main libvlc debug: module bank initialized, found 272 modules
[00000001] main libvlc debug: opening config file (/home/pamela/.config/vlc/vlcrc)
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000370] main interaction debug: thread started
[00000370] main interaction debug: thread 3081390992 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000372] main input debug: Creating an input for 'Media Library'
[00000372] main input debug: Input is a meta file: disabling unneeded options
[00000372] main input debug: `file/xspf-open:///home/pamela/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/pamela/.local/share/vlc/ml.xspf'
[00000372] main input debug: creating access 'file' path='/home/pamela/.local/share/vlc/ml.xspf'
[00000373] main access debug: looking for access module: 3 candidates
[00000373] access_mmap access debug: opening file /home/pamela/.local/share/vlc/ml.xspf
[00000373] main access debug: using access module "access_mmap"
[00000373] main access debug: TIMER module_Need() : 14.566 ms - Total 14.566 ms / 1 intvls (Avg 14.566 ms)
[00000377] main stream debug: Using AStream*Block
[00000377] main stream debug: pre buffering
[00000377] main stream debug: received first data for our buffer
[00000373] access_mmap access debug: at end of memory mapped file
[00000372] main input debug: creating demux: access='file' demux='xspf-open' path='/home/pamela/.local/share/vlc/ml.xspf'
[00000378] main demux debug: looking for demux module: 1 candidate
[00000378] playlist demux debug: using XSPF playlist reader
[00000378] main demux debug: using demux module "playlist"
[00000378] main demux debug: TIMER module_Need() : 28.672 ms - Total 28.672 ms / 1 intvls (Avg 28.672 ms)
[00000372] main input debug: `file/xspf-open:///home/pamela/.local/share/vlc/ml.xspf' successfully opened
[00000393] main xml debug: looking for xml module: 2 candidates
[00000393] main xml debug: using xml module "xml"
[00000393] main xml debug: TIMER module_Need() : 1.803 ms - Total 1.803 ms / 1 intvls (Avg 1.803 ms)
[00000373] access_mmap access debug: at end of memory mapped file
[00000378] playlist demux warning: invalid <playlist> attribute:"xmlns:vlc"
[00000378] playlist demux debug: parsed 0 tracks successfully
[00000393] main xml debug: removing module "xml"
[00000372] main input debug: EOF reached
[00000372] main input debug: control type=1
[00000378] main demux debug: removing module "playlist"
[00000373] main access debug: removing module "access_mmap"
[00000372] main input debug: TIMER input launching for 'Media Library' : 83.030 ms - Total 83.030 ms / 1 intvls (Avg 83.030 ms)
[00000395] main preparser debug: thread started
[00000395] main preparser debug: waiting for thread initialization
[00000395] main preparser debug: thread 3071441808 (preparser) created at priority 0 (playlist/thread.c:79)
[00000396] main fetcher debug: thread started
[00000396] main fetcher debug: waiting for thread initialization
[00000396] main fetcher debug: thread 3063049104 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000371] main playlist debug: thread started
[00000371] main playlist debug: waiting for thread initialization
[00000371] main playlist debug: rebuilding array of current - root Playlist
[00000371] main playlist debug: rebuild done - 0 items, index -1
[00000371] main playlist debug: thread 3054656400 (playlist) created at priority 0 (playlist/thread.c:117)
[00000397] main interface debug: looking for interface module: 1 candidate
[00000397] main interface debug: using interface module "hotkeys"
[00000397] main interface debug: TIMER module_Need() : 9.798 ms - Total 9.798 ms / 1 intvls (Avg 9.798 ms)
[00000397] main interface debug: thread started
[00000397] main interface debug: thread 3046263696 (interface) created at priority 0 (interface/interface.c:168)
[00000399] main interface debug: looking for interface module: 1 candidate
[00000399] main interface debug: using interface module "inhibit"
[00000399] main interface debug: TIMER module_Need() : 6.019 ms - Total 6.019 ms / 1 intvls (Avg 6.019 ms)
[00000399] main interface debug: thread started
[00000399] main interface debug: thread 3036674960 (interface) created at priority 0 (interface/interface.c:168)
[00000401] main interface debug: looking for interface module: 1 candidate
[00000401] main interface debug: using interface module "screensaver"
[00000401] main interface debug: TIMER module_Need() : 8.224 ms - Total 8.224 ms / 1 intvls (Avg 8.224 ms)
[00000401] main interface debug: thread started
[00000401] main interface debug: thread 3028282256 (interface) created at priority 0 (interface/interface.c:168)
[00000403] main interface debug: looking for interface module: 22 candidates
[00000403] main interface debug: using interface module "signals"
[00000403] main interface debug: TIMER module_Need() : 0.779 ms - Total 0.779 ms / 1 intvls (Avg 0.779 ms)
[00000403] main interface debug: thread started
[00000403] main interface debug: thread 3011496848 (interface) created at priority 0 (interface/interface.c:168)
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000405] main interface debug: looking for interface module: 4 candidates
[00000405] main interface debug: using interface module "qt4"
[00000405] main interface debug: TIMER module_Need() : 473.420 ms - Total 473.420 ms / 1 intvls (Avg 473.420 ms)
[00000405] main interface debug: thread 2984901520 (interface) created at priority 0 (interface/interface.c:168)
[00000405] main interface debug: thread started
[00000405] qt4 interface debug: Error while initializing qt-specific localization

export DVDCSS_VERBOSE=2 followed by vlc > vlc_output 2>&1 and try to play the dvd i get this error message:
Your input can't be opened:
**VLC is unable to open the MRL 'dvd:///dev/scd0'. Check the log for details.**

hope someone find this info useful to help :)

btw just checked my log all it says is MARK for the time when I was trying to open vlc, anyone know what that means?

---

### Post by jubop on 2009-04-29
problem seened to solve itself (maybe updates fixed it).

---

### Post by lonach on 2009-06-19
having the same problem.  Totem and VLC both stopped playing DVDs.  VLC works fine with .avi and other file formats from disk.  anyone have any ideas?

---

