---
title: "Transcode Jobs Failing"
date: 2010-11-02
forum: Mythbuntu
---

### Post by uncle hammy on 2010-11-02
Since upgrading to 0.24, I am having almost all of my transcode jobs failing.  They all fall prey to the same error

```
(exit status 0, job status was "Starting"
```

My current versions are...

```

ii  libmyth-0.24-0                       0.24.0+fixes27071-0ubuntu0+mythbuntu1           Common library code for MythTV and add-on mo
ii  libmyth-python                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           A python library to access some MythTV featu
ii  libmythtv-perl                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           A PERL library to access some MythTV feature
ii  mytharchive                          0.24.0+fixes27071-0ubuntu0+mythbuntu1           create and burn DVD's from MythTV - binary f
ii  mythbuntu-common                     0.50-0ubuntu1                                   Mythbuntu application support functions
ii  mythbuntu-control-centre             0.62-0ubuntu1                                   Mythbuntu Configuration Application
ii  mythbuntu-default-settings           0.96-0ubuntu1                                   default settings for Mythbuntu
ii  mythbuntu-desktop                    0.59                                            The Mythbuntu standalone system
ii  mythbuntu-gdm-theme                  0.6-0ubuntu1                                    Mythbuntu GDM theme
ii  mythbuntu-lirc-generator             0.24-0ubuntu1                                   Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                0.7-0ubuntu1                                    Mythbuntu repos installer
ii  mythbuntu-repos                      8.7-0ubuntu0+mythbuntu~auto20101030003223       Mythbuntu repos installer
ii  mythgallery                          0.24.0+fixes27071-0ubuntu0+mythbuntu1           Image gallery/slideshow add-on module for My
ii  mythmovies                           0.24.0+fixes27071-0ubuntu0+mythbuntu1           Find nearby movies and cinema listings
ii  mythmusic                            0.24.0+fixes27071-0ubuntu0+mythbuntu1           Music add-on module for MythTV
ii  mythtv                               0.24.0+fixes27009-0ubuntu0+mythbuntu1           A personal video recorder application (clien
ii  mythtv-backend                       0.24.0+fixes27071-0ubuntu0+mythbuntu1           A personal video recorder application (serve
ii  mythtv-backend-master                0.24.0+fixes27009-0ubuntu0+mythbuntu1           Metapackage to setup and configure a "Master
ii  mythtv-common                        0.24.0+fixes27071-0ubuntu0+mythbuntu1           A personal video recorder application (commo
ii  mythtv-database                      0.24.0+fixes27009-0ubuntu0+mythbuntu1           A personal video recorder application (datab
ii  mythtv-frontend                      0.24.0+fixes27071-0ubuntu0+mythbuntu1           A personal video recorder application (clien
ii  mythtv-theme-arclight                1:0.24.0+fixes27009-0ubuntu0+mythbuntu1         The arclight MythTV Theme
ii  mythtv-theme-blootube-osd            1:0.24.0~trunk25106-0ubuntu0~mythbuntu1         The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                 1:0.24.0~trunk25106-0ubuntu0~mythbuntu1         The blueosd MythTV Theme
ii  mythtv-theme-childish                1:0.24.0+fixes27009-0ubuntu0+mythbuntu1         The childish MythTV Theme
ii  mythtv-theme-graphite                1:0.24.0+fixes27009-0ubuntu0+mythbuntu1         The graphite MythTV Theme
ii  mythtv-theme-iulius-osd              1:0.24.0~trunk25106-0ubuntu0~mythbuntu1         The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy              1:0.24.0+fixes27009-0ubuntu0+mythbuntu1         The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                1:0.24.0~trunk25106-0ubuntu0~mythbuntu1         The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu               1:0.24.0+fixes27009-0ubuntu0+mythbuntu1         The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd      1:0.24.0~trunk25106-0ubuntu0~mythbuntu1         The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd               1:0.24.0~trunk25106-0ubuntu0~mythbuntu1         The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd          1:0.24.0~trunk25106-0ubuntu0~mythbuntu1         The titivillus-osd MythTV Theme
ii  mythtv-themes                        1:0.24.0+fixes27009-0ubuntu0+mythbuntu1         Themes for MythTV
ii  mythtv-transcode-utils               0.24.0+fixes27071-0ubuntu0+mythbuntu1           Utilities used for transcoding MythTV tasks
ii  mythvideo                            0.24.0+fixes27071-0ubuntu0+mythbuntu1           A generic video player frontend module for M
ii  mythweather                          0.24.0+fixes27071-0ubuntu0+mythbuntu1           Weather add-on module for MythTV
ii  mythweb                              0.24.0+fixes27009-0ubuntu0+mythbuntu1           Web interface add-on module for MythTV
```

