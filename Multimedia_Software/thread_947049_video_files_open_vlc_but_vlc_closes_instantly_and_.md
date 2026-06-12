---
title: "video files open vlc but vlc closes instantly and nothing plays."
date: 2008-10-13
forum: Multimedia Software
---

### Post by noogs on 2008-10-13
I have looked for this issue and it seems only one person had it and he rebooted and everything was fine. This did not work for me and I continue to only be able to watch videos online. Any help is greatly appreciated I hate not being able to watch my videos. Thanks in advance.

---

### Post by Cybergod on 2008-10-13
> **noogs said:**
> I have looked for this issue and it seems only one person had it and he rebooted and everything was fine. This did not work for me and I continue to only be able to watch videos online. Any help is greatly appreciated I hate not being able to watch my videos. Thanks in advance.

Run VLC from the console that way when it closes you'll see the errors in the console.

---

### Post by noogs on 2008-10-14
Ok I won't know what to do with the information I receive from the console so I will post it here and look for help.

---

### Post by Cybergod on 2008-10-14
> **noogs said:**
> Ok I won't know what to do with the information I receive from the console so I will post it here and look for help.

That's exactly what I wanted you to do.  Please post the output from the console here so we can look at it.

---

### Post by noogs on 2008-10-14
max@max-PC:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

---

### Post by Cybergod on 2008-10-14
> **noogs said:**
> max@max-PC:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

What type of video card do you have?  I've read up a bit on the BadAlloc error and some people suggest different solutions.  Do a google search for "VLC BadAlloc(insufficient resources for operation)".

---

### Post by noogs on 2008-10-14
I have an ATI Technologies inc. Radeon X1650 Pro (rev 9e). I googled what you said but dont see anything that would fix this error. Please help.

**update**
ok so I did some updates and rebooted a couple times and am now using a restricted driver for my video card. So now I can watch videos but the screen flashes black with every frame or so.

---

### Post by noogs on 2008-10-15
Any ideas will help guys i hate having my videos flash black with every frame or so.

---

### Post by noogs on 2008-10-16
Ok I fixed it. It was caused by compiz, I just had to change the video output to X11 and it works fine now thanks for everyone's help.

---

### Post by bloskat on 2008-10-29
thanks for posting noogs, had the same issue, you saved me alot of forum searching (came up on a google search for the same error!)

---

### Post by deejross on 2008-10-30
This did not solve the problem for me. I have tried X11 and XVideo output with the same result. OpenGL and ASCII art works, but OpenGL causes problem and I tried watching in ASCII art but I don't think that's going to cut it :)

---

