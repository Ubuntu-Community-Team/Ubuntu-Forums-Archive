---
title: "Video Scrambled and Distorted! Please Read..."
date: 2008-04-22
forum: Multimedia Software
---

### Post by Simpotico on 2008-04-22
Okay, I've hit a wall on this one. I'm new to Ubuntu (still in the dual boot trial phase) and I have to say I absolutely love it. It's like meeting that special someone at the bar on a Saturday night and finding out that she doesn't drink more than you do; butterflies. Well, after two days of pounding the pavement trying to find a wine workaround for the Zinio Reader I've thrown in the towel and no, I don't need it for some expensive "technical journal" like some of you Linux geeks claim you do, right, like I'm buying that one. 

Now you without sin cast the first stone. So there I was, watching a "short film" on my Ubuntu movie player when bam; I want to see that again. So I use the little time scroll bar to go back a few moments. You with me so far, It begins playing right along to the point where I decided I couldn't live without seeing again when the image freezes but the sound continues to play; major letdown. I figure, alright, I'll just close the movie player and restart it, always works with MS Windows (oh, did I say a bad word here?). It fixed nothing. The "film" played right to where it froze last time and froze again. Alright, I think, maybe it's a bad media file. I delete and redownload. Coincidence, it did it again. "Frustrated", I open another media file. This time when the movie player starts I've got sound but now the movie image is scrambled and distorted. I close and try opening the media file with my "vlc" player and kaffeine. Same thing, sound plays but distorted and scrambled movie image. Now, before you naysayers start ranting, "It sounds like one of your little 'alternative' films corrupted something special that I wouldn't understand"; this has been an intermittent problem (more like 80 to 90 percent of the time) that I have been experiencing since I first installed Ubuntu and tried to watch Nelson Mandela's interview in the examples folder. And from what I've read I'm not the only one who's been experiencing it, just maybe not quite so colorfully.

A little background on problem, in case you haven't had enough; audio files play just fine except for the distorted visualizations in the media player screen and if you try and rewind manually there's a good chance the music will become choppy and distorted. Starting to sound a little familiar, right? This occurs with all the media players I have installed in Ubuntu. All types of movie files fail to show visualization and imagery. All embedded video online works just fine. Also, maybe not related, maybe it is, sometimes when I start Ubuntu the login music decides to treat me a never ending drum beat until I restart my computer.

Anyhow, aggravated to no end now, I completely remove the movie player from Ubuntu using the Synaptic Package Manager (little novice earing his wings). And guess what, the movies start to play in the vlc and kaffeine movie players. Awesome right, not so fast; I click and drag the vlc player to the middle of my screen and bam, the image becomes distorted again. It's also distorted again in kaffeine too. So, I reinstall the movie player and every imaginable driver that I could find for it and vlc and kaffeine using the synaptic package manager (little padawan fast becoming a Jedi Master) thinking that vlc and kaffeine are just lonely and nothing; I get nothing but scrambled eggs. And just to satisfy my "curiosity", you know, for science, I restart my computer in Windows Xp and all my media files play just fine with the windows media player.

Any help with this BUG would be greatly appreciated. Nothing else I've found in the forums so far has been able to help. I've only been doing this Ubuntu thing for going on two weeks now so I really need a "Ubuntu for Dummies" explanation to fix this. 

Thanks in advance.

---

### Post by cor2y on 2008-04-22
what is the media file type ?
avi? wmv? mov? rm?
Sounds like its either an old codec problem, a decoder problem with the media player,  your video drivers or desktop effects are you using compiz-fusion etc?
You say with vlc etc  its distorted when you move the player window or seek forward or back using the playbar , the only media types that i know of that vlc has problem decoding is asf/wmv anytime you play with the progress bar moving it forward and back you get artifacts in the video and older encoded mpeg4 vids talking about old versions of the divx codec and xvid that at the time was considered encoded correctly but now the profile used is considered invalid sometimes the image will freeze on screen while the audio continues to play, samething happens in totem-xine, totem-gstreamer as well i would suggest trying mplayer, is kaffine just a front end for mplayer? i can't remember if it is. Don't forget to add the w32codecs or w64codecs if you are in 64bit ubuntu. To get them use the medibuntu repos [www.medibuntu.org](www.medibuntu.org).

---

### Post by Simpotico on 2008-04-22
Thanks for the response,

Unfortunately all types of movie files; mpg, mpeg, avi, divx, ect. have displayed the same problem. I've tried to play them with; kaffeine, movie player, vlc, and xine. All have the same problem. However, just to make this a little more of a conundrum, when I try to take a screen shot check out what I get. It's absolutely perfect. What gives??? Again, I've had this problem since I first installed Ubuntu 32 bit and it's default media player gave me the same jacked up video.

---

### Post by cor2y on 2008-04-22
are desktop effects enabled? aka compiz. compiz-fusion or beryl?

---

### Post by Simpotico on 2008-04-22
Okay, I got into the Compiz-Config Settings Manager. Check out my screen shot to see what I have. I also included a desktop snapshot this time of the video effects I've been experiencing. Hopefully it comes out... one minute it shows the scrambled effects the other just a black image.

Thanks

---

### Post by cor2y on 2008-04-23
go down a bit in the compiz settings and enable the ability to play/render videos in compiz-fusion its a bit lower down with the options to enable glib and svg and take a screenshot, i believe those should be enabled also gstreamer (the version in 7.10 ubuntu) has a bug that it can't render out movies with compiz-fusion  enabled unless you set the video acceleration to x11 instead of XV if you don't want to change your x video output then use totem-xine instead.
In 8.04 this bug was fixed.

---

### Post by Simpotico on 2008-04-23
I think I've enabled everything you've recommended. I just hope I didn't miss anything. But at this rate I may just have to wait until tomorrow to upgrade to Ubuntu 8 and see if that fixes it... If you have any more suggestions I'd love to try them.

Thanks

---

### Post by cor2y on 2008-04-24
Sorry i took so long to reply been away. :)
Anyway the good news is gstreamer and all its plugins are working for compiz-fusion with hardy heron.
The bad news is make sure you install all of the gstreamer plugins for the ability to playback all media types.

---

### Post by Simpotico on 2008-04-27
Ubuntu 8 upgrade resolved the issue...

---

