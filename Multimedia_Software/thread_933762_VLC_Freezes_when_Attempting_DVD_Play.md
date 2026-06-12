---
title: "VLC Freezes when Attempting DVD Play"
date: 2008-09-29
forum: Multimedia Software
---

### Post by TrikeKid on 2008-09-29
I tried everything I found to get Totem to play nice with DVD's, with no progress, so I downloaded VLC and set it as default, but it still is non functional. The computer recognizes that there is a DVD in the drive, and VLC will try to play it, but this is all the farther I get.
[IMG]http://i161.photobucket.com/albums/t229/TrikeKid/Screenshot-3.png[/IMG]
What should I do? I don't need to watch DVD's all that often but I like to have everything work for those rare occasions.

---

### Post by mc4man on 2008-09-29
That  might depend on how you set it to be the default player (assuming your using 8.04

 Have you set vlc's launch command to %m (either overall or specific to autoplay

---

### Post by TrikeKid on 2008-09-29
> **mc4man said:**
> That  might depend on how you set it to be the default player (assuming your using 8.04

 Have you set vlc's launch command to %m (either overall or specific to autoplay

Yes, I'm on 8.04

I changed the launch command, now it taunts my by almost playing. The VLC window now expands and just starts to play with one DVD, I tried a different one and VLC just quits, and my Volkerball DVD plays just fine. 
I used the method in this post to change VLC to the default
[http://ubuntuforums.org/showpost.php?p=5861353&postcount=3](http://ubuntuforums.org/showpost.php?p=5861353&postcount=3)

I'm excited that something plays, but Rammstien isn't the most romantic thing to watch with the girlfriend when she's been without a computer all week at school.

---

### Post by mc4man on 2008-09-29
That method's fine, that's how i set vlc as a choice. Why don't you open a terminal, enter vlc and after it opens, with the problem dvd in the drive, go 
file -> Open Disc and then post the complete output from the terminal.

---

### Post by bufsabre666 on 2008-09-30
this might be the obvious thing but i have to ask it, do you have the dvd codecs installed?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

if you dont follow the medibuntu instructions, its easy just follow that page.

---

### Post by TrikeKid on 2008-10-01
> **bufsabre666 said:**
> this might be the obvious thing but i have to ask it, do you have the dvd codecs installed?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

if you dont follow the medibuntu instructions, its easy just follow that page.

Yes, I have all the codecs installed. 

mc4man, I've not yet had a reason to open a program with the terminal, so I wouldn't know how to enter VLC via the terminal.

---

### Post by mc4man on 2008-10-01
> how to enter VLC via the terminal. 

Open a terminal then type vlc (lowercase) and press enter

Then (with the dvd in the drive) on  vlc click File -> Open Disc and then click ok.
Info will start showing up in the terminal, when it stops, copy and paste into a reply

---

### Post by TrikeKid on 2009-03-22
Finally got back around to fiddling with this, this is what I get in the terminal

```
justin@justin-laptop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: ROBIN_WILLIAMS_LIVE_ON_BROADWA  
libdvdnav: DVD Serial Number: 3D9CA617___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/justin/.dvdnav/ROBIN_WILLIAMS_LIVE_ON_BROADWA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c20000. Regions: 1 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000147
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000197
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000476
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00002c40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00002c79
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002a9c87
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002a9cc0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002aaedc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002aaf15
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002bc735
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002bc76e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00329071
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003290aa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00339e1b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00339e54
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_PGCI_UT failed - CRASHING!!!
vlc: vm.c:210: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

```

---

