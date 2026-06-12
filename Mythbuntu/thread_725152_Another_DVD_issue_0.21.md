---
title: "Another DVD issue 0.21"
date: 2008-03-15
forum: Mythbuntu
---

### Post by uncle hammy on 2008-03-15
I have run the update to mythtv 0.21, still using Gutsy.  Everything went over fine, and I have figured out most of he menu changes, setting changes, etc.

I also went ahead and ran sudo apt-get install mythvideo, which removed mythdvd and upgraded mythvideo.  

However, when I go to Optical Disks>Play DVD (with a DVD in the drive), the screen goes black for a second, like it's trying to do something, then the frontend closes and I am staring at the mythbuntu desktop.

---

### Post by superm1 on 2008-03-15
Please launch it from a terminal (mythfrontend) and see if you catch any output relevant to the issue.

---

### Post by uncle hammy on 2008-03-15
Will do, I'll let you know what I find.

---

### Post by punkrawker82 on 2008-03-16
I've experienced this as well.  I just opted to launch an external player and used the following in the "DVD Player Command" setting:

xine -pfhq --no-splash dvd:/

---

### Post by uncle hammy on 2008-03-16
In my settings, DVD Commnd is set to "internal", the dvd device is set to /dev/dvd.  I have also set that to /dev/hdc, because if I go to Optical Disks>Eject Media, the selection box that comes up lists my dvd drive as /dev/hdc, and since it actually ejected the correct drive, I assume that's correct.

Either way, when running from a termial, this is what is displayed when I try to play a dvd...

```

libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2992849A
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/sharris/.dvdnav/DVD VIDEO.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO
2008-03-16 18:47:11.495 Failed to open DVD device at //dev/dvd

```

---

### Post by DemonBob on 2008-03-18
Same issue

```
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: vm: faild to open/read the DVD
2008-03-18 20:39:53.944 Failed to open DVD device at //dev/dvd
2008-03-18 20:40:12.238 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open //dev/dvd with libdvdcss.
libdvdread: Can't open //dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: vm: faild to open/read the DVD
2008-03-18 20:40:45.088 Failed to open DVD device at //dev/dvd

```

This did not happen last week before i upgraded to .21 (Only issue i have found with .21 love it so far keep up the good work guys.)

Can anyone shed some light on this issue.?

---

### Post by nasha on 2008-03-18
> sudo apt-get install mythvideo
Will solve your problem.

I don't know how many times a day i reply to a thread with that command... Theres been so many threads regarding MythDVD, MythVideo issues while upgrading, please search before posting...

---

### Post by larsolav on 2008-03-18
> **nasha said:**
> Will solve your problem.

I don't know how many times a day i reply to a thread with that command... Theres been so many threads regarding MythDVD, MythVideo issues while upgrading, please search before posting...

Hmmmm, didn't the first poster in this thread do that already?
>  
I also went ahead and ran sudo apt-get install mythvideo, which removed mythdvd and upgraded mythvideo.


---

### Post by nasha on 2008-03-18
Ok, i stand corrected. That'll teach me for scanning :P

---

### Post by uncle hammy on 2008-03-24
Nobody has any solutions for this issue?

---

### Post by majoridiot on 2008-03-24
(after installing the new mythvideo, of course...)

i had the same issue on a build yesterday... black screen only after loading a dvd.  i went into media
configuration and changed the dvd device from the default of /dev/dvd to the actual location of the 
drive- /dev/sr0  this fixed the problem and dvd's play fine with the internal player.  i would try
replacing the default with the actual location of the dvd drive.

alternately, you can symlink it to point to the correct location.  assuming a dvd physical location of /dev/hdc
you can create the symlink by:

```
$ sudo ln -s /dev/hdc /dev/dvd
$ sudo chmod a+rw /dev/dvd
```

that will redirect any read/write for /dev/dvd to the correct device.

---

