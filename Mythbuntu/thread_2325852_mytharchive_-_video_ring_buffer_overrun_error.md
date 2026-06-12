---
title: "mytharchive - video ring buffer overrun error"
date: 2016-05-26
forum: Mythbuntu
---

### Post by 9072997 on 2016-05-26
I am trying to get mytharchive to burn DVDs of my recorded movies (with cutlists). It is not working, and it deletes the original recordings (I don't know if this is intended behavior, but I don't like it). the end of mythburn.log is reproduced below (on 16.10):

```

video DTS inconsistent: 
 0:00:01.9347
 0:00:01.9347
 0:00:02.0015
 0:00:01.4681
diff: 
 0:00:00.0667
video PTS inconsistent:
 0:00:01.9681
 0:00:01.9681
 0:00:02.0682
 0:00:01.5348
 diff: 
 0:00:00.1001
video DTS inconsistent: 
 0:00:01.9347
 0:00:01.9347
 0:00:02.0348
 0:00:01.5015
diff: 
 0:00:00.1001
video PTS inconsistent:
 0:00:01.9681
 0:00:01.9681
 0:00:02.1016
 0:00:01.5682
 diff: 
 0:00:00.1334
video DTS inconsistent: 
 0:00:01.9347
 0:00:01.9347
 0:00:02.0682
 0:00:01.5348
diff: 
 0:00:00.1334
starting audio PTS: 
 0:00:13.5207
ringbuffer overflow 628<2015 629145
video ring buffer overrun error
************************************************************
ERROR: Failed while running mythreplex. Command was mythreplex --demux --fix_sync -o "/var/lib/mytharchive/temp/work/1/stream" -v 224 -c 128 "/var/lib/mytharchive/temp/work/1/newfile2.mpg"
See mythburn.log for more information.
************************************************************

chmod: changing permissions of '/var/lib/mytharchive/temp/': Operation not permitted
Terminated

```

some additional info which might be usefull
```

thrive@thrive-dvr:~/Desktop$ mythfrontend --version
Please attach all output as a file in bug reports.
MythTV Version : v0.28-2-g15cf421
MythTV Branch : fixes/0.28
Network Protocol : 88
Library API : 0.28.20160309-1
QT Version : 5.5.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_vbox using_ceton using_hdpvr using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libfftw3 using_libxml2 using_lirc using_mheg using_opengl using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_sdl using_taglib using_v4l2 using_x11 using_xrandr using_xv using_profiletype using_bindings_perl using_bindings_python using_bindings_php using_freetype2 using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_mheg using_libass using_libxml2
thrive@thrive-dvr:~/Desktop$ ls -l /var/lib/mytharchive/
total 4
drwxrwsr-x 5 mythtv mythtv 4096 May 25 22:34 temp
thrive@thrive-dvr:~/Desktop$ 

```

---

