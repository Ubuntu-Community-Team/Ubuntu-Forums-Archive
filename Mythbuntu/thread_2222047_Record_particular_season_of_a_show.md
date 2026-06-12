---
title: "Record particular season of a show?"
date: 2014-05-04
forum: Mythbuntu
---

### Post by funkyFlash on 2014-05-04
So, it seems like the functionality is there to record a show based on the season reported in Metadata.  My wife and I are caught up on all but the latest season of a couple shows, so i just want myth to pick up ANYTHING in the current season.  Seems simple enough.  So, I set the record policy to be any channel any time, check for duplicates, get metadata, record from season 9 episode 0 (which i assumed to mean any).  I hit the "Find Metadata" button, and it seems to work, it gave me a show ID, season, and episode of the recording I clicked. I defaulted the episode back to 0, and hit save.

So, it's recording every HD episode ever...  I assume only once, because it's still set to check for duplicates.  Well, drat.  So, I make sure metadata fetching is working:

[FONT=Fixedsys]mysql> select chanid,title,subtitle,season,episode,category,seriesid,programid from recorded where seriesid = 'EP00753796';
+--------+-----------------------+--------------------------+--------+---------+----------+------------+----------------+
| chanid | title                 | subtitle                 | season | episode | category | seriesid   | programid      |
+--------+-----------------------+--------------------------+--------+---------+----------+------------+----------------+
**|   1238 | How I Met Your Mother | The Rough Patch          |      0 |       0 | Sitcom   | EP00753796 | EP007537960100 |**
|   1238 | How I Met Your Mother | Miracles                 |      3 |      20 | Sitcom   | EP00753796 | EP007537960069 |
|   1810 | How I Met Your Mother | Sandcastles in the Sand  |      3 |      16 | Sitcom   | EP00753796 | EP007537960065 |
|   1238 | How I Met Your Mother | Symphony of Illumination |      7 |      12 | Sitcom   | EP00753796 | EP007537960153 |
|   1810 | How I Met Your Mother | I'm Not That Guy         |      3 |       6 | Sitcom   | EP00753796 | EP007537960055 |
|   1810 | How I Met Your Mother | The Goat                 |      3 |      17 | Sitcom   | EP00753796 | EP007537960066 |
+--------+-----------------------+--------------------------+--------+---------+----------+------------+----------------+
6 rows in set (0.00 sec)[/FONT]

(Do a mythmetadatalookup --refresh-all)

[FONT=Fixedsys]mysql> select chanid,title,subtitle,season,episode,category,seriesid,programid from recorded where seriesid = 'EP00753796';
+--------+-----------------------+--------------------------+--------+---------+----------+------------+----------------+
| chanid | title                 | subtitle                 [FONT=Courier Neseason | episode | category | seriesid   | programid      |
+--------+-----------------------+--------------------------+--------+---------+----------+------------+----------------+
**|   1238 | How I Met Your Mother | The Rough Patch          |      5 |       7 | Sitcom   | EP00753796 | EP007537960100 |**
|   1238 | How I Met Your Mother | Miracles                 |      3 |      20 | Sitcom   | EP00753796 | EP007537960069 |
|   1810 | How I Met Your Mother | Sandcastles in the Sand  |      3 |      16 | Sitcom   | EP00753796 | EP007537960065 |
|   1238 | How I Met Your Mother | Symphony of Illumination |      7 |      12 | Sitcom   | EP00753796 | EP007537960153 |
|   1810 | How I Met Your Mother | I'm Not That Guy         |      3 |       6 | Sitcom   | EP00753796 | EP007537960055 |
|   1810 | How I Met Your Mother | The Goat                 |      3 |      17 | Sitcom   | EP00753796 | EP007537960066 |
+--------+-----------------------+--------------------------+--------+---------+----------+------------+----------------+
6 rows in set (0.00 sec)
[/FONT]

Sorry for the poor formatting.  I can't figure out how to make a monospace font...  This tells me that mythmetadatalookup is working properly.  Now, why doesn't it filter on the metadata?

Oh, and this is a mythbuntu add-on to a ubuntu 12.04.4 minimal system.  Backend version:
mythtv@chimera:~$ mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version : v0.27-205-g39686c6
MythTV Branch : fixes/0.27
Network Protocol : 77
Library API : 0.27.20140323-1
QT Version : 4.8.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libfftw3 using_libxml2 using_lirc using_mheg using_opengl using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_sdl using_taglib using_v4l2 using_x11 using_xrandr using_xv using_profiletype using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_mheg using_libass using_libxml2

Help!  Thanks!

---

### Post by blm-ubunet on 2014-05-04
The season/series & episode numbers have come from the metadatalookup which happens after the show is recorded.
For your rule idea to work you need to use what is available in your EIT/EPG at scheduling (title, seriesid & programid).

Some of us don't even that that much good data..

---

