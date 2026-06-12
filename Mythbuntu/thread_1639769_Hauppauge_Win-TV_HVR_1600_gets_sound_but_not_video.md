---
title: "Hauppauge Win-TV HVR 1600 gets sound but not video"
date: 2010-12-07
forum: Mythbuntu
---

### Post by mikeishooligan on 2010-12-07
I got this card yesterday and it took me a while but I finally got it up and running with mythtv.  However, when I try to watch live TV I get sound but no video.  In fact the mythtv window becomes transparent and I can see my desktop through it.  I can hear the TV and even change channels but I can't see anything.  If I hit esc the mythtv window returns to the main menu and I can see it once again.

I installed mythbuntu on top of ubuntu 10.10. I have an Nvidia geforce gt-220 video card with dual outputs (TV and monitor) that I've been using without problem for some time.

I tried disabling compiz and that had no effect.  I've searched online but can't seem to find anyone that has a similar problem to this.

---

### Post by klc5555 on 2010-12-07
Some initial ideas:

Have you tried running mythfrontend full-screen (which is what it expects) rather than in a window? Might be some odd resolution issue.

Does, um, "listening" to a livetv channel for say a half-hour or so yield a 0.5-to-3.3 Gb file in your recording directory of the shape XXXX_20101207XXXXXX.mpg (where the first batch of Xs will actually be some four-digit numerical channel code and the second batch of Xs will be the 6-digit time stamp for when the 'recording' started)? If there is such a file, does it play (with both video and sound) in mplayer or xine or what have you? If it does, then the Hauppauge 1600 and mythbackend are working correctly and together, and the issue is likely to be something with mythfrontend. Might want to have a look at the mythfrontend log (and post same, if warranted) to see if something odd is being described there.

That at least, is somewhere to start.

---

### Post by mikeishooligan on 2010-12-07
Thanks for the help.

Windowed/Fullscreen made no difference.

You were right about the files though.  I found them and they played fine through vlc, both video and audio so I guess it is a setting with mythfrontend.  Any ideas?

Thanks again.

---

### Post by mikeishooligan on 2010-12-07
more info.  Myth plays recorded tv the same as live, that is the video is transparent.  These files played fine through vlc.  Also, I tried loging into a mythbuntu session and that was worse.  The screen went black and I had no sound.

---

### Post by thatguruguy on 2010-12-07
Have you tried regular .avi files in myth to see if you get the same result?  If those play fine, it may be an issue with the playback profile set for your frontend.  To the playback profile, do the following:

First, go to Utilities/Setup in the main menu.
Click Setup
Click TV Settings
Click Playback
Click through the pages until you get to the page entitled "Playback Profiles."  You can change settings from there.

If this is only happening with recordings from analog cable, you may also want to go to the Recording Profiles section of TV Settings, click on "Software Encoders (v4l based)," and then go into each listed profile and make sure that the width and height are set to 720 and 480, respectively.

---

### Post by mikeishooligan on 2010-12-08
OK, I tried adding some avi files to the media library but they wouldn't show up so I couldn't test to see if they'd play.  I noticed that it said the mythtv user had to have read/write access to the directory.  Could there be a problem with permissions there because my own user is the owner of all those directories, not 'mythtv'.

I have tried out all of the video playback profiles.  Most of them give me no video but the VDPAU profiles all do, however it is a translucent image like a watermark.

Also, I opened the stream from the video card in VLC and it played perfectly so thats more evidence that the card itself is working fine, it's just some problem with mythfrontend.

---

### Post by klc5555 on 2010-12-08
Well, it's definitely mythfrontend, but nothing immediately obvious. So it's time to start checking the logs. In your installation, likely under /var/log/mythtv

Oh, and also, since we know that the 1600 and mythbackend are working, you may try scheduling some recording, record it, and then play it back later as a recorded show from mythfrontend, just to see whether your issue is affecting all playback from mythfrontend, or is having to do only with playback from livetv.

---

### Post by mikeishooligan on 2010-12-08
I have tried playing recorded tv both through VLC (worked fine) and through mythfronted (didn't work).

I've attached the log file.  Hopefully you can make some sense of it because I couldn't.

---

### Post by thatguruguy on 2010-12-08
> **mikeishooligan said:**
> OK, I tried adding some avi files to the media library but they wouldn't show up so I couldn't test to see if they'd play.  I noticed that it said the mythtv user had to have read/write access to the directory.  Could there be a problem with permissions there because my own user is the owner of all those directories, not 'mythtv'.

Yes, it's a permissions problem.  Make sure that the folder that you have your videos in allows others to access the files within it.  

Are you running myth .23 or myth .24?

---

### Post by mikeishooligan on 2010-12-08
whenever I change the permission for the top-level folder to 'read/write' access for others it defaults back to just -- under 'file access' and none of the subdirectories show the updated permissions.  What is the command to do this from the command line?  I apologize, I'm still a bit of a noob even though I've been using ubuntu for 3 years now!

I was initially running .23 but I tried upgrading to .24 to see if that would fix the problem.  It didn't.

---

### Post by mikeishooligan on 2010-12-08
whenever I change the permission for the top-level folder to 'read/write' access for others it defaults back to just -- under 'file access' and none of the subdirectories show the updated permissions.  What is the command to do this from the command line?  I apologize, I'm still a bit of a noob even though I've been using ubuntu for 3 years now!

I was initially running .23 but I tried upgrading to .24 to see if that would fix the problem.  It didn't.

---

### Post by mikeishooligan on 2010-12-09
I solved it.  I had to change the letterbox colour option from black to grey and it worked.

Thanks for the help.

---