### Post by uncle hammy on 2008-03-25
I have already tried that, I indicated in one of my posts.  It had no effect. :(

---

### Post by laga on 2008-03-26
What error message do you get now?

---

### Post by uncle hammy on 2008-03-29
I get the same results as I posted.

---

### Post by laga on 2008-03-30
So you're still getting > 2008-03-18 20:40:45.088 Failed to open DVD device at //dev/dvd although you've got a correct symlink in place?

---

### Post by uncle hammy on 2008-04-02
After entering the commands you indicated, this is exactly what I get. 

```

libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2992849A
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/sharris/.dvdnav/DVD VIDEO.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO
2008-04-02 20:57:25.598 Failed to open DVD device at //dev/dvd

```
Also, here are the results of a ls -all on /dev
```

lrwxrwxrwx  1 root   root           3 2008-04-02 20:46 dvd -> hdc
brw-rw-rw-  1 root   cdrom    22,   0 2008-04-02 20:46 hdc

```

---

### Post by sreyes on 2008-04-03
[QUOTE=uncle hammy;4529064]In my settings, DVD Commnd is set to "internal", the dvd device is set to /dev/dvd.  I have also set that to /dev/hdc, because if I go to Optical Disks>Eject Media, the selection box that comes up lists my dvd drive as /dev/hdc, and since it actually ejected the correct drive, I assume that's correct.

Where are the DVD settings?  I'm trying to get mine to work.  Nothing happens when I click on Watch DVD.

---

### Post by harlee188 on 2008-04-03
I am having the same issue, no one seems to have an answer...

---

### Post by Prefader on 2008-04-04
[quote=uncle hammy]Encrypted DVD support unavailable.[/quote]

Just out of curiosity, do you have the libdvdcss2 package installed?  And if you don't, are you certain that this disc isn't copy-protected?

---

### Post by agent5150 on 2008-04-07
Let me add to this mythvideo fiasco.  I did not experience the DVD issue but the update process did not let me select mythvideo (even though it was listed).  After the complete update finished and I havd .21 version for all other mythtv items.. I DID run apt-get install mythvideo, it uninstalled mythdvd and updated mythvideo.. but I have issues.

1. both mplayer and xine take good 10 secs to load a 600 mb avi (prior to update it was instantaneous).
2. 1st movie plays file, exit, select another avi... both mplayer and xine show green screen with dots (audio plays fine).. at this point I can't exit the player... have to ssh into the box and kill the process.  
... this merging of mythdvd into mythvideo was probably a good idea.. but didn't get executed correctly.  

Any one else getting green screens in mythvideo with avi files?

---

### Post by uncle hammy on 2008-04-07
> **Prefader said:**
> Just out of curiosity, do you have the libdvdcss2 package installed?
Thar she blows!  Went into MCC, and sure enough, I enabled the proprietary codecs, and all is well in DVD land.

Thanks so much!

---

### Post by Adrian Baugh on 2008-04-12
I have a slightly different variation on the problem:

I'm using Mythbuntu 8.04 beta, updates up to 13 April, dual core AMD64, onboard GeForce 7050 using the nvidia-new driver. I'm using ffmpeg as the decoder and all the device names are correct.  (My drive is /dev/scd0 symlinked to /dev/dvd).

All video playback is fine (using the internal player) except DVDs created with MythArchive.  These almost (but not quite) always immediately crash mythfrontend, leaving me with the xfce desktop.  Other DVDs work fine.  I've switched to using xine for the time being, but would love to see the internal player fixed as the DVD bookmarking is really useful.  Output is attached below...

myth@myth-desktop:~$ mythfrontend
2008-04-13 01:40:55.780 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-13 01:40:55.781 Configuration::Load - Error parsing: /home/myth/.mythtv/config.xml at line: 1  column: 1
2008-04-13 01:40:55.781 Configuration::Load - Error Msg: unexpected end of file
2008-04-13 01:40:56.255 XScreenSaver support enabled
2008-04-13 01:40:56.255 DPMS is disabled.
2008-04-13 01:40:56.256 Empty LocalHostName.
2008-04-13 01:40:56.256 Using localhost value of myth-desktop
2008-04-13 01:40:56.257 Configuration::Load - Error parsing: /home/myth/.mythtv/config.xml at line: 1  column: 1
2008-04-13 01:40:56.257 Configuration::Load - Error Msg: unexpected end of file
2008-04-13 01:40:56.269 New DB connection, total: 1
2008-04-13 01:40:56.273 Connected to database 'mythconverg' at host: localhost
2008-04-13 01:40:56.274 Closing DB connection named 'DBManager0'
2008-04-13 01:40:56.276 Primary screen 0.
2008-04-13 01:40:56.276 Connected to database 'mythconverg' at host: localhost
2008-04-13 01:40:56.278 Using screen 0, 1360x768 at 0,0
2008-04-13 01:40:56.286 New DB connection, total: 2
2008-04-13 01:40:56.286 Connected to database 'mythconverg' at host: localhost
2008-04-13 01:40:56.289 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-04-13 01:40:56.289 Enabled verbose msgs:  important general
2008-04-13 01:40:56.652 Primary screen 0.
2008-04-13 01:40:56.652 Using screen 0, 1360x768 at 0,0
2008-04-13 01:40:56.654 Switching to square mode (G.A.N.T)
2008-04-13 01:40:56.673 Using the Qt painter
2008-04-13 01:40:56.679 JoystickMenuClient Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2008-04-13 01:40:56.690 lirc init success using configuration file: /home/myth/.mythtv/lircrc
2008-04-13 01:40:58.454 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-04-13 01:40:58.550 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-13 01:40:58.605 Registering Internal as a media playback plugin.
2008-04-13 01:40:58.670 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-13 01:40:58.737 MythMusic adding CD-Writer: 0,0,0 -- ST3160815AS     
2008-04-13 01:40:58.738 MythMusic adding CD-Writer: 1,0,0 -- DVD A  DH20A1S  
2008-04-13 01:40:58.796 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-13 01:40:58.877 Starting update of BBC-Current-XML
2008-04-13 01:40:58.885 Starting update of BBC-3day-XML
2008-04-13 01:40:58.893 Starting update of Animated-Map-Download
2008-04-13 01:40:58.911 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-13 01:40:58.912 Using protocol version 40
2008-04-13 01:41:00.046 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccurrentxml.pl -u SI -d /home/myth/.mythtv/MythWeather/BBC-Current-XML L2441 has exited
2008-04-13 01:41:00.046 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbcthreedayxml.pl -u SI -d /home/myth/.mythtv/MythWeather/BBC-3day-XML L2441 has exited
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Pan's Labyrinth
libdvdnav: DVD Serial Number: 47FFA1D400002710
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/myth/.dvdnav/Pan's Labyrinth.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000007ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000dbb
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
2008-04-13 01:41:04.060 Opened DVD device at //dev/scd0
2008-04-13 01:41:04.060 There are 1 titles on the disk
2008-04-13 01:41:04.060 Title 0 has 0 parts.
2008-04-13 01:41:04.104 TV: Attempting to change from None to WatchingPreRecorded
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Pan's Labyrinth
libdvdnav: DVD Serial Number: 47FFA1D400002710
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/myth/.dvdnav/Pan's Labyrinth.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000007ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000dbb
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
2008-04-13 01:41:04.213 Opened DVD device at //dev/scd0
2008-04-13 01:41:04.213 There are 1 titles on the disk
2008-04-13 01:41:04.213 Title 0 has 0 parts.
2008-04-13 01:41:04.259 AFD: Opened codec 0xb58030, id(MPEG2VIDEO) type(Video)
2008-04-13 01:41:04.259 NVP: Disabling Audio, params(-1,-1,-1)
2008-04-13 01:41:04.294 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-04-13 01:41:04.334 OSD Theme Dimensions W: 640 H: 480
2008-04-13 01:41:04.576 TV: Changing from None to WatchingPreRecorded
Segmentation fault (core dumped)
myth@myth-desktop:~$

---