I don't know if it's related, but I have noticed that many of the preview images of recordings (in MythWeb, or on the Recordings) screen are "pixelated" or can't be generated.  My backend logs are full of errors trying to create previews...

```

2010-11-02 20:16:21.454 Preview Error: Preview process not ok.
                        fileinfo(/mythtv_storage3/recordings/1081_20101028200000.mpg.png) exists: 0 readable: 0 size: 0
2010-11-02 20:16:21.462 Preview Error: Despite command '/usr/bin/mythpreviewgen --size 0x0 --chanid 1081 --starttime 20101028200000  > /dev/null' returning success
2010-11-02 20:16:21.478 Launching:  2
2010-11-02 20:16:21.544 PID 4523: launched
2010-11-02 20:16:21.554 PID 4520: exited: status=32512, result=127
sh: 2010-11-02 20:16:21.587 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1081 --starttime 20101030203000  > /dev/null'
ï¿½2: not found
2010-11-02 20:16:21.618 Launching: 2
2010-11-02 20:16:21.626 PID 4526: launched
sh: ï¿½ï¿½2: not found
2010-11-02 20:16:21.687 PID 4523: exited: status=32512, result=127
2010-11-02 20:16:21.696 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1131 --starttime 20101031190000  > /dev/null'
2010-11-02 20:16:21.796 PID 4526: exited: status=32512, result=127
2010-11-02 20:16:21.804 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1032 --starttime 20101101200000  > /dev/null'
2010-11-02 20:17:03.232 MainServer::ANN Monitor
2010-11-02 20:17:03.245 adding: myth-backend as a client (events: 2)
2010-11-02 20:17:58.148 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-02 20:20:17.929 Launching: `p2
2010-11-02 20:20:17.936 Launching:  m2
2010-11-02 20:20:17.989 PID 4566: launched
sh: sh: 2010-11-02 20:20:18.006 PID 4567: launched
Syntax error: EOF in backquote substitutionm2: not found

2010-11-02 20:20:18.095 PID 4566: exited: status=512, result=2
2010-11-02 20:20:18.101 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1131 --starttime 20101031210000  > /dev/null'
2010-11-02 20:20:18.117 Launching:
2010-11-02 20:20:18.132 PID 4569: launched
2010-11-02 20:20:18.202 PID 4567: exited: status=32512, result=127
2010-11-02 20:20:18.210 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1131 --starttime 20101031190000  > /dev/null'
2010-11-02 20:20:18.224 Launching:
2010-11-02 20:20:18.232 PID 4571: launched
2010-11-02 20:20:18.310 PID 4569: exited: status=0, result=0
2010-11-02 20:20:18.318 Preview Error: Preview process not ok.
                        fileinfo(/mythtv_storage1/recordings/1131_20101017190000.mpg.png) exists: 0 readable: 0 size: 0
2010-11-02 20:20:18.326 Preview Error: Despite command '/usr/bin/mythpreviewgen --size 0x0 --chanid 1131 --starttime 20101017190000  > /dev/null' returning success

```

Anyone have any ideas what's going on?

---

### Post by nickrout on 2010-11-02
yes, you are using an unreleased version!

---

### Post by uncle hammy on 2010-11-03
Yes, I am aware of that.  Thanks for the helpful response.  I was more hoping for a bud report or known issue or something that I missed.  However, it appears that a round of updates this morning has my transcode jobs back on track.

---

### Post by LowSky on 2010-11-03
Part of the problem with using beta software is dealing with things that break. No one should use beta software on machines they deem critical.

---

### Post by Prium on 2010-11-09
'Transcoding' and 'Ubuntu' in the same sentence is a tumultuous proposition. With 10.04 I have had limited success with Transmageddon, but MEncoder fails 100% of the time and I have not found satisfaction in any other Ubuntu software for this purpose. My suggestion is, rather than brave a solution which will undoubtedly break during your next upgrade, either use XP in a virtual machine for transcoding or using online services. Good luck!

---

### Post by dibuntux on 2010-12-23
Just updated to 0.24, and noticed that transcode jobs are errored with exit status 136 IF I have a cut list I edited myself.

If not, they do transcode.

Any idea?

---

### Post by BicyclerBoy on 2010-12-31
What file formats are you trying to transcode ?
What is the container & the codecs required ?

I've not had any cutlists honoured for h264 (MPEG-4 part 10) material using 0.23, ever...

I'll try a cutlisted h264 encoded file using 0.24..

A common problem is the external ffmpeg version does not match the command line options used by mythtv.
Or ffmpeg needs to be patched to work so it is problematic to get a working pair..

---

