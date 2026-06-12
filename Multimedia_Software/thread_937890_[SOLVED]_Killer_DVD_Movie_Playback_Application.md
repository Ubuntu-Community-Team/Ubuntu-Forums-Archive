---
title: "[SOLVED] Killer DVD Movie Playback Application"
date: 2008-10-04
forum: Multimedia Software
---

### Post by coolbrook on 2008-10-04
When are we gonna see it?   I'm looking forward to a seamless installation that will get this functionality going.  I've been through every how-to to get DVD playback working on my system but even if my DVDs start, they'll crash.  I believe it really is the difference between Ubuntu and Win XP at the moment.

---

### Post by terry_gardener on 2008-10-04
i followed the instructions in the thread that is in the stick section. 

i use vlc to play dvd's and they play perfectly. 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

also can you supply bit more info with regard to your problem. 

ie app used, any errors, what happens does it crash the player or ubuntu itself, when does it crash when it tries to start playing or does it play for few seconds/minutes then crash.

---

### Post by wolfen69 on 2008-10-04
i had seamless DVD playback on many computers. never a problem.

have you tried vlc for dvd's?

---

### Post by coolbrook on 2008-10-04
Tried both Totem and VLC.  It plays for a few seconds then crashes.

```
steven@LEONARDO:~$ vlc dvd:///dev/scd0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: MINORITY_REPORT
libdvdnav: DVD Serial Number: 2d42aeee
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/steven/.dvdnav/MINORITY_REPORT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000182
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000106b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00035639
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003e88dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003e88e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003ea0a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003ea0a7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003ebc20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003ebc24
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
[00000334] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000283] main playlist: nothing to play
```

---

### Post by markbuntu on 2008-10-04
Do any other dvds give the same messages?

---

### Post by HyperHacker on 2008-10-04
That could be due to some bizarre copy protection on the DVD that the players aren't able to handle. Surprisingly, even today software players tend to stumble over these. (Why they don't just emulate a standalone player, I don't know. I guess it's more difficult than you'd expect.) You can ask at doom9.org, they have a lot of people very knowledgeable in various fields of video, only problem is they have (last I checked) this silly rule that you have to wait 3 days after registering to post... :roll:

mplayer can play DVDs fairly well, if you're not afraid of the command line. There are no menus, and it has trouble skipping chapters so you often have to manually specify a chapter on the command line, but it plays as well as it plays any other video (i.e. pretty darn well).

---

### Post by coolbrook on 2008-10-05
> **markbuntu said:**
> Do any other dvds give the same messages?Yeah I'm getting the same result.  They look good for a few seconds and then they crash.

HH, I'll give mplayer a try as well.

---

### Post by coolbrook on 2008-10-05
Well mplayer stalled for about a minute or so and then it ran beautifully, but like you said, no DVD menu, and the full length I'm seeing defaulted to director's commentary on one and french on another lol.

---

### Post by mc4man on 2008-10-05
If you haven't already try changing the launch command of vlc. Right click on  Applications -> edit menus, highlight sound & video, right click on vlc properties. Change to vlc %f. Sometimes this helps

---

### Post by timjohn7 on 2008-10-05
vlc plays Zone 2 DVDs perfectly... and the latest version's user interface is superb.
Great app... perfect example of OSS trumping commercial software by far.

---

### Post by SuperSonic4 on 2008-10-05
> **timjohn7 said:**
> vlc plays Zone 2 DVDs perfectly... and the latest version's user interface is superb.
Great app... perfect example of OSS trumping commercial software by far.

You can also pick the region:

```
sudo apt-get install regionset
```

then, in terminal type ```
sudo regionset
``` and pick the region. I changed mine to region 1 to play my imported dvds lol

---

### Post by coolbrook on 2008-12-01
> **HyperHacker said:**
> mplayer can play DVDs fairly well, if you're not afraid of the command line.
I may have figured it out.  If I right click on the mplayer control panel and then 'open disc' the DVD starts and I have access to the controls and the english audio track.  No command line necessary.  I'll stick with mplayer.  At least it will work for the movie.

:popcorn:

---

