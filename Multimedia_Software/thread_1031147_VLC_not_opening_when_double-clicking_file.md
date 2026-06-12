---
title: "VLC not opening when double-clicking file"
date: 2009-01-05
forum: Multimedia Software
---

### Post by scarf on 2009-01-05
i am using version intrepid 8.10 and i have VLC 0.9.4-1ubuntu3 installed.

i have right-clicked on an mp3 file and gone to properties, and told it to open with VLC media player.  now, when i double-click on any mp3 file, nothing appears to happen.  but, i can see in the process list that VLC is running (with the command "vlc /path/to/my_mp3_file.mp3")

if i launch VLC from the main menu then it opens up all right and i can open or drag and drop my mp3 into it and it plays.

i did try to reinstall vlc within synaptic but that hasn't fixed this problem.

---

### Post by bsmith1051 on 2009-01-05
Three things to try:

1st, if you close VLC is there still a 'stuck' copy running in the background?  Go into System > Administration > System Monitor and look for a "vlc" in the Process list.  If it's there, kill it.  Now try again.

2nd, can you open VLC by itself (not via a file association)?  If so, then go into Tools > Preferences and enable/disable Instances > Allow Only One Instance.  Basically, if it's off, try switching it on.

3rd, reset the VLC configuration.  You can do this from the command-line but I usually do it through the GUI.  Open your Places > Home Folder.  Type <CTRL> <H> to show the hidden folders.  Go into the ".config" folder and delete the "vlc" sub-folder.  Now try re-opening VLC.

---

### Post by bsmith1051 on 2009-01-05
_

---

### Post by scarf on 2009-01-05
thanks for all of these options.  i will try them out.

1. when i close vlc, the process disappears.  now there is no vlc process running.  still, if i double-click on a file associated with vlc, it seems to hang.  only way to get vlc open and playing is to first open vlc and then open the file within vlc.


2. yes it will open if i start it from choosing it from the main menu.  i can even type "vlc" on the command line and it will also open.  however, if i type "vlc /path/to/my_mp3_file.mp3" then nothing appears to happen, like when i double-click on a file.  i get the following output, but nothing opens nor starts playing:

```

$ vlc my_mp3_file.mp3 
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.


```

the 'allow one instance' option was off, so i have turned it on.  no vlc processes are currently running.  when i double-click on a file, vlc opens a little more but it is still hanging and not playing.  that is, i can see the outline of the vlc window now, with the vlc icon in the upper left of the window, "VLC Media Player" as the title, and the three buttons in the upper right of the window, but it hasn't been filled in with any of the vlc interface or menus, etc.  kinda just stuck there.  i click on the X in the upper right and nothing happens.  after a few seconds i get a dialog asking if i want to wait or force quit, so i have chosen force quit.


3. no vlc processes are running, and i have deleted the folder as you suggested.  now i have tried double-clicking on a file, and vlc opens and starts playing!  cool!

now i have tried setting the option to use the visualize filter for audio (audio > visualization > visualize filter) and saved and exited and re-tried double-clicking a file, and now vlc is hanging again.

so i opened vlc manually and reset that option back to "default" and closed vlc and tried re-double-clicking another file.  now vlc is opening and playing properly.

so there seems to be a problem with this visualizer filter option and starting vlc with a file argument.  i think i should file a bug report.


update: since there have been no objections, i have filed [bug #318017]( https://bugs.launchpad.net/bugs/318017)

---

### Post by pveurshout on 2009-08-01
> **bsmith1051 said:**
> Three things to try:

1st, (...)

2nd, (...)

3rd, reset the VLC configuration.  You can do this from the command-line but I usually do it through the GUI.  Open your Places > Home Folder.  Type <CTRL> <H> to show the hidden folders.  Go into the ".config" folder and delete the "vlc" sub-folder.  Now try re-opening VLC.

Unlike Scarf, my VLC didn't do anything at all anymore after I (I think) told Ubuntu to open all .m3u-playlist files with VLC. Couldn't get it to work no matter what I tried. I "Completely Removed" 'vlc', 'vlc-nox', 'vlc-data', 'libvlccore0' and 'libvlc2' using Synaptic, but none of this had any effect. However, the solution quoted above did the trick. Thanks! :)

---

