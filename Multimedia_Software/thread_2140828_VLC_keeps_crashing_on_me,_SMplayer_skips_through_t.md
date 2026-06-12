---
title: "VLC keeps crashing on me, SMplayer skips through the movie...  Ubuntu 13.04"
date: 2013-04-30
forum: Multimedia Software
---

### Post by Silverflyer on 2013-04-30
I tried watching The Avengers on DVD today.  VLC does not work at all and SMplayer skips from scene to scene without finishing one...  It is very annoying,...

When I try running VLC from terminal this is what I get...

I ran synaptic, no packages were broken and it updated a few.  The problem still persists.

```
jason@jason-b628:~$ vlc
VLC media player 2.0.7 Twoflower (revision 2.0.6+git20130423+r563)
[0x21cc108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: MARVELS_THE_AVENGERS
libdvdnav: DVD Serial Number: 40EC6AC2
libdvdnav: DVD Title (Alternative): MARVELS_THE_AVENGERS
libdvdnav: Unable to find map file '/home/jason/.dvdnav/MARVELS_THE_AVENGERS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000059f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000005bc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000060a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000006e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00002d6b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000031a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00004444
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00004681
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0002d854
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00385e30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x00385e30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x00385e30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x00385e30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003ade61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003ade61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x003ade61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x003ade61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x003debc8
libdvdread: Elapsed time 0
libdvdread: Found 21 VTS's
libdvdread: Elapsed time 0
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.
libdvdread: No VTS_TMAPT available - skipping.

*** libdvdread: CHECK_VALUE failed in ifo_read.c:914 ***
*** for pgc->cell_playback_offset != 0 ***

libdvdread: No VTS_TMAPT available - skipping.

*** libdvdread: CHECK_VALUE failed in ifo_read.c:914 ***
*** for pgc->cell_playback_offset != 0 ***

libdvdread: No VTS_TMAPT available - skipping.

*** libdvdread: CHECK_VALUE failed in ifo_read.c:914 ***
*** for pgc->cell_playback_offset != 0 ***

libdvdread: No VTS_TMAPT available - skipping.

*** libdvdread: CHECK_VALUE failed in ifo_read.c:914 ***
*** for pgc->cell_playback_offset != 0 ***

libdvdread: No VTS_TMAPT available - skipping.
Segmentation fault (core dumped)
jason@jason-b628:~$ 


```

---

### Post by mc4man on 2013-04-30
Maybe it has some structure protection that is messing up dvd navigation.

You could try these with vlc, **I'll assume for the moment dvd drive is /dev/sr0**

To try without menus - (can also be done from vlc's disc  menu but cli may be useful

```
vlc dvdsimple:///dev/sr0
```

Or try to find the real title number for the movie, some structure protections use bogus title #'s. If you have a standalone dvd player (tv) then should be simple or I've read it may be title 35 or 28 for region 1, so 
```
vlc dvdsimple:///dev/sr0#35
```
or 
```
vlc dvdsimple:///dev/sr0#28
```
or
```
vlc dvd:///dev/sr0#35
```
ect.

---

### Post by Silverflyer on 2013-04-30
I tried the steps in this thread and this is what I get now.  I took a screen shot of it.


[http://ubuntuforums.org/showthread.php?t=2084964&page=2](http://ubuntuforums.org/showthread.php?t=2084964&page=2)


[IMG]http://ubuntuone.com/7F9QjXQwq1KFpeA86Xks88[/IMG]

---

### Post by Silverflyer on 2013-04-30
I tried your first command, and it is playing right now.

this is what Terminal says...

```
jason@jason-b628:~$ vlc dvdsimple:///dev/sr0
VLC media player 2.0.7 Twoflower (revision 2.0.6+git20130423+r563)
[0x2103108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdread: Using libdvdcss version 1.2.12 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000059f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000005bc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000060a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000006e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00002d6b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000031a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00004444
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00004681
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0002d854
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0002d953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00385e30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x00385e30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x00385e30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x00385e30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003ade61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003ade61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x003ade61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x003ade61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x003debc8
libdvdread: Elapsed time 0
libdvdread: Found 21 VTS's
libdvdread: Elapsed time 0
[0x7fc350000b78] main input error: ES_OUT_RESET_PCR called
[0x7fc350000b78] main input error: ES_OUT_RESET_PCR called
[0x7fc350000b78] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[0x7fc350000b78] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[0x7fc350000b78] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[mpeg2video @ 0x7fc32c086f00] releasing zombie picture
[0x7fc350000b78] main input error: ES_OUT_RESET_PCR called
[0x7fc350000b78] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !


```

---

### Post by mc4man on 2013-04-30
(don't quite get post 3 ) but if vlc seems to be playing the movie correctly using dvdsimple then would be interesting  - 

While movie is playing,  in vlc's menu > Playback > Title & see which title number is playing (& how many titles are listed

---

### Post by Silverflyer on 2013-04-30
Hmmm, I tried another DVD and it worked just fine...  It must be the Avengers DVD...  Is there a way I can work around this problem in the future?  It seems to be skipping to the next scene without finishing the current one as well.

---

### Post by Silverflyer on 2013-04-30
> **mc4man said:**
> (don't quite get post 3 ) but if vlc seems to be playing the movie correctly using dvdsimple then would be interesting  - 

While movie is playing,  in vlc's menu > Playback > Title & see which title number is playing (& how many titles are listed

Titles listed are 1-99, title 3 is playing.

---

### Post by mc4man on 2013-04-30
> **Silverflyer said:**
> Hmmm, I tried another DVD and it worked just fine...  It must be the Avengers DVD...  Is there a way I can work around this problem in the future?  It seems to be skipping to the next scene without finishing the current one as well.

> **Silverflyer said:**
> Titles listed are 1-99, title 3 is playing.
It's quite possible you're playing the wrong title, many of those 99 are bogus & or have improper nav or other such nonsense.

Try to find the actual main movie title & specify that title # to vlc.
Did you try 35 & or 28?

---

### Post by y2kmagna on 2013-06-23
I have been having the same trouble with Avengers, and as it turns out, always at the same time in the movie. Then it occurred to me, this is graphic content filtering. Always removing the sequences that contain violence. So the question now is, why the graphic filter/parental control, and how to turn it on or off?

---

### Post by SeijiSensei on 2013-06-23
Maybe ripping the DVD with something like Handbrake would remove the controls?

---

### Post by y2kmagna on 2013-06-23
I switched over to Xine. It took me a little time to find the settings, ie dvd drive is /dev/sr0 not /dev/dvd. The movie plays flawlessly now.

---

### Post by mc4man on 2013-06-24
> **y2kmagna said:**
> I switched over to Xine. It took me a little time to find the settings, ie dvd drive is /dev/sr0 not /dev/dvd. The movie plays flawlessly now.

May be that xine use xine-libs version of dvd nav which has always be somewhat immune to most structure protections.  That's why totem-xine was always one of the better dvd players, was too bad when they killed it off in 9.10 (karimic

I always kept a redo of totem-xine around here though the last release it was possible to do in was 12.04 precise, after that no longer possible to hack around issues

---

