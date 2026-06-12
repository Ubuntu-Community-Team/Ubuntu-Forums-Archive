---
title: "King of Kong DVD wont play"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by fooz44 on 2008-02-02
Hello,

I recently got King of Kong from netflix, and it will NOT play on my ubuntu system.  I am trying to watch it with Totem, and here is the story:

Heres what happens.  I open the DVD, and it plays the "NEW LINE HOME ENTERTAINMENT" screen
(Title 5, ch 1)

Then it goes to the previews, (Title 10 and Title 9)

Then the DVD MENU! YES! Play movie!

Then Title 6 informs me that the motion picture has been rated PG-13.  

Then the playlist on the right shows that I am back on the DVD Menu, but the movie is paused.

I click play, and it starts me over at the first step again, ready to watch some previews.

Now, I know whats going on here.  Someone at New Line figured out a really clever way to keep people from ripping their DVDs.  Good for them.  But I am a legitimate user of their DVD, and it's more annoying to me than it would be to a really clever DVD pirate.  How am I going to watch this DVD without buying a dvd player or removing my PC from under my bed?     

Anyway, Im running gutsy with all the latest updates.  I have libdvdcss2 v1.2.5-1, and im not really sure what other packages would be relevant. 

Thanks,
fooz

---

### Post by Incense on 2008-02-02
Follow the directions on the page below to update your libdvdcss2 from the Medibuntu repos, and you should be able to play it. 

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by fooz44 on 2008-02-02
Okay, that got me up to libdvdcss2 v 1.2.9-2medibuntu4, but still no dice, same result.

Also, in totem, going to scene selection causes totem to tell me it cant read it, and asks me if i am using libdvdcss2.  In gxine, doing the same causes a crash.


here is the output from lsdvd in the cl:

libdvdread: Invalid title IFO (VTS_02_0.IFO).

*** libdvdread: CHECK_VALUE failed in ifo_read.c:551 ***
*** for vtsi_mat->vts_ptt_srpt <= vtsi_mat->vtsi_last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:552 ***
*** for vtsi_mat->vts_pgcit <= vtsi_mat->vtsi_last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:553 ***
*** for vtsi_mat->vtsm_pgci_ut <= vtsi_mat->vtsi_last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:554 ***
*** for vtsi_mat->vts_tmapt <= vtsi_mat->vtsi_last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:555 ***
*** for vtsi_mat->vtsm_c_adt <= vtsi_mat->vtsi_last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:556 ***
*** for vtsi_mat->vtsm_vobu_admap <= vtsi_mat->vtsi_last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:557 ***
*** for vtsi_mat->vts_c_adt <= vtsi_mat->vtsi_last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:558 ***
*** for vtsi_mat->vts_vobu_admap <= vtsi_mat->vtsi_last_sector ***

                                                                        
Thanks,
fooz

---

### Post by mc4man on 2008-02-02
It's not going to matter what version of libdvdcss2 you have, your not going to be able to play this title with an open source_ non licensed _player. It will playback with licensed players which in linux is lindvd. (It's playing fine on my box with lindvd right now)

---

### Post by fooz44 on 2008-02-02
Yeah you're right, made by intervideo

what a joke.

---

### Post by Incense on 2008-02-02
That's no good, have you tried to play it in VLC?

> sudo apt-get install vlc

---

### Post by fooz44 on 2008-02-02
Just did. Gets to the menu, I hit play movie, then it shows the Rating screen and DUMPS.   No message, just disappears.

UGH.  SO IF I BOUGHT THIS STUPID DVD I WOULD STILL HAVE TO USE SOME OTHER COMPANY's SOFTWARE JUST TO PLAY IT.  ANGRY.

Edit.  No really:
...
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x002430ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003e8e2b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003e8edc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00024b4c
libdvdread: Elapsed time 0
libdvdread: Found 13 VTS's
libdvdread: Elapsed time 0
[00000352] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
[00000381] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
**Aborted (core dumped)**

---

### Post by SunnyRabbiera on 2008-02-02
stuff like this is getting more common I am afraid, its what we get for living in a microsoft owned world.

---

### Post by fooz44 on 2008-02-02
Well this is why we need open source to protect us from these "HAHA, GOTCHA, MORE MONEY PLZ"  capitalists that really run the world.  Someone will fix up the dvd libs in the next few months probably to make this keep working.  But for right now, this is straight bulls**T.

---

### Post by Incense on 2008-02-02
Wow, that isn't cool at all. MPAA is getting tricky. My only other suggestion would be to see if you can rip it with something like K9Copy, or even dvdshrink, or dvd fap decryptor under WINE, and see if you can at least get the video off of it. Then you can watch the raw files with VLC, or burn it to a DVD. K9Copy will even let you rip to an AVI. Good luck! 

This is why copy protection is bad kids!

---

### Post by ubuntu-freak on 2008-02-02
Please tell me if Part 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) enables you to play it.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-04
I'm still interested.

---

### Post by bkt_uf on 2008-02-06
I ran into this as well.  Some internet searching suggested the culprit is an additional layer of copy protection (featured on recent New Line Cinema releases, among others).  It is possible to use the free (beer) DVDFab Decrypter running under wine to get a playable version as either a directory structure or an ISO file.  I'd be interested if anyone knows a Linux tool that does the job (none of the usual suspects in Gusty did, neither did the new MPlayer (the one with dvdnav support) backported from Hardy).

---

### Post by ubuntu-freak on 2008-02-06
> **bkt_uf said:**
> I ran into this as well.  Some internet searching suggested the culprit is an additional layer of copy protection (featured on recent New Line Cinema releases, among others).  It is possible to use the free (beer) DVDFab Decrypter running under wine to get a playable version as either a directory structure or an ISO file.  I'd be interested if anyone knows a Linux tool that does the job (none of the usual suspects in Gusty did, neither did the new MPlayer (the one with dvdnav support) backported from Hardy).

 
Why do they develope new techniques? Courts keep ruling against them anyway, saying that a buyer of a DVD has the right to play it. It's so idiotic. The industry even tried to kill VHS. 
 
They know nothing and yet think they know everything.
 
Nathan

---

### Post by gsmanners on 2008-02-06
DVDFab Decrypter indeed will get the job done and should run in Wine okay. I consider it a temporary fix for the few DVDs that absolutely won't rip any other way.

---

### Post by mc4man on 2008-02-12
A patch I just heard about  allows playback of the new line titles (at least for the moment) in vlc and mplayer/smplayer 
[http://ubuntuforums.org/showthread.php?t=652528](http://ubuntuforums.org/showthread.php?t=652528)
The method is different for vlc vs.mplayer - both work fine

---

### Post by ubuntu-freak on 2008-02-13
Thanks! Added the link to the troubleshooting section of my [how-to](http://ubuntuforums.org/showthread.php?t=661833). Well spotted!
 
Nathan

---

