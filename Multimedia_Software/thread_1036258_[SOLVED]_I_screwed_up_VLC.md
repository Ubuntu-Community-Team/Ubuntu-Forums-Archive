---
title: "[SOLVED] I screwed up VLC"
date: 2009-01-10
forum: Multimedia Software
---

### Post by Riverwolf on 2009-01-10
I have a problem that for once I have not been able to find a solution to after trying several ideas on my own, and searching the documentation and forums.  I am a newbie, and have some how made vlc not function totally right.  I was trying out different skins from the videoLan.org site and then I am not sure weather I got a bad download or it was just me that screwed up but I no longer have access to the vlc controls and can not/do not know how to get them back.  Have tried uninstall then reinstal through synaptic, add/remove programs, and terminal, all with the same results.  I get error messages about files missing.  This is the output from the terminal::confused:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libvlc2 libvlccore0 vlc-data vlc-nox
Suggested packages:
  mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libvlc2 libvlccore0 vlc vlc-data vlc-nox
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9816kB of archives.
After this operation, 26.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package vlc-data.
(Reading database ... 146127 files and directories currently installed.)
Unpacking vlc-data (from .../vlc-data_0.9.4-1ubuntu3_all.deb) ...
Selecting previously deselected package libvlccore0.
Unpacking libvlccore0 (from .../libvlccore0_0.9.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package libvlc2.
Unpacking libvlc2 (from .../libvlc2_0.9.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_0.9.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_0.9.4-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up vlc-data (0.9.4-1ubuntu3) ...
Setting up libvlccore0 (0.9.4-1ubuntu3) ...

Setting up libvlc2 (0.9.4-1ubuntu3) ...

Setting up vlc-nox (0.9.4-1ubuntu3) ...
Setting up vlc (0.9.4-1ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
riverwolf@riverwolf-desktop:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000405] skins2 interface: skin: Winamp2  author: See README.txt in the skin file
[00000405] skins2 interface error: Failed to open INI file /usr/share/vlc/skins2/pledit.txt
[00000418] access_directory access error: /usr/share/vlc/skins2/main.bmp: No such file or directory
[00000418] access_file access error: cannot open file /usr/share/vlc/skins2/main.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/main.bmp'
[00000421] access_directory access error: /usr/share/vlc/skins2/cbuttons.bmp: No such file or directory
[00000421] access_file access error: cannot open file /usr/share/vlc/skins2/cbuttons.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/cbuttons.bmp'
[00000422] access_directory access error: /usr/share/vlc/skins2/eqmain.bmp: No such file or directory
[00000422] access_file access error: cannot open file /usr/share/vlc/skins2/eqmain.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/eqmain.bmp'
[00000423] access_directory access error: /usr/share/vlc/skins2/eq_ex.bmp: No such file or directory
[00000423] access_file access error: cannot open file /usr/share/vlc/skins2/eq_ex.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/eq_ex.bmp'
[00000424] access_directory access error: /usr/share/vlc/skins2/pledit.bmp: No such file or directory
[00000424] access_file access error: cannot open file /usr/share/vlc/skins2/pledit.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/pledit.bmp'
[00000425] access_directory access error: /usr/share/vlc/skins2/playpaus.bmp: No such file or directory
[00000425] access_file access error: cannot open file /usr/share/vlc/skins2/playpaus.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/playpaus.bmp'
[00000426] access_directory access error: /usr/share/vlc/skins2/posbar.bmp: No such file or directory
[00000426] access_file access error: cannot open file /usr/share/vlc/skins2/posbar.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/posbar.bmp'
[00000427] access_directory access error: /usr/share/vlc/skins2/titlebar.bmp: No such file or directory
[00000427] access_file access error: cannot open file /usr/share/vlc/skins2/titlebar.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/titlebar.bmp'
[00000428] access_directory access error: /usr/share/vlc/skins2/shufrep.bmp: No such file or directory
[00000428] access_file access error: cannot open file /usr/share/vlc/skins2/shufrep.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/shufrep.bmp'
[00000429] access_directory access error: /usr/share/vlc/skins2/volume.bmp: No such file or directory
[00000429] access_file access error: cannot open file /usr/share/vlc/skins2/volume.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/volume.bmp'
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: cbuttons
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eqmain
[00000405] skins2 interface error: unknown bitmap id: eq_ex
[00000405] skins2 interface error: unknown bitmap id: eq_ex
[00000405] skins2 interface error: unknown bitmap id: eq_ex
[00000405] skins2 interface error: unknown bitmap id: eq_ex
[00000405] skins2 interface error: unknown bitmap id: eq_ex
[00000405] skins2 interface error: unknown bitmap id: eq_ex
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: pledit
[00000405] skins2 interface error: unknown bitmap id: playpaus
[00000405] skins2 interface error: unknown bitmap id: playpaus
[00000405] skins2 interface error: unknown bitmap id: playpaus
[00000405] skins2 interface error: unknown bitmap id: posbar
[00000405] skins2 interface error: unknown bitmap id: posbar
[00000405] skins2 interface error: unknown bitmap id: posbar
[00000405] skins2 interface error: unknown bitmap id: posbar
[00000405] skins2 interface error: unknown bitmap id: posbar
[00000405] skins2 interface error: unknown bitmap id: posbar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: titlebar
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: shufrep
[00000405] skins2 interface error: unknown bitmap id: volume
[00000405] skins2 interface error: unknown bitmap id: volume
[00000405] skins2 interface error: unknown bitmap id: volume
[00000405] skins2 interface error: unknown bitmap id: volume
[00000430] access_directory access error: /usr/share/vlc/skins2/nums_ex.bmp: No such file or directory
[00000430] access_file access error: cannot open file /usr/share/vlc/skins2/nums_ex.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/nums_ex.bmp'
[00000431] access_directory access error: /usr/share/vlc/skins2/numbers.bmp: No such file or directory
[00000431] access_file access error: cannot open file /usr/share/vlc/skins2/numbers.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/numbers.bmp'
[00000432] access_directory access error: /usr/share/vlc/skins2/text.bmp: No such file or directory
[00000432] access_file access error: cannot open file /usr/share/vlc/skins2/text.bmp (No such file or directory)
[00000405] main interface error: no suitable access module for `/usr/share/vlc/skins2/text.bmp'
[00000405] skins2 interface error: unknown bitmap id: menu_up
[00000405] skins2 interface error: unknown bitmap id: small_previous
[00000405] skins2 interface error: unknown bitmap id: small_play
[00000405] skins2 interface error: unknown bitmap id: small_pause
[00000405] skins2 interface error: unknown bitmap id: small_stop
[00000405] skins2 interface error: unknown bitmap id: small_forward
[00000405] skins2 interface error: unknown bitmap id: small_eject
[00000405] skins2 interface error: unknown bitmap id: minimize_up
[00000405] skins2 interface error: unknown bitmap id: switch_up
[00000405] skins2 interface error: unknown bitmap id: quit_up
[00000405] skins2 interface error: unknown bitmap id: menu_up
[00000405] skins2 interface error: unknown bitmap id: minimize_up
[00000405] skins2 interface error: unknown bitmap id: switch_up
[00000405] skins2 interface error: unknown bitmap id: quit_up
[00000405] skins2 interface error: unknown bitmap id: previous_up
[00000405] skins2 interface error: unknown bitmap id: play_up
[00000405] skins2 interface error: unknown bitmap id: pause_up
[00000405] skins2 interface error: unknown bitmap id: stop_up
[00000405] skins2 interface error: unknown bitmap id: next_up
[00000405] skins2 interface error: unknown bitmap id: eject_up
[00000405] skins2 interface error: unknown bitmap id: eq_small_switch_up
[00000405] skins2 interface error: unknown bitmap id: eq_small_close_up
[00000405] skins2 interface error: unknown bitmap id: eq_switch_up
[00000405] skins2 interface error: unknown bitmap id: eq_close_up
[00000405] skins2 interface error: unknown bitmap id: pl_small_switch_up
[00000405] skins2 interface error: unknown bitmap id: pl_small_close_up
[00000405] skins2 interface error: unknown bitmap id: pl_switch_up
[00000405] skins2 interface error: unknown bitmap id: pl_close_up
[00000405] skins2 interface error: unknown bitmap id: pl_add_up
[00000405] skins2 interface error: unknown bitmap id: pl_sub_up
[00000405] skins2 interface error: unknown bitmap id: pl_previous
[00000405] skins2 interface error: unknown bitmap id: pl_play
[00000405] skins2 interface error: unknown bitmap id: pl_pause
[00000405] skins2 interface error: unknown bitmap id: pl_stop
[00000405] skins2 interface error: unknown bitmap id: pl_forward
[00000405] skins2 interface error: unknown bitmap id: pl_eject
[00000405] skins2 interface error: unknown bitmap id: dot2_up
[00000405] skins2 interface error: unknown bitmap id: noshuffle_up
[00000405] skins2 interface error: unknown bitmap id: noloop_up
[00000405] skins2 interface error: unknown bitmap id: eqoff_up
[00000405] skins2 interface error: unknown bitmap id: ploff_up
[00000405] skins2 interface error: unknown bitmap id: eq_notok_up
[00000405] skins2 interface error: unknown bitmap id: small_focus
[00000405] skins2 interface error: unknown bitmap id: small_time_bg
[00000405] skins2 interface error: unknown bitmap id: main
[00000405] skins2 interface error: unknown bitmap id: five_dots
[00000405] skins2 interface error: unknown bitmap id: play_icon
[00000405] skins2 interface error: unknown bitmap id: pause_icon
[00000405] skins2 interface error: unknown bitmap id: stop_icon
[00000405] skins2 interface error: unknown bitmap id: title_focus
[00000405] skins2 interface error: unknown bitmap id: time_bg
[00000405] skins2 interface error: unknown bitmap id: eq_small_focus
[00000405] skins2 interface error: unknown bitmap id: eq_bg
[00000405] skins2 interface error: unknown bitmap id: eq_title_focus
[00000405] skins2 interface error: unknown bitmap id: eq_grid
[00000405] skins2 interface error: unknown bitmap id: pl_small_left
[00000405] skins2 interface error: unknown bitmap id: pl_small_middle
[00000405] skins2 interface error: unknown bitmap id: pl_small_middle
[00000405] skins2 interface error: unknown bitmap id: pl_small_middle
[00000405] skins2 interface error: unknown bitmap id: pl_small_middle
[00000405] skins2 interface error: unknown bitmap id: pl_small_middle
[00000405] skins2 interface error: unknown bitmap id: pl_small_middle
[00000405] skins2 interface error: unknown bitmap id: pl_small_middle
[00000405] skins2 interface error: unknown bitmap id: pl_small_middle
[00000405] skins2 interface error: unknown bitmap id: pl_small_right_focus
[00000405] skins2 interface error: unknown bitmap id: pl_small_resize
[00000405] skins2 interface error: unknown bitmap id: pl_upleft_focus
[00000405] skins2 interface error: unknown bitmap id: pl_up_focus
[00000405] skins2 interface error: unknown bitmap id: pl_up_focus
[00000405] skins2 interface error: unknown bitmap id: pl_up_focus
[00000405] skins2 interface error: unknown bitmap id: pl_title_focus
[00000405] skins2 interface error: unknown bitmap id: pl_up_focus
[00000405] skins2 interface error: unknown bitmap id: pl_up_focus
[00000405] skins2 interface error: unknown bitmap id: pl_up_focus
[00000405] skins2 interface error: unknown bitmap id: pl_upright_focus
[00000405] skins2 interface error: unknown bitmap id: pl_left
[00000405] skins2 interface error: unknown bitmap id: pl_right
[00000405] skins2 interface error: unknown bitmap id: pl_left
[00000405] skins2 interface error: unknown bitmap id: pl_right
[00000405] skins2 interface error: unknown bitmap id: pl_down1
[00000405] skins2 interface error: unknown bitmap id: pl_down2
[00000405] skins2 interface error: unknown bitmap id: pl_downleft
[00000405] skins2 interface error: unknown bitmap id: pl_downright
[00000405] skins2 interface error: unknown bitmap id: pl_resize
[00000405] skins2 interface error: unknown font id: text_font
[00000405] skins2 interface error: unknown font id: digits_font;digits_font_2
[00000405] skins2 interface error: unknown font id: text_font
[00000405] skins2 interface error: unknown font id: text_font
[00000405] skins2 interface error: unknown font id: text_font
[00000405] skins2 interface error: unknown font id: text_font
[00000405] skins2 interface error: unknown font id: text_font
[00000405] skins2 interface error: unknown bitmap id: small_time_cursor_up
[00000405] skins2 interface error: unknown bitmap id: volume_bg;volume_bg_2
[00000405] skins2 interface error: unknown bitmap id: time_up;time_up_2
[00000405] skins2 interface error: unknown bitmap id: eq_small_volume_up
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: eq_slider_bg
[00000405] skins2 interface error: unknown bitmap id: pl_slider_up
: Fatal IO error: client killed

:confused:I know it is long, but I wanted to ensure I included everything I had so far.  Please, if you have any ideas on what I need to do, I would be grateful.

---

### Post by mc4man on 2009-01-10
In a terminal (will return to default install
```
vlc --reset
```

---

### Post by Riverwolf on 2009-01-11
Thank You mc4man.  That got it straighten out.

---

### Post by gobberpooper on 2009-09-12
> **mc4man said:**
> In a terminal (will return to default install
```
vlc --reset
```
omg omg omg omg omg THANK YOU SO MUCH!!!
I kept messing around with the interfaces and there was some really bad combination with the QT Interface apparently which made VLC either run and not play anything, play but then close down immediately, or play with no interface. I thought I absolutely fubared it since reinstallation of everything associated with VLC and restarting my computer didn't work.

---

