---
title: "VLC crashing on start"
date: 2009-03-20
forum: Multimedia Software
---

### Post by Kenrin on 2009-03-20
I tried installing the 1.0 vlc git from source.  It did not work out for some reason and now my normal VLC from repos is fubared. Here is the termainl output when trying to run it. Please help!  I'm using 8.10


"VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
LibVLC fatal error locking mutex in thread 3082225328 at misc/objects.c:392: 22
 Error message: Invalid argument at:
/usr/lib/libvlccore.so.0(vlc_pthread_fatal+0xb5)[0xb7ed1cc5]
vlc[0x8048d03]
vlc[0x804aff4]
Aborted"

---

### Post by mc4man on 2009-03-20
> I tried installing the 1.0 vlc git from source. It did not work out

How far did you get doing this?, did you actually do an install? (sudo make install

If not try this in a terminal (or try anyway, can't hurt
```
vlc --reset-config
```

---

### Post by Kenrin on 2009-03-21
Yeah I did a make install on it.  Is there some files I can wipe out to fix it?  I've already tried removing VLC numerous times and reinstalling.  Maybe installing VLC from source would work?

i've done the vlc reset config before and just tried again,  it gives the same error messages

---

### Post by mc4man on 2009-03-21
hopefully you didn't delete the vlc 1.0 folder you built from.
If it's still there than cd to it and run 
```
sudo make uninstall
```

If you deleted it then you'll need to track down the files manually. (can be a pita with vlc if you installed to /usr

---

### Post by Kenrin on 2009-03-21
Unfortunately I deleted the directory, but I did manage to compile 1.0.0 successfully (in which it did not play h.264 files for some reason).  Then I proceeded to install and uninstall 1.0.0 then re-do vlc from the repos again,  and it worked! Thanks. :p

---

