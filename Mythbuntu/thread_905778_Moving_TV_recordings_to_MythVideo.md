---
title: "Moving TV recordings to MythVideo"
date: 2008-08-30
forum: Mythbuntu
---

### Post by robbiegregg on 2008-08-30
Hi all,
I was hoping someone out there has enough expertise for this post.  My question is the following:

I have now got alot of movies I have recorded from TV.  However I would now like to transfer these recordings so they can be watched through MythVideo.  The reason why is because I like the idea of being able to browse through my list of movies together with the film artwork which can be downloaded from the IMDB server.

I assumed all I needed to do was move the .mpg files from:

/var/lib/mythtv/recordings  

to

/var/lib/mythtv/videos

Although I can watch these copied movies through MythVideo, I can not fast forward or rewind them.  I am using the Internal Player and after reading other posts I am aware this approach uses seek tables to help fast forward / rewind.  Since I have merely copied the video files across, seek table information will not be available.

I am aware that I could use a different player such as Xine or VLC however I like the idea of using the same player so that the look, feel and user interfaces are identical.

My question is how do I fast forward / rewind video files using MythVideo?  I am guessing I need to somehow populate the MythTV database with seek table data for each movie file I have copied over to the /videos folder however I have absolutely no idea how to do this correctly.  I have already tried mythconverg and myth.rebuilddatabase.pl.  It appears the latter can only add videos to the TV -> "Watch Recordings" list.  I am completely lost! Please help.

Thanks very much for reading this long post.

Cheers

Robbie

---

### Post by robbiegregg on 2008-09-02
Does anyone have any ideas on this one?

Thanks for looking

---

### Post by tgm4883 on 2008-09-02
AFAIK, the seektables only apply to the recordings (which technically I guess this is).  What you might try is creating a user job that transcodes and transfers the movie over to your mythvideo directory (maybe using mythexport).  You will probably save some space doing it this was too.

---

### Post by newlinux on 2008-09-02
I can't remember for sure right now - but I'm pretty sure in the past I have simply copied over a recording and been able to fast forward and rewind... Wait, maybe I only skip forward and backword and direct seek, not actually fast forward and rewind. Can you do any of those?

What types of recordings are these  (software or hardware encoded analog, digital mpeg-2 transport streams)?

What happens when you try to fastforward or rewind? Have you looked at your frontend logs for errors?

---

### Post by robbiegregg on 2008-09-06
Hi all,

Thanks very much for your posts.  In response to New Linux:

> I can't remember for sure right now - but I'm pretty sure
> in the past I have simply copied over a recording and been 
> able to fast forward and rewind... Wait, maybe I only skip 
> forward and backword and direct seek, not actually fast 
> forward and rewind. Can you do any of those?

I also meant to say that it is not possible to skip fowards or backward (i.e. use the cursor keys to skip forward 15 seconds or whatever).

> What types of recordings are these (software or hardware 
> encoded analog, digital mpeg-2 transport streams)?

I'm not too sure really.  How can I find out?  All I know is that they were recorded by one of my DVT Leadtek TV cards (DVB DTV capture card (v3.x)) from TV.

> What happens when you try to fastforward or rewind? 
> Have you looked at your frontend logs for errors?

When I try to skip forward (i.e. press the right key on the keyboard), the video simply does not skip forward - it just carries on playing as if I didn't skip forward at all.  The position bar at the bottom of the screen showing your current position does however appear and even though I am intending to skip only 15 seconds, the position bar moves all the way to the right as if  I want to skip the whole video.

I have looked at my frontend,backend and mythecleome logs (in /var/log/mythtv/).  The mmythwelcome is the only log with something looking relevant.  I have pasted it in below:

