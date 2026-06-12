---
title: "Internet DJ Console - Problems with configure"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by Josh1 on 2007-01-09
Hello All!

I have decided to try [Internet DJ Console]("http://www.onlymeok.nildram.co.uk/download.html"), it looks amazing!

So I download the latest version, unextract it, change into the directory, type "./configure" and this comes up:
```

josh@JOSH:~/Desktop/idjc-0.6.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... configure: error: newly created file is older than distributed files!
Check your system clock

```

Any ideas? I am really stuck! Time is correct as well..

---

### Post by Josh1 on 2007-01-09
Here is the entire log:
```

josh@JOSH:~/Desktop$ tar xzvf idjc-0.6.9_pre4.tar.gz
idjc-0.6.9_pre4/
idjc-0.6.9_pre4/doc/
idjc-0.6.9_pre4/doc/ChangeLog.html
tar: idjc-0.6.9_pre4/doc/ChangeLog.html: time stamp 2007-01-08 17:45:42 is 31535001.163675 s in the future
idjc-0.6.9_pre4/doc/download.html
tar: idjc-0.6.9_pre4/doc/download.html: time stamp 2007-01-08 17:45:42 is 31535001.162363 s in the future
idjc-0.6.9_pre4/doc/index.html
tar: idjc-0.6.9_pre4/doc/index.html: time stamp 2007-01-08 17:45:42 is 31535001.161743 s in the future
idjc-0.6.9_pre4/doc/jingles.html
tar: idjc-0.6.9_pre4/doc/jingles.html: time stamp 2007-01-08 17:45:42 is 31535001.161386 s in the future
idjc-0.6.9_pre4/doc/prefs.html
tar: idjc-0.6.9_pre4/doc/prefs.html: time stamp 2007-01-08 17:45:42 is 31535001.160958 s in the future
idjc-0.6.9_pre4/doc/realtime.html
tar: idjc-0.6.9_pre4/doc/realtime.html: time stamp 2007-01-08 17:45:42 is 31535001.160266 s in the future
idjc-0.6.9_pre4/doc/server.html
tar: idjc-0.6.9_pre4/doc/server.html: time stamp 2007-01-08 17:45:42 is 31535001.159199 s in the future
idjc-0.6.9_pre4/doc/voip.html
tar: idjc-0.6.9_pre4/doc/voip.html: time stamp 2007-01-08 17:45:42 is 31535001.158294 s in the future
idjc-0.6.9_pre4/doc/favicon.png.jpg
tar: idjc-0.6.9_pre4/doc/favicon.png.jpg: time stamp 2007-01-08 17:45:41 is 31535000.157426 s in the future
idjc-0.6.9_pre4/doc/icon.jpg
tar: idjc-0.6.9_pre4/doc/icon.jpg: time stamp 2007-01-08 17:45:40 is 31534999.156576 s in the future
idjc-0.6.9_pre4/doc/idjc-jack.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-jack.png.jpg: time stamp 2007-01-08 17:45:41 is 31535000.147037 s in the future
idjc-0.6.9_pre4/doc/idjc-jingleswindow.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-jingleswindow.png.jpg: time stamp 2007-01-08 17:45:40 is 31534999.14601 s in the future
idjc-0.6.9_pre4/doc/idjc-mainwindow.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-mainwindow.png.jpg: time stamp 2007-01-08 17:45:41 is 31535000.14366 s in the future
idjc-0.6.9_pre4/doc/idjc-mainwindow1.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-mainwindow1.png.jpg: time stamp 2007-01-08 17:45:42 is 31535001.141464 s in the future
idjc-0.6.9_pre4/doc/idjc-prefsgeneral.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-prefsgeneral.png.jpg: time stamp 2007-01-08 17:45:41 is 31535000.13913 s in the future
idjc-0.6.9_pre4/doc/idjc-prefsgeneral1.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-prefsgeneral1.png.jpg: time stamp 2007-01-08 17:45:42 is 31535001.13807 s in the future
idjc-0.6.9_pre4/doc/idjc-prefsmicrophone1.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-prefsmicrophone1.png.jpg: time stamp 2007-01-08 17:45:41 is 31535000.112136 s in the future
idjc-0.6.9_pre4/doc/idjc-prefsmicrophone2.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-prefsmicrophone2.png.jpg: time stamp 2007-01-08 17:45:41 is 31535000.110751 s in the future
idjc-0.6.9_pre4/doc/idjc-serverwindow.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-serverwindow.png.jpg: time stamp 2007-01-08 17:45:41 is 31535000.108726 s in the future
idjc-0.6.9_pre4/doc/idjc-xchat.png.jpg
tar: idjc-0.6.9_pre4/doc/idjc-xchat.png.jpg: time stamp 2007-01-08 17:45:41 is 31535000.10662 s in the future
idjc-0.6.9_pre4/doc/killerlogo.jpg
tar: idjc-0.6.9_pre4/doc/killerlogo.jpg: time stamp 2007-01-08 17:45:40 is 31534999.105565 s in the future
idjc-0.6.9_pre4/doc/style.css
tar: idjc-0.6.9_pre4/doc/style.css: time stamp 2007-01-08 17:45:40 is 31534999.087169 s in the future
idjc-0.6.9_pre4/README
tar: idjc-0.6.9_pre4/doc: time stamp 2007-01-08 17:45:42 is 31535001.086499 s in the future
tar: idjc-0.6.9_pre4/README: time stamp 2006-09-12 12:02:45 is 21319224.085824 s in the future
idjc-0.6.9_pre4/configure.in
tar: idjc-0.6.9_pre4/configure.in: time stamp 2007-01-08 16:36:39 is 31530858.084975 s in the future
idjc-0.6.9_pre4/aclocal.m4
tar: idjc-0.6.9_pre4/aclocal.m4: time stamp 2007-01-08 17:45:11 is 31534970.082057 s in the future
idjc-0.6.9_pre4/idjc.desktop_
tar: idjc-0.6.9_pre4/idjc.desktop_: time stamp 2006-09-10 23:03:48 is 21186087.081177 s in the future
idjc-0.6.9_pre4/idjc_
tar: idjc-0.6.9_pre4/idjc_: time stamp 2007-01-02 03:09:23 is 30964022.064187 s in the future
idjc-0.6.9_pre4/idjcskype_
idjc-0.6.9_pre4/Makefile.am
tar: idjc-0.6.9_pre4/Makefile.am: time stamp 2007-01-02 01:59:13 is 30959812.062834 s in the future
idjc-0.6.9_pre4/Makefile.in
tar: idjc-0.6.9_pre4/Makefile.in: time stamp 2007-01-08 17:45:14 is 31534973.061105 s in the future
idjc-0.6.9_pre4/config.h.in
tar: idjc-0.6.9_pre4/config.h.in: time stamp 2007-01-08 17:45:22 is 31534981.060182 s in the future
idjc-0.6.9_pre4/configure
tar: idjc-0.6.9_pre4/configure: time stamp 2007-01-08 17:45:14 is 31534973.034987 s in the future
idjc-0.6.9_pre4/AUTHORS
tar: idjc-0.6.9_pre4/AUTHORS: time stamp 2006-09-09 12:54:53 is 21063152.034079 s in the future
idjc-0.6.9_pre4/COPYING
idjc-0.6.9_pre4/ChangeLog
tar: idjc-0.6.9_pre4/ChangeLog: time stamp 2007-01-08 16:44:59 is 31531358.031414 s in the future
idjc-0.6.9_pre4/INSTALL
tar: idjc-0.6.9_pre4/INSTALL: time stamp 2006-09-03 21:04:15 is 20574114.014312 s in the future
idjc-0.6.9_pre4/NEWS
tar: idjc-0.6.9_pre4/NEWS: time stamp 2006-09-08 15:56:56 is 20987675.013428 s in the future
idjc-0.6.9_pre4/compile
tar: idjc-0.6.9_pre4/compile: time stamp 2006-09-03 21:04:15 is 20574114.012538 s in the future
idjc-0.6.9_pre4/depcomp
tar: idjc-0.6.9_pre4/depcomp: time stamp 2006-09-03 21:04:15 is 20574114.011388 s in the future
idjc-0.6.9_pre4/install-sh
tar: idjc-0.6.9_pre4/install-sh: time stamp 2006-09-03 21:04:15 is 20574114.009675 s in the future
idjc-0.6.9_pre4/missing
tar: idjc-0.6.9_pre4/missing: time stamp 2006-09-03 21:04:15 is 20574114.008718 s in the future
idjc-0.6.9_pre4/py-compile
tar: idjc-0.6.9_pre4/py-compile: time stamp 2006-09-03 21:04:15 is 20574114.007473 s in the future
idjc-0.6.9_pre4/c/
idjc-0.6.9_pre4/c/Makefile.am
tar: idjc-0.6.9_pre4/c/Makefile.am: time stamp 2007-01-07 21:55:20 is 31463578.991334 s in the future
idjc-0.6.9_pre4/c/Makefile.in
tar: idjc-0.6.9_pre4/c/Makefile.in: time stamp 2007-01-08 17:45:13 is 31534971.989049 s in the future
idjc-0.6.9_pre4/c/idjcmixer.c
tar: idjc-0.6.9_pre4/c/idjcmixer.c: time stamp 2007-01-06 23:10:20 is 31381678.985527 s in the future
idjc-0.6.9_pre4/c/kvpdict.c
tar: idjc-0.6.9_pre4/c/kvpdict.c: time stamp 2007-01-06 23:10:20 is 31381678.984644 s in the future
idjc-0.6.9_pre4/c/kvpparse.c
tar: idjc-0.6.9_pre4/c/kvpparse.c: time stamp 2007-01-06 23:10:20 is 31381678.983633 s in the future
idjc-0.6.9_pre4/c/dsp.c
tar: idjc-0.6.9_pre4/c/dsp.c: time stamp 2007-01-06 23:10:20 is 31381678.96825 s in the future
idjc-0.6.9_pre4/c/kvpdict.h
tar: idjc-0.6.9_pre4/c/kvpdict.h: time stamp 2006-09-23 04:57:30 is 22244108.967336 s in the future
idjc-0.6.9_pre4/c/kvpparse.h
tar: idjc-0.6.9_pre4/c/kvpparse.h: time stamp 2006-09-23 04:57:30 is 22244108.966472 s in the future
idjc-0.6.9_pre4/c/dsp.h
tar: idjc-0.6.9_pre4/c/dsp.h: time stamp 2006-09-23 04:57:30 is 22244108.965604 s in the future
idjc-0.6.9_pre4/c/compressor.c
tar: idjc-0.6.9_pre4/c/compressor.c: time stamp 2007-01-06 23:10:20 is 31381678.964681 s in the future
idjc-0.6.9_pre4/c/compressor.h
tar: idjc-0.6.9_pre4/c/compressor.h: time stamp 2006-09-23 04:57:30 is 22244108.96365 s in the future
idjc-0.6.9_pre4/c/noisegate.c
tar: idjc-0.6.9_pre4/c/noisegate.c: time stamp 2007-01-06 23:10:20 is 31381678.962791 s in the future
idjc-0.6.9_pre4/c/noisegate.h
tar: idjc-0.6.9_pre4/c/noisegate.h: time stamp 2006-09-23 04:57:30 is 22244108.961209 s in the future
idjc-0.6.9_pre4/c/dbconvert.c
tar: idjc-0.6.9_pre4/c/dbconvert.c: time stamp 2007-01-06 23:10:20 is 31381678.960343 s in the future
idjc-0.6.9_pre4/c/dbconvert.h
tar: idjc-0.6.9_pre4/c/dbconvert.h: time stamp 2006-09-23 04:57:30 is 22244108.959284 s in the future
idjc-0.6.9_pre4/c/ialloc.c
tar: idjc-0.6.9_pre4/c/ialloc.c: time stamp 2007-01-06 23:10:20 is 31381678.943218 s in the future
idjc-0.6.9_pre4/c/ialloc.h
tar: idjc-0.6.9_pre4/c/ialloc.h: time stamp 2006-09-23 04:57:30 is 22244108.942344 s in the future
idjc-0.6.9_pre4/c/vorbinfo.c
tar: idjc-0.6.9_pre4/c/vorbinfo.c: time stamp 2007-01-06 23:10:20 is 31381678.94146 s in the future
idjc-0.6.9_pre4/c/vorbinfo.h
tar: idjc-0.6.9_pre4/c/vorbinfo.h: time stamp 2006-09-23 04:57:30 is 22244108.940603 s in the future
idjc-0.6.9_pre4/c/xlplayer.c
tar: idjc-0.6.9_pre4/c/xlplayer.c: time stamp 2007-01-08 16:34:35 is 31530733.938496 s in the future
idjc-0.6.9_pre4/c/xlplayer.h
tar: idjc-0.6.9_pre4/c/xlplayer.h: time stamp 2007-01-07 21:12:34 is 31461012.936965 s in the future
idjc-0.6.9_pre4/c/askxine.c
tar: idjc-0.6.9_pre4/c/askxine.c: time stamp 2007-01-06 23:10:20 is 31381678.936099 s in the future
idjc-0.6.9_pre4/c/askxine.h
tar: idjc-0.6.9_pre4/c/askxine.h: time stamp 2006-09-23 04:57:30 is 22244108.935072 s in the future
idjc-0.6.9_pre4/c/mp4tag.c
tar: idjc-0.6.9_pre4/c/mp4tag.c: time stamp 2007-01-06 23:10:20 is 31381678.91884 s in the future
idjc-0.6.9_pre4/c/mp4tag.h
tar: idjc-0.6.9_pre4/c/mp4tag.h: time stamp 2006-09-23 04:57:30 is 22244108.91794 s in the future
idjc-0.6.9_pre4/c/rms_calc.c
tar: idjc-0.6.9_pre4/c/rms_calc.c: time stamp 2007-01-06 23:10:20 is 31381678.917082 s in the future
idjc-0.6.9_pre4/c/rms_calc.h
tar: idjc-0.6.9_pre4/c/rms_calc.h: time stamp 2006-09-23 04:57:30 is 22244108.916171 s in the future
idjc-0.6.9_pre4/c/idjcserver.c
tar: idjc-0.6.9_pre4/c/idjcserver.c: time stamp 2007-01-06 23:10:20 is 31381678.913532 s in the future
idjc-0.6.9_pre4/c/metaqueue.c
tar: idjc-0.6.9_pre4/c/metaqueue.c: time stamp 2007-01-06 23:10:20 is 31381678.912617 s in the future
idjc-0.6.9_pre4/c/metaqueue.h
tar: idjc-0.6.9_pre4/c/metaqueue.h: time stamp 2006-09-23 04:57:30 is 22244108.911614 s in the future
idjc-0.6.9_pre4/idjcpython/
tar: idjc-0.6.9_pre4/c: time stamp 2007-01-08 17:45:42 is 31535000.910951 s in the future
idjc-0.6.9_pre4/idjcpython/idjc-announce.py
tar: idjc-0.6.9_pre4/idjcpython/idjc-announce.py: time stamp 2006-11-27 19:10:26 is 27911284.91006 s in the future
idjc-0.6.9_pre4/idjcpython/IDJCfree.py
tar: idjc-0.6.9_pre4/idjcpython/IDJCfree.py: time stamp 2006-06-29 11:21:15 is 14836733.893737 s in the future
idjc-0.6.9_pre4/idjcpython/IDJCjingles.py
tar: idjc-0.6.9_pre4/idjcpython/IDJCjingles.py: time stamp 2006-08-28 20:15:48 is 20052806.885572 s in the future
idjc-0.6.9_pre4/idjcpython/IDJCmedia.py
tar: idjc-0.6.9_pre4/idjcpython/IDJCmedia.py: time stamp 2007-01-03 03:00:55 is 31049913.881936 s in the future
idjc-0.6.9_pre4/idjcpython/IDJCmixprefs.py
tar: idjc-0.6.9_pre4/idjcpython/IDJCmixprefs.py: time stamp 2006-11-29 15:15:55 is 28070013.878981 s in the future
idjc-0.6.9_pre4/idjcpython/IDJCmultitagger.py
tar: idjc-0.6.9_pre4/idjcpython/IDJCmultitagger.py: time stamp 2006-08-28 20:18:53 is 20052991.863091 s in the future
idjc-0.6.9_pre4/idjcpython/IDJCservergui.py
tar: idjc-0.6.9_pre4/idjcpython/IDJCservergui.py: time stamp 2006-11-27 18:09:07 is 27907605.860587 s in the future
idjc-0.6.9_pre4/idjcpython/IDJCservdialog.py
tar: idjc-0.6.9_pre4/idjcpython/IDJCservdialog.py: time stamp 2006-03-09 00:12:26 is 5119804.859535 s in the future
idjc-0.6.9_pre4/idjcpython/idjc_config.py
tar: idjc-0.6.9_pre4/idjcpython/idjc_config.py: time stamp 2007-01-08 17:45:27 is 31534985.858677 s in the future
idjc-0.6.9_pre4/idjcpython/langheader.py
tar: idjc-0.6.9_pre4/idjcpython/langheader.py: time stamp 2006-12-01 20:02:06 is 28259984.857061 s in the future
idjc-0.6.9_pre4/idjcpython/idjcgui.py
tar: idjc-0.6.9_pre4/idjcpython/idjcgui.py: time stamp 2007-01-03 02:36:14 is 31048432.854071 s in the future
idjc-0.6.9_pre4/idjcpython/Makefile.am
tar: idjc-0.6.9_pre4/idjcpython/Makefile.am: time stamp 2006-09-09 17:24:43 is 21079341.837639 s in the future
idjc-0.6.9_pre4/idjcpython/Makefile.in
tar: idjc-0.6.9_pre4/idjcpython/Makefile.in: time stamp 2007-01-08 17:45:13 is 31534971.836659 s in the future
idjc-0.6.9_pre4/artwork/
tar: idjc-0.6.9_pre4/idjcpython: time stamp 2007-01-08 17:45:43 is 31535001.8357 s in the future
idjc-0.6.9_pre4/artwork/add3.xpm
idjc-0.6.9_pre4/artwork/advance.xpm
idjc-0.6.9_pre4/artwork/del.xpm
idjc-0.6.9_pre4/artwork/greenphone.xpm
idjc-0.6.9_pre4/artwork/interlude.xpm
idjc-0.6.9_pre4/artwork/jack2.xpm
idjc-0.6.9_pre4/artwork/led_lit_amber_black_border_64x64.xpm
tar: idjc-0.6.9_pre4/artwork/led_lit_amber_black_border_64x64.xpm: time stamp 2006-03-05 21:12:10 is 4849788.812907 s in the future
idjc-0.6.9_pre4/artwork/led_lit_green_black_border_64x64.xpm
tar: idjc-0.6.9_pre4/artwork/led_lit_green_black_border_64x64.xpm: time stamp 2006-03-05 21:12:55 is 4849833.811711 s in the future
idjc-0.6.9_pre4/artwork/led_lit_red_black_border_64x64.xpm
tar: idjc-0.6.9_pre4/artwork/led_lit_red_black_border_64x64.xpm: time stamp 2006-03-05 21:13:28 is 4849866.810157 s in the future
idjc-0.6.9_pre4/artwork/led_unlit_clear_border_64x64.xpm
tar: idjc-0.6.9_pre4/artwork/led_unlit_clear_border_64x64.xpm: time stamp 2006-03-05 21:13:52 is 4849890.809188 s in the future
idjc-0.6.9_pre4/artwork/mic4.xpm
idjc-0.6.9_pre4/artwork/mic5.xpm
idjc-0.6.9_pre4/artwork/next.xpm
idjc-0.6.9_pre4/artwork/note.xpm
idjc-0.6.9_pre4/artwork/pass.xpm
idjc-0.6.9_pre4/artwork/pause.xpm
idjc-0.6.9_pre4/artwork/pause_yellow.xpm
tar: idjc-0.6.9_pre4/artwork/pause_yellow.xpm: time stamp 2006-03-10 02:41:04 is 5215122.789002 s in the future
idjc-0.6.9_pre4/artwork/pbphone.xpm
idjc-0.6.9_pre4/artwork/play2.xpm
idjc-0.6.9_pre4/artwork/play3.xpm
idjc-0.6.9_pre4/artwork/prev.xpm
idjc-0.6.9_pre4/artwork/rec.xpm
idjc-0.6.9_pre4/artwork/redphone.xpm
idjc-0.6.9_pre4/artwork/stop.xpm
idjc-0.6.9_pre4/artwork/volume2.xpm
idjc-0.6.9_pre4/artwork/logo.xpm
tar: idjc-0.6.9_pre4/artwork/logo.xpm: time stamp 2006-09-06 20:10:55 is 20830113.7812 s in the future
idjc-0.6.9_pre4/artwork/icon.xpm
tar: idjc-0.6.9_pre4/artwork/icon.xpm: time stamp 2006-09-09 18:45:00 is 21084158.779125 s in the future
idjc-0.6.9_pre4/artwork/add3.png
tar: idjc-0.6.9_pre4/artwork/add3.png: time stamp 2006-03-05 21:21:58 is 4850376.764685 s in the future
idjc-0.6.9_pre4/artwork/advance.png
tar: idjc-0.6.9_pre4/artwork/advance.png: time stamp 2006-03-05 21:21:21 is 4850339.763498 s in the future
idjc-0.6.9_pre4/artwork/del.png
tar: idjc-0.6.9_pre4/artwork/del.png: time stamp 2006-03-05 21:20:56 is 4850314.762571 s in the future
idjc-0.6.9_pre4/artwork/greenphone.png
tar: idjc-0.6.9_pre4/artwork/greenphone.png: time stamp 2006-03-05 21:19:47 is 4850245.761683 s in the future
idjc-0.6.9_pre4/artwork/interlude.png
tar: idjc-0.6.9_pre4/artwork/interlude.png: time stamp 2006-03-05 21:17:44 is 4850122.759639 s in the future
idjc-0.6.9_pre4/artwork/jack2.png
tar: idjc-0.6.9_pre4/artwork/jack2.png: time stamp 2006-03-05 21:17:23 is 4850101.75872 s in the future
idjc-0.6.9_pre4/artwork/led_lit_amber_black_border_64x64.png
tar: idjc-0.6.9_pre4/artwork/led_lit_amber_black_border_64x64.png: time stamp 2006-03-05 21:04:26 is 4849324.757844 s in the future
idjc-0.6.9_pre4/artwork/led_lit_green_black_border_64x64.png
tar: idjc-0.6.9_pre4/artwork/led_lit_green_black_border_64x64.png: time stamp 2006-03-05 20:46:29 is 4848247.756942 s in the future
idjc-0.6.9_pre4/artwork/led_lit_red_black_border_64x64.png
tar: idjc-0.6.9_pre4/artwork/led_lit_red_black_border_64x64.png: time stamp 2006-03-05 21:03:43 is 4849281.756087 s in the future
idjc-0.6.9_pre4/artwork/led_unlit_clear_border_64x64.png
tar: idjc-0.6.9_pre4/artwork/led_unlit_clear_border_64x64.png: time stamp 2006-03-05 20:23:02 is 4846840.740435 s in the future
idjc-0.6.9_pre4/artwork/mic4.png
tar: idjc-0.6.9_pre4/artwork/mic4.png: time stamp 2006-03-05 21:23:57 is 4850495.732718 s in the future
idjc-0.6.9_pre4/artwork/mic5.png
tar: idjc-0.6.9_pre4/artwork/mic5.png: time stamp 2006-03-05 21:24:20 is 4850518.730078 s in the future
idjc-0.6.9_pre4/artwork/next.png
tar: idjc-0.6.9_pre4/artwork/next.png: time stamp 2006-03-05 21:24:43 is 4850541.728928 s in the future
idjc-0.6.9_pre4/artwork/note.png
tar: idjc-0.6.9_pre4/artwork/note.png: time stamp 2006-03-05 21:25:12 is 4850570.728054 s in the future
idjc-0.6.9_pre4/artwork/pass.png
tar: idjc-0.6.9_pre4/artwork/pass.png: time stamp 2006-03-05 21:25:33 is 4850591.727016 s in the future
idjc-0.6.9_pre4/artwork/pause.png
tar: idjc-0.6.9_pre4/artwork/pause.png: time stamp 2006-03-05 21:25:56 is 4850614.726138 s in the future
idjc-0.6.9_pre4/artwork/pause_yellow.png
tar: idjc-0.6.9_pre4/artwork/pause_yellow.png: time stamp 2006-03-10 02:40:32 is 5215090.725267 s in the future
idjc-0.6.9_pre4/artwork/pbphone.png
tar: idjc-0.6.9_pre4/artwork/pbphone.png: time stamp 2006-03-05 21:26:15 is 4850633.72436 s in the future
idjc-0.6.9_pre4/artwork/play2.png
tar: idjc-0.6.9_pre4/artwork/play2.png: time stamp 2006-03-05 21:26:32 is 4850650.709139 s in the future
idjc-0.6.9_pre4/artwork/play3.png
tar: idjc-0.6.9_pre4/artwork/play3.png: time stamp 2006-03-05 21:26:52 is 4850670.708273 s in the future
idjc-0.6.9_pre4/artwork/prev.png
tar: idjc-0.6.9_pre4/artwork/prev.png: time stamp 2006-03-05 21:27:07 is 4850685.706859 s in the future
idjc-0.6.9_pre4/artwork/rec.png
tar: idjc-0.6.9_pre4/artwork/rec.png: time stamp 2006-03-05 21:27:24 is 4850702.705968 s in the future
idjc-0.6.9_pre4/artwork/redphone.png
tar: idjc-0.6.9_pre4/artwork/redphone.png: time stamp 2006-03-05 21:27:53 is 4850731.70511 s in the future
idjc-0.6.9_pre4/artwork/stop.png
tar: idjc-0.6.9_pre4/artwork/stop.png: time stamp 2006-03-05 21:28:06 is 4850744.704253 s in the future
idjc-0.6.9_pre4/artwork/volume2.png
tar: idjc-0.6.9_pre4/artwork/volume2.png: time stamp 2006-03-05 21:28:19 is 4850757.703172 s in the future
idjc-0.6.9_pre4/artwork/logo.png
tar: idjc-0.6.9_pre4/artwork/logo.png: time stamp 2006-09-06 20:10:33 is 20830091.702138 s in the future
idjc-0.6.9_pre4/artwork/icon.png
tar: idjc-0.6.9_pre4/artwork/icon.png: time stamp 2006-09-09 16:41:03 is 21076721.70005 s in the future
idjc-0.6.9_pre4/artwork/Makefile.am
tar: idjc-0.6.9_pre4/artwork/Makefile.am: time stamp 2006-09-09 18:38:57 is 21083795.683907 s in the future
idjc-0.6.9_pre4/artwork/Makefile.in
tar: idjc-0.6.9_pre4/artwork/Makefile.in: time stamp 2007-01-08 17:45:13 is 31534971.682404 s in the future
idjc-0.6.9_pre4/Man/
tar: idjc-0.6.9_pre4/artwork: time stamp 2007-01-08 17:45:43 is 31535001.681705 s in the future
idjc-0.6.9_pre4/Man/idjc.1_
tar: idjc-0.6.9_pre4/Man/idjc.1_: time stamp 2006-11-28 00:38:49 is 27930987.680845 s in the future
idjc-0.6.9_pre4/Man/idjcskype.1_
tar: idjc-0.6.9_pre4/Man/idjcskype.1_: time stamp 2007-01-03 22:24:46 is 31119744.679828 s in the future
idjc-0.6.9_pre4/Man/Makefile.am
tar: idjc-0.6.9_pre4/Man/Makefile.am: time stamp 2006-09-12 01:23:28 is 21280866.678964 s in the future
idjc-0.6.9_pre4/Man/Makefile.in
tar: idjc-0.6.9_pre4/Man/Makefile.in: time stamp 2007-01-08 17:45:13 is 31534971.677992 s in the future
tar: idjc-0.6.9_pre4/Man: time stamp 2007-01-08 17:45:43 is 31535001.67724 s in the future
tar: idjc-0.6.9_pre4: time stamp 2007-01-08 17:45:43 is 31535001.676605 s in the future
josh@JOSH:~/Desktop$ cd idjc-0.6.9_pre4
josh@JOSH:~/Desktop/idjc-0.6.9_pre4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... configure: error: newly created file is older than distributed files!
Check your system clock
josh@JOSH:~/Desktop/idjc-0.6.9_pre4$ 

```

