---
title: "Always the wrong default audio codec"
date: 2009-10-10
forum: Multimedia Software
---

### Post by iranai on 2009-10-10
Hello everyone,
I am a newer Ubuntu user and there is one problem I'd think that has to have an easy fix, but I just cannot seem to find it.

I play many types of video files as an avid anime watcher.  Some of these files, in particular the matroska mkv files, use dolby, DTS 5.1, etc.  After trying many video players I prefer to use smplayer, which fixes many issues, but brings one more.  When I open the video file, the wrong audio codec is always selected by default.  

Here is the original issue and the fix, which brings up the below Question.  

Issue:
When opening the video, audio would play, but the voices of people would be extremely low compared to the music and other background noise.  By the way, I am using alsa drivers with a Xonar DX sound card on Jaunty to S/PDIF.  For example, I could hear the background music, birds chirping, airplanes flying buy, but would need to crank up my receiver to hear the voices and now the background if deafening.  

Fix:
After searching the web for 6 hours and trying stuff out, I finally figured out one solution.   I can change the codec in smplayer by clicking on the "i" button or accessing "View info and properties" by right clicking on the video playing>options>view info...>select the Audio codec tab>then go down the list and select the proper codec.  If I reopen the file, the settings are saved for the one file.  The audio is now playing correctly.  So for anyone that is really annoyed by someone's voice they maybe can still watch the movie/video with full sound effects with subs by doing the reverse of this fix.  LOL   

Question:
So the question is, is there a way to set the preferred codec for smplayer or system wide for all video programs? Or change a configuration file so it tries the codecs at the top of the list first or something?  Having to manually change it every time for 50 or so 20 minute episodes gets annoying.  
Codecs I have had this issue with so far:
When opened-->changed to
faad-->faac
a52 (liba52)-->hwac3
ffac3 (ac3)-->hwac3
dts (libdca)-->hwdts

---