***************************************
2008-09-06 07:47:17.320 TV: Attempting to change from None to WatchingPreRecorded
2008-09-06 07:47:17.324 DPMS Deactivated
2008-09-06 07:47:17.470 AFD: Opened codec 0x1cb3b40, id(MPEG2VIDEO) type(Video)
2008-09-06 07:47:17.470 AFD: codec MP3 has 2 channels
2008-09-06 07:47:17.470 AFD: Opened codec 0xfcba30, id(MP3) type(Audio)
2008-09-06 07:47:17.470 AFD: codec MP3 has 1 channels
2008-09-06 07:47:17.470 AFD: Opened codec 0xaf86d0, id(MP3) type(Audio)
2008-09-06 07:47:17.470 AFD: Opened codec 0x1ea2630, id(DVB_SUBTITLE) type(Subtitle)
2008-09-06 07:47:17.471 Opening audio device 'surround51'. ch 6(2) sr 48000
2008-09-06 07:47:17.471 Opening ALSA audio device 'surround51'.
2008-09-06 07:47:17.531 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-06 07:47:17.550 Unable to parse themeinfo.xml for glass-wide
2008-09-06 07:47:17.550 The theme (glass-wide) is missing a themeinfo.xml file
2008-09-06 07:47:17.550 OSD Theme Dimensions W: 640 H: 480
2008-09-06 07:47:17.678 TV: Changing from None to WatchingPreRecorded
2008-09-06 07:47:17.680 Realtime priority would require SUID as root.
2008-09-06 07:47:17.777 Video timing method: USleep with busy wait
2008-09-06 07:47:17.778 WriteAudio: buffer underrun
2008-09-06 07:47:17.804 WriteAudio: buffer underrun
2008-09-06 07:47:23.232 TV: Attempting to change from WatchingPreRecorded to None
2008-09-06 07:47:23.343 TV: Changing from WatchingPreRecorded to None
2008-09-06 07:47:24.434 DPMS Reactivated.
***************************************

If I try to skip back, the video stops playing altogether presumably due to an error.  The log shows the following:

***************************************
2008-09-06 07:51:42.750 [mpeg2video @ 0x7f09445585b0]current_picture not initialized
2008-09-06 07:51:42.750 AFD Error: Unknown decoding error
2008-09-06 07:51:42.751 WriteAudio: buffer underrun
***************************************

I have also had the following error which does indicate there is something wrong with the seektables for MythVideo:

***************************************
2008-09-06 07:50:54.841 AFD Error: av_seek_frame(ic, -1, 19840000, 0) -- error
***************************************


Thanks very much,

Robbie

---

### Post by talvinzijk1 on 2011-01-16
> **robbiegregg said:**
> Hi all,I was hoping someone out there has enough expertise for this post. My question is the following:I have now got alot of movies I have recorded from TV. However I would now like to transfer these recordings so they can be watched through MythVideo. The reason why is because I like the idea of being able to browse through my list of movies together with the film artwork which can be downloaded from the IMDB server.I assumed all I needed to do was move the .mpg files from:/var/lib/mythtv/recordings to/var/lib/mythtv/[[COLOR=#000000]videos[/COLOR]](http://www.conversion-guides.com/mpg-conversion-guide/mpg-to-matroska-guide.html)Although I can watch these copied movies through MythVideo, I can not fast forward or rewind them. I am using the Internal Player and after reading other posts I am aware this approach uses seek tables to help fast forward / rewind. Since I have merely copied the video files across, seek table information will not be available.I am aware that I could use a different player such as Xine or VLC however I like the idea of using the same player so that the look, feel and user interfaces are identical.My question is how do I fast forward / rewind video files using MythVideo? I am guessing I need to somehow populate the MythTV database with seek table data for each movie file I have copied over to the /videos folder however I have absolutely no idea how to do this correctly. I have already tried mythconverg and myth.rebuilddatabase.pl. It appears the latter can only add videos to the TV -> "Watch Recordings" list. I am completely lost! Please help.Thanks very much for reading this long post.CheersRobbieThis is what I'm looking for, Thanks for your effort! It's comprehensive.

---

### Post by nickrout on 2011-01-17
Dealt with very simply in the wiki:

mythcommflag --rebuild --video filename.ext

[http://www.mythtv.org/wiki/MythVideo](http://www.mythtv.org/wiki/MythVideo)

---

