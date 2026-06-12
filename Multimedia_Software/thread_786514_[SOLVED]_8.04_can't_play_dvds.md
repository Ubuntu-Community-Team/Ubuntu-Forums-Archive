---
title: "[SOLVED] 8.04 can't play dvds"
date: 2008-05-08
forum: Multimedia Software
---

### Post by ataraxia on 2008-05-08
I've already installed the ubuntu restricted extras package, libdvdcss2 and w32codecs but I still can't play any of my dvd's. the vlc player even turned off the power from my dvdrom.

on gutsy the dvds played fine.

I have absolutely no idea what to do.

---

### Post by ubuntu-freak on 2008-05-08
Did you follow the steps in my [sticky thread](http://ubuntuforums.org/showthread.php?t=766683)?
 
Nathan

---

### Post by ataraxia on 2008-05-08
> **reassuringlyoffensive said:**
> Did you follow the steps in my [sticky thread](http://ubuntuforums.org/showthread.php?t=766683)?
 
Nathan

yes I did. I feel like there's something missing even though I've done basically eveything there is to do.

I also tried different rom drives with no result.

I'm doomed.

---

### Post by ubuntu-freak on 2008-05-08
> **ataraxia said:**
> yes I did. I feel like there's something missing even though I've done basically eveything there is to do.

I also tried different rom drives with no result.

I'm doomed.

 
Absolute zero happens? Any error messages? It's not a bad cable is it? I know problems can also arrise from switching drives. Have you tinkered with VLC's settings?
 
Nathan

---

### Post by Kowalski_GT-R on 2008-05-08
> **reassuringlyoffensive said:**
> It's not a bad cable is it? 
 Nathan, it must be my cables too then...:)

exact same thing happening for me.

---

### Post by ubuntu-freak on 2008-05-08
> **Kowalski_GT-R said:**
> Nathan, it must be my cables too then...:)

exact same thing happening for me.

 
It's just one possible explaination. Could also be a configuration error, cos it worked in Gutsy and then was lost in Hardy. If it was me, I'd perhaps just format and install Hardy fresh. 
 
Nathan

---

### Post by mc4man on 2008-05-08
It's worth at least once running vlc from terminal and posting output. 
You may also want to run sudo lshw -C disk to ck. on links

---

### Post by Jammerdelray on 2008-05-08
See my earlier post, had the same problem.

[http://ubuntuforums.org/showthread.php?t=779834](http://ubuntuforums.org/showthread.php?t=779834)

Hope it helps :P

---

### Post by ubuntu-freak on 2008-05-08
> **Jammerdelray said:**
> See my earlier post, had the same problem.

[http://ubuntuforums.org/showthread.php?t=779834](http://ubuntuforums.org/showthread.php?t=779834)

Hope it helps :P

 
He's done all that from my sticky I think.
 
Nathan

---

### Post by ataraxia on 2008-05-09
> **reassuringlyoffensive said:**
> Absolute zero happens? Any error messages? It's not a bad cable is it? I know problems can also arrise from switching drives. Have you tinkered with VLC's settings?
 
Nathan

the cables were fine and I've checked vlc's, totem's and mplayer's settings.
vlc simply shuts down by itself if I try to play a dvd, while totem says "cannot read from resource". mplayer just freezes and then I'd have to force quit.

Nicole

---

### Post by ubuntu-freak on 2008-05-09
> **ataraxia said:**
> the cables were fine and I've checked vlc's, totem's and mplayer's settings.
vlc simply shuts down by itself if I try to play a dvd, while totem says "cannot read from resource". mplayer just freezes and then I'd have to force quit.

Nicole

 
That's the error you get when libdvdcss2 isn't installed properly. Navigate to System > Administration > Synaptic Package Manager and search for libdvdcss2, making sure it's installed. If it is, there must be some communication problem with your system and the drive. How many films have you tried to play? Are they new? Although, the menu should show even with a problematic new DVD.
 
Nathan

---

### Post by ataraxia on 2008-07-08
bump and update:
I bought a new dvdrom but the players still do the same thing. So it's not the dvdrom. Yay, I wasted 26 euros for nothing.

---

### Post by gsp@hardy heron on 2008-07-08
try opening vlc and then drag and drop the file into it.. for me, if i double click or directly opened using ctrl+O i get such errors... PS:kaffeine should do well..
vlc worked fine after installing the available updates!!! :)

---

### Post by Prefix100 on 2008-07-08
type the following in console and post the output.

```
vlc dvd:///dev/scd0

```

---

### Post by ataraxia on 2008-07-09
```
VLC media player 0.8.6e Janus

(.:6254): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: BRIDGET_JONES_THE_EDGE_OF_REAS  
libdvdnav: DVD Serial Number: 323a7f30
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/niksu/.dvdnav/BRIDGET_JONES_THE_EDGE_OF_REAS .map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
[00000283] main playlist: nothing to play
[00000283] main playlist: stopping playback
```

aw crap, is it just the encryption? shouldn't the dvd drive have a decryption module?


//edit: I found this [http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html) and this [http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)
now dvd's work. I can't believe I missed those packs.
(p.s. the bridget jones dvd is NOT mine! :D)

---

### Post by Prefix100 on 2008-07-10
haha,

glad it worked out for you.

---

### Post by funksoulbrother on 2008-07-25
Hello,
I have a similar Problem and did the same as the other user above. I get another error. Can you help me?

VLC media player 0.8.6e Janus

** (.:7216): CRITICAL **: gtk_pizza_set_size: assertion `pizza != NULL' failed
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: HOT_FUZZ
libdvdnav: DVD Serial Number: 37690b7a
libdvdnav: DVD Title (Alternative): HOT_FUZZ
libdvdnav: Unable to find map file '/home/funksoulbrother/.dvdnav/HOT_FUZZ.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000160
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000003e7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00019837
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002b838e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002b8393
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003158bb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003158c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00341428
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0034142d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00343b6b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00343b70
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0035374e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00353753
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0035e352
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0035e357
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00366d19
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00366d1e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003682b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003682bb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0036cae8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0036caed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0036e815
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0036e81a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003720e8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003720ed
libdvdread: Elapsed time 0
libdvdread: Found 12 VTS's
libdvdread: Elapsed time 0

---

### Post by Midgetprawn on 2008-07-25
Me too!!
Although first time I typed in vlc dvd: //dev/scd0 the video played


desktop:~$ vlc dvd:///dev/scd0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 45100C3F___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kjb/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000143
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000069ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00006bb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00006c03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00008968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000089b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000520ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0005214c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0009bab7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0009bb04
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000e5430
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000e547d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0012ebaa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0012ebf7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0017855f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001785ac
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
[00000350] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000345] main decoder error: decoder is leaking pictures, resetting the heap
[00000346] main video output error: picture 0x8473484 refcount is -1
[00000346] main video output error: picture to date 0x847369c has invalid status 6
[00000346] main video output error: picture to display 0x847369c has invalid status 6
[00000346] main video output error: picture 0x847369c refcount is -1
[00000403] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000283] main playlist: stopping playback
kjb@kjb-desktop:~$ vlc dvd:///dev/scd0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 45100C3F___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kjb/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000143
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000069ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00006bb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00006c03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00008968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000089b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000520ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0005214c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0009bab7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0009bb04
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000e5430
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000e547d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0012ebaa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0012ebf7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0017855f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001785ac
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
[00000349] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  90
  Current serial number in output stream:  91
kjb@kjb-desktop:~$

---

