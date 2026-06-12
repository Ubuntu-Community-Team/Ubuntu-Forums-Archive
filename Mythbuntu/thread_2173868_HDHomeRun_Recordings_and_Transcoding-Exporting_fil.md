---
title: "HDHomeRun Recordings and Transcoding-Exporting files"
date: 2013-09-11
forum: Mythbuntu
---

### Post by bonelifer on 2013-09-11
My cable company without notice fully removed analog (ie we knew about going all digital, just wasn't given the FULL cutoff date). I'm now having to use my HDHomeRun(was using a PVR-500) that was just being used to watch live shows.  Now I'm having to use it to record, I need to find a solution to replace mythnuv2mkv(which for whatever reason doesn't like the MPEG-2 files the HDHomeRun produces).  I always cut the commercials myself and don't want to change that, but I would like to automate the rest of the process.  I was hoping to find a single userjob script that would allow me to:

[LIST]
[*]First transcode(autodetect(MPEG-2), lossless, remove comm's with the premade cutlist)
[*]Transcode the new file to MPEG-4 using a predefined Transcoder profile.
[*]Allow to place(copy) the recording to a predefined non-storage groups location(I only use mythtv to record, ie I use xbmc to watch).
[*] Leave the final transcoded file in place so I can delete it via mythweb, in-case moving(copying) fails.
[*] Ability to choose to change the nuv file extension to mkv
[/LIST]

Right now I can manually do all three separately, with the third being moved via mythvidexport.py, but I'd rather a) have this all done with one userjob script(ie the transcoding, moving) per show/movie and 2) I don't want it in mythvideo, but in an "incoming" folder that is processed by other means(ie programs I have to rename and sort the show filename and movie names).

I'm running mythbuntu 12.04.3 LTS.

---

### Post by TheFu on 2013-09-12
I do something like this but don't use MythTV at all .... I'm lazy and record using Win7 media center.  Never had any issues with the HDHR3 recording files ... 

However, I have never found a Linux video editing tool that works with cut files and easily lets me tweak them.  Ideas?
Here's how I do it [http://blog.jdpfu.com/ALE/ALE-NW/TV_Remove_Commercials.html](http://blog.jdpfu.com/ALE/ALE-NW/TV_Remove_Commercials.html)  I'm certain it can be improved and made 100% Linux.  At least I hope it can.

---

### Post by bonelifer on 2013-09-12
I use mythtv's built-in editor to cut. Then using it's builtin transcoding I use the autodetect profile with lossless cutting checked off, which will apply the settings I configure for mpeg2.  It honors the cutlist from it's own builtin editor, then I run a custom transcode profile to reduce it in size with MPEG4(XVID).  I was actually hoping someone had already created a mythtv userjob script I could use.

---

### Post by TheFu on 2013-09-12
> **bonelifer said:**
> I use mythtv's built-in editor to cut. Then using it's builtin transcoding I use the autodetect profile with lossless cutting checked off, which will apply the settings I configure for mpeg2.  It honors the cutlist from it's own builtin editor, then I run a custom transcode profile to reduce it in size with MPEG4(XVID).  I was actually hoping someone had already created a mythtv userjob script I could use.

I knew that MythTV and XBMC would honor .EDL skip files, but I didn't know it had an editor.  Which software does the editing and honors .EDL cut files?  I'd love to dump my use of Windows for editing, but I'm unwilling to leave 7MC for recording ... the free channel guide is great.

BTW, I dumped Comcast last year.  Put up a $20 DIY db4 antenna in the attic and pointed it towards the transmission towers based on tvfool.com data for my location.  Basic cable was 30 channels - 50% shopping and religious.  OTA I get 60+ channels ... with 50% shopping and religious. Still, there are local channels that ARE NOT available on any cable system that I've seen. A few of them are movie channels too.  Recorded the famous "Chinatown" movie yesterday with Jack Nicholson.  Comcast started encrypting more and more channels here, so I moved from $150/month to $65/month to $26/month to $0/forever over the last 6 yrs.  Returning their "free" DTV tuner that I'd never used was a happy day. Even saving $300/yr with a good antenna setup makes this useful near most metro areas.  Check my blog for more about my antenna design, build, results ...

---

### Post by bonelifer on 2013-09-12
Mythtv has a builtin editor.  Just go into the view recordings page, hit play, then hit the "e" key.  Left arrow, Right Arrow, HOME, End, Page Up, Page Down, just try them and you'll figure out their use. Use the up and down arrows, to change from Key Frame, Frame, 1 sec, 5 sec, 10 second, 1min, 5 min 10 min increases in jump.  Hit enter to start a cut, go to the end of that cut, hit enter again to define the end point of the cut.   To be clear, I'm talking about using these to cut commercials in a MPEG-2 lossless transcode, then run a second transcode to shrink the entire file down with MPEG-4(builtin). Editor only works on the original MPEG-3 file, so make sure you got it right before transcoding down to MPEG-4(XVID).

---

### Post by TheFu on 2013-09-12
> **bonelifer said:**
> Mythtv has a builtin editor.  Just go into the view recordings page, hit play, then hit the "e" key.  Left arrow, Right Arrow, HOME, End, Page Up, Page Down, just try them and you'll figure out their use. Use the up and down arrows, to change from Key Frame, Frame, 1 sec, 5 sec, 10 second, 1min, 5 min 10 min increases in jump.  Hit enter to start a cut, go to the end of that cut, hit enter again to define the end point of the cut.   To be clear, I'm talking about using these to cut commercials in a MPEG-2 lossless transcode, then run a second transcode to shrink the entire file down with MPEG-4(builtin). Editor only works on the original MPEG-3 file, so make sure you got it right before transcoding down to MPEG-4(XVID).

Is the mythtv editor available stand-alone?

---

### Post by bonelifer on 2013-09-12
It's not. It doesn't have a method of importing files it didn't record itself. Though you could probably find a script that took your old cutlist files and run you stuff through ffmpeg and then do x264 transcode through another script for current ones you have

---

