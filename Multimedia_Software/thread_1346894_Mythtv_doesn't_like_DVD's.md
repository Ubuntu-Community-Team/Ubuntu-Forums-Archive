---
title: "Mythtv doesn't like DVD's"
date: 2009-12-05
forum: Multimedia Software
---

### Post by ronklob on 2009-12-05
Hi all, 

I'll try to give as much info as possible, because I really need to get this fixed asap.  Please bear with me, I'm still learning.  

I installed Mythbuntu 0.21(Ubuntu 9.04) several weeks ago.  Everything seemed to be working fine.  I wanted to add Mirobridge, so I upgraded to Mythbuntu 0.22(9.10).  The upgrade for Ubuntu seemed to work, but I couldn't get Mythtv to work at all.  

So, in desperation, I dl'd and installed Myth 0.22 from source.  Then I had problems with everything, but found out I had to also install the Themes and Plugins.  So I did that.  Now everything seems to work, EXCEPT for DVD playback and transcoding.  Mplayer, zine, and VLC can all play DVDs just fine.  

So, I'm thinking I must have messed up my Myth install somehow.  

Here are the details of my install:  

ronklob@ronklob-desktop:~/Desktop/mythtv-0.22rc1$ ./configure
# Basic Settings
Compile type              release
Compiler cache            no
DistCC                    no
qmake                     /usr/bin/qmake
install prefix            /usr/local
runtime prefix            /usr/local
CPU                       x86 x86_32 (model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz)
big-endian                no
runtime cpu detection     no
yasm                      no
MMX enabled               yes
MMX2 enabled              yes
3DNow! enabled            yes
3DNow! extended enabled   yes
SSE enabled               yes
SSSE3 enabled             yes
CMOV enabled              yes

# Input Support
Joystick menu             yes
lirc support              yes
Video4Linux sup.          yes
ivtv support              yes
HD-PVR support            yes
FireWire support          no
DVB support               yes [/usr/include]
DVB-S2 support            yes
HDHomeRun support         yes
IPTV support              yes

# Sound Output Support
PulseAudio support        no
OSS support               yes
ALSA support              no
aRts support              no
JACK support              no
libfftw3 support          no

# Video Output Support
x11 support               yes
xrandr support            yes
xv support                no
XvMC support              no
XvMC VLD support          no
XvMC pro support          no
XvMC libs                 -lchromeXvMC
VDPAU support             no
OpenGL video              yes
OpenGL vsync              yes
DirectFB                  no
Fribidi formatting        no
MHEG support              yes

# Misc Features
multi threaded libavcodec yes
Frontend                  yes
Backend                   yes

# Bindings
bindings_perl             yes
bindings_python           yes

Creating libs/libmythdb/mythconfig.h and libs/libmythdb/mythconfig.mak

libs/libmythdb/mythconfig.h is unchanged
===============================================

ronklob@ronklob-desktop:~/Desktop/mythplugins-0.22$ ./configure
Disabling MythZoneMinder. Requires mysql/mysql.h header

Configuration settings: 
 
        qmake          /usr/bin/qmake
 
        MythArchive    plugin will be built
        MythBrowser    plugin will be built
        MythFlix       plugin will be built
        MythGallery    plugin will be built
        MythGame       plugin will be built
        MythMusic      plugin will be built
        MythNews       plugin will be built
        MythVideo      plugin will be built
        MythWeather    plugin will be built
        MythZoneMinder plugin will not be built
        MythMovies     plugin will be built
        OpenGL         support will be included in MythGallery
        EXIF           support will not be included in MythGallery
        OpenGL         support will be included in MythMusic
        libvisual      support will not be included in MythMusic
        FFTW           support will not be included in MythMusic
        SDL            support will not be included in MythMusic
================================================

Here is the output from mtd when I attempt to rip a DVD:

2009-12-04 08:06:31.945 08:06:31: a client socket has been opened
2009-12-04 08:07:13.663 08:07:13: launching job: job dvd 15 1 2 1 -1 /media/media200/mythtv/videos/Unknown
Error in my_thread_global_end(): 1 threads didn't exit
2009-12-04 08:07:18.681 New DB connection, total: 1
2009-12-04 08:07:18.686 Connected to database 'mythconverg' at host: 127.0.0.1
2009-12-04 08:07:18.744 Found Transcode Version: 1.1
2009-12-04 08:07:18.744 New DB connection, total: 2
2009-12-04 08:07:18.745 Connected to database 'mythconverg' at host: 127.0.0.1
2009-12-04 08:07:18.751 08:07:18: transcode command will be: 'transcode -i /var/lib/mythdvd/temp/Unknown/vob/ -g 720x480 -M 2 -y xvid,null -A -N 0x2000 -o /dev/null --log_no_color -R 1,twopass.log'
2009-12-04 08:07:18.751 08:07:18: job thread beginning to rip dvd title
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000168
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000271
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000032c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000016fd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000017b8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000278a7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00027962
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00027aff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00027bba
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00060223
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00067c6c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002ab93d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002abb7f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002abd45
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002abe00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x002ad833
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x002ad8ee
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x002ada68
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x002adb23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x002adc00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x002adcbb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x002ade53
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x002adf0e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x002adfeb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x002ae0a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x002ae52a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x002ae5e5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x002ae839
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x002ae8f4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x002c779e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x002c7859
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x002dbfd9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x002dc094
libdvdread: Elapsed time 0
libdvdread: Found 16 VTS's
libdvdread: Elapsed time 0
2009-12-04 08:09:09.005 08:09:09: Error: DVDPerfectThread read failed for 235 blocks at 185561
2009-12-04 08:09:09.739 08:09:09: job failed: job dvd 15 1 2 1 -1 /media/media200/mythtv/videos/Unknown
================================================

And here is the output of mythfrontend when I attempt to play a DVD:

2009-12-04 08:10:06.327 Connected to database 'mythconverg' at host: 127.0.0.1
2009-12-04 08:10:06.502 TV: Attempting to change from None to Watching DVD
libdvdnav: Using dvdnav version svnR1169
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ronklob/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2009-12-04 08:10:38.813 Failed to open DVD device at /dev/cdrom

So it appears that the transcoder can access the DVD, but somehow it fails, but the reading can't open the device.  ???

My thinking is that I missed something when I compiled.  But I don't know how to re-do it.  Can I just re-compile and re-install just the DVD support without screwing up everything else?  Or do I have to start from scratch?  

Thanks for the help.

---

### Post by ronklob on 2009-12-09
bump... 

Anyone?  I have found out that it is definitely Myth.  I can rip and transcode with dvd::rip just fine.

---

### Post by &lt;mike&gt; on 2009-12-20
I don't really know, but could it be that myth is looking for dvd files in the wrong place?
Silly question, but do you have a dvd device at /dev/cdrom/ ? (I do.)
If not, you'll need to figure out how to change where myth is looking... I can't find it in the gui settings, but you can do it via the database if you need to.

To see where myth is looking,
```

mysql -u mythtv -p -e 'select data from settings where value = "DVDDeviceLocation";' mythconverg

```
type your password. I get the following:
```

+----------+
| data     |
+----------+
| /dev/dvd | 
+----------+


```

---