---

### Post by saperduper on 2007-05-21
the solution is quite simple

```
sudo apt-get install idjc
```

---

### Post by paul928 on 2007-06-04
> **saperduper said:**
> the solution is quite simple

```
sudo apt-get install idjc
```

Yes that's how I installed it. It is great,but I have a recurring problem . After several hours running it does this:

Toggle ON recieved for signal: Play
player shutdown code was called
song title: Rob Costlow - Solo Piano - Forever

updated metadata with: Rob Costlow - Solo Piano - Forever
Seek time is 0 seconds
player context id is 937

Attempting reconnection
updated metadata with: Rob Costlow - Solo Piano - Forever
Disconnect... waiting for server threads to finish
Error writing mp3 output 
Forcible disconnection by watchdog
subgraph starting at idjc-mx timed out (subgraph_wait_fd=13, status = 0, state = Finished)
cannot send event to client [idjc-srv] (Broken pipe)


**** alsa_pcm: xrun of at least 498.236 msecs

Server was pressed
idjc: the server module appears to have crashed -- possible segfault
updated metadata with: Rob Costlow - Solo Piano - Forever
Assuming raw pcm input file : Forcing byte-swapping
LAME version 3.96.1 ([http://lame.sourceforge.net/](http://lame.sourceforge.net/))
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE
Resampling:  input 44.1 kHz  output 24 kHz
Using polyphase lowpass filter, transition band: 10935 Hz - 11226 Hz
Encoding <stdin> to <stdout>
Encoding as 24 kHz  64 kbps j-stereo MPEG-2 Layer III (12x) qval=1
Connected to server...


**** alsa_pcm: xrun of at least 2.141 msecs

Ubuntu 7.04 running IDJC from console.

---

