---
title: "dvd players have all crashed and burn"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by satn3ver on 2008-03-26
Hi,

I am running Feisty 64 bit AMD.
I've been using ubuntu for about 3 years now and well, I've run into a problem with my dvd playback.

I used automatix on my last feisty install which lead, I believe, to an uncorrectable situation between my nvidia drivers and my xorg.conf file or something of that sort. If i recall i had the older nvidia driver with new kernal headers or it was the opposite but i could not correct the issue despite the numerous threads i read through. I decided to just wipe and start over fresh. I tried gutsy and had issues and decided to reinstall feisty since I've had my  most success running that version. So i did.

I havent needed to play a dvd since then until tonight. I have attempted to play Hot Fuzz for about an hour now.

First off, with the Medibuntu directions i get this:


> :~$ sudo apt-get install libdvdcss2 libdvdnav4 lsdvd libdvdread3 libavcodec1d non-free-codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
libdvdnav4 is already the newest version.
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
E: Couldn't find package libavcodec1d

w/e.  No dice. Totem xine and gstreamer both spit out an error saying

> The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?


Again, libdvdcss2 is installed already.

I then go to my trusty mplayer.

I get this: >  Fatal error: Could not initialize video filters (-vf) or video output (-vo).

I've been using mplayer for atleast a month or more now no issues.

I poke around and get the recommendation for VLC which i use on my install of Mac OS X Tiger. I install that from repos and it begins to play the DVD menu then crashes hard and disappears. So I know the codecs for VLC are working but something else is going wrong. 

When I did use automatix to install my multimedia software previously, i never had an issue playing any dvd, and I am a netflix whore.


Any help would be great.:popcorn:

---

### Post by mc4man on 2008-03-27
Try opening vlc from the terminal, play hot fuzz and post  output

---

### Post by satn3ver on 2008-03-27
my VLC output:

> VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: HOT_FUZZ
libdvdnav: DVD Serial Number: 36c900a4
libdvdnav: DVD Title (Alternative): WIDESCREEN_R1
libdvdnav: Unable to find map file '/home/sayn3ver/.dvdnav/HOT_FUZZ.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000158
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00013c37
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000457af
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002e43ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002e43b1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002fb278
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002fb27c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003417f0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003417f4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0037b7d1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0037b7d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003dedbd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003dedc1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003e8bf8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003e8bfc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003f0d9a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003f0d9e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003f52fb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003f52ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003f74fe
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003f7503
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 0
[00000295] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
Segmentation fault (core dumped)


I dunno know what it means but i assume its not right considering some core got dumed.[-X

---

### Post by mc4man on 2008-03-27
> my VLC output:
Everything is 100% proper except for vlc crashing - you have everything vlc needs for playback, it's retrieving the decrypt keys at correct locations, correct # of vts's, -  the disk should play. You may be able to gather a little more info by starting vlc in terminal with  vlc -vvv    then open disk and see if anything interesting shows up 
As far as libavcodec the feisty ver. is libavcodec0d - you probably have it installed already
There's a very slim chance that the info in home>.dvdcss (hidden folder) is incorrect, won't hurt to browse to it , find the hot fuzz folder and delete it before trying vlc again

---

### Post by satn3ver on 2008-03-30
The last bit of the  VLC -VVV output where I'd imagine I am having the issue:

> [00000301] main private warning: dts != current_pts (-284993)
[00000300] main private debug: Registering subpicture channel, ID: 2
[00000300] main private debug: Registering subpicture channel, ID: 3
[00000300] main private debug: Registering subpicture channel, ID: 4
[00000300] main private debug: Registering subpicture channel, ID: 5
[00000301] main private warning: backward_pts != current_pts (-33363)
[00000295] a52 decoder debug: emulated sync word (no sync on following frame)
[00000294] libmpeg2 decoder warning: invalid picture encountered
[00000301] main private warning: vout synchro warning: pts != current_date (-50059)
[00000299] main video output warning: late picture skipped (1206918740647492)
[00000301] main private warning: dts != current_pts (-50055)
[00000296] main audio output warning: audio drift is too big (-192000), clearing out
[00000296] main audio output warning: mixer start isn't output start (-73728)
[00000296] main audio output debug: audio output is starving (212675), playing silence
[00000296] alsa audio output debug: recovered from buffer underrun
[00000294] libmpeg2 decoder warning: invalid picture encountered
[00000295] a52 decoder debug: emulated sync word (no sync on following frame)
[00000296] main audio output warning: audio drift is too big (-128000), clearing out
[00000296] main audio output warning: mixer start isn't output start (-49152)
[00000296] main audio output debug: audio output is starving (148676), playing silence
[00000299] main video output warning: late picture skipped (1206918741572258)
[00000301] main private warning: backward_pts != current_pts (83414)
[[B]00000301] main private warning: dts != current_pts (-216885)
[00000296] alsa audio output debug: recovered from buffer underrun
[00000294] libmpeg2 decoder warning: invalid picture encountered
[00000295] a52 decoder debug: emulated sync word (no sync on following frame)[/B]
Segmentation fault (core dumped)


Maybe its just the stupid DVD.


I do have libavcodec0d installed already.




EDIT: Go figure. I deleted the Hot Fuzz folder in my .dvdcss folder and it played fine in VLC  Mplayer and Totem

---

### Post by mc4man on 2008-03-30
> I deleted the Hot Fuzz folder in my .dvdcss folder and it played fine in VLC Mplayer and Totem
the first time you insert an encrypted dvd a folder with the decrypt keys in created in .dvdcss. The next time you try to open the disk vlc (and probably totem) will access .dvdcss first and if a folder for the title is found will use that info instead of parsing the disk. Sometimes due to various reasons that title specific folder will have the wrong or incomplete info (keys) causing the player to crash or only play some of the disk properly
There is never any harm in deleting the folders _in_ .dvdcss, they will be recreated next time you play the disk.

---

### Post by satn3ver on 2008-03-30
And knowing is half the battle. G.I. Joe.


Thanks guys for the help.

---

