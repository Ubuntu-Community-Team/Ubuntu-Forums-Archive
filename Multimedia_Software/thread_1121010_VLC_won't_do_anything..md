---
title: "VLC won't do anything."
date: 2009-04-09
forum: Multimedia Software
---

### Post by Kristofer Gustafsson on 2009-04-09
Seems like my VLC is a bit sad, I can open the app and all but when i try to open a video file it wont load anything. I can play videos in mplayer tho but everything is strange, its like flashing every 2 secs.. I prefer VLC if it works, but now its dead.. Think I do have the codecs needed.

---

### Post by Meow27 on 2009-04-09
what version of ubuntu are you using?
what version of vlc are you using?
where did you get vlc (online source or ubuntu repository)?

---

### Post by Kristofer Gustafsson on 2009-04-10
ubuntu is 8.10 32 bit
vlc version is 0.9.4
i got it from ubuntu repository

when i start vlc in terminal i get this however. it tells me i configured libvlc? i have no memory of that tho, i did try to configure 0.9.9a but.. libvlc? 

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

```

```
[00000371] main playlist: playlist is empty

```

---

### Post by Meow27 on 2009-04-10
ok since you seem to understand what compiling entails ill ask you to take the hard road and do this:

open up a terminal and type ```
sudo apt-get build-dep vlc
``` this will install all available dependencies

after that, download the latest source code for vlc, extract the contents into a folder you are comfortable using and linking

```
./configure --disable libzvbi
``` if you dont have it, good. if you only use it for vlc, remove it. vlc doesnt work right with it.

assuming the script went well (if you werent told that you were missing something fatal and the !end! of the script, then proceed)
```
make
```

this will take a while it should complete, NOTE: dont place it in a folder with a space, use an underscore instead "a a" vs "a_a"

after you are done, there should be a vlc file in the folder you compiled in, double click on it and run it. if it works, and you want to use it, you can make install, but i suggest that you dont for reasons im not completely sure of, but ur system can get a little messed up. 

so assuming you dont do make install, and you want videos to run on vlc by defualt,right click on the video file, click on the properties, click on the "open with" tab, and add the vlc file to where its located. (its not gonna be in)
after ur done with that, make sure the bullet clovers vlc, 

tada!

hope this helps you

---

### Post by Kristofer Gustafsson on 2009-04-10
Thanks for the help and all but i found out what the problem is.. While I'm not entirely sure why it shouldn't work tho. I'm on a mac, and have an external HDD formated with hfsplus apperently which is a apple filesystem thingy... I compiled vlc as you said and it works but still when i try to open a file it just wont do anything so i tried to move a file to my desktop which is another file system and then it works. I think it's odd but maybe there's some limitations i don't know about when it comes to hfs? I'm able to move the files and then play them but not play them while they are on the external? 

Well.. good thing is that i have the latest vlc now :D

---

### Post by Meow27 on 2009-04-10
edit... nvm i reread the post


you may want to find some other medium to backup the external, then reformat it to ntfs with gparted, so every modern platform would be able to read it. or if you just want a good filesystem, use ext4 or reiserfs.

---

### Post by Kristofer Gustafsson on 2009-04-11
Yep, big thanks for the help tho i learned about "build-dep" i never knew about that command. 

thank you

---

