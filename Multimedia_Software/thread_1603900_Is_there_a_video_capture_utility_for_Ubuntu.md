---
title: "Is there a video capture utility for Ubuntu?"
date: 2010-10-23
forum: Multimedia Software
---

### Post by Bernie Gallagher on 2010-10-23
On my Windoze machine, I use Replay Media Catcher 4 which runs silently in the background and captures any videos (FLV, AVI, MPG, WMV, etc) on any websites that I happen to go to, and saves them to a folder on my hard drive.

Right now, if I want to save a video that I'm wathing from Ubuntu, I have to go to /temp, guess which file it is, and copy it after it downloads fully but before it finishes playing, otherwise Firefox deletes it from /temp right away.  This is a pain.

Yes, there are screen motion capture utilities in the Ubuntu Software Center, but they're just screen scrapers that result in low quality copies without any audio.  I want something that will actually capture the video stream and save it as a file.

Even if it doesn't save all videos automatically like RMC4, and I have to right click on the video to Save As, that would be better than copying it from /temp at the precise exact moment.

Is there anything like this for Ubuntu?

---

### Post by perspectoff on 2010-10-23
Lots and lots.

You can save .flv, .avi from the web using Video Downloadhelper and a myriad of other Firefox plugins.

There are also screencapture programs (like Recordmydesktop).

See, for example:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Screencasts_and_Desktop_Recording](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Screencasts_and_Desktop_Recording)

or

[http://kubuntuguide.org/Maverick#Screencasts_and_Desktop_Recording](http://kubuntuguide.org/Maverick#Screencasts_and_Desktop_Recording)

---

### Post by Bernie Gallagher on 2010-10-23
Thanks!  I downloaded Video DownloadHelper and the converter for Firefox on both my Ubuntu and Windoze machines.  

I tried it on a few sites and it works very well.  

Comparing VDH to RMC4, well, each has its advantages and disadvantages.

The advantage of RMC4 is that it runs silently in the background (it can also automatically convert videos to your preferred format), so after an extended YouTube session, I have every video I watched stored in /downloads without having to think about it.

One nice thing about RMC4 is that you can navigate away from the page immediately after the video starts.  You don't have to sit and watch the whole video for it to be captured.  RMC4 will still continue to keep the video feed alive even if you shut down your broser and will still download and save the video--excellent for long videos like TV shows, etc.

Another advantage of RMC4 is that it's not a browser plugin.  It's a software app that runs in the background, so it's independent of what browser you use.   Believe it or not, there are occasions I like to use IE on my Windoze machine.

The disadvantage of RMC4 is that I also end up with a lot of crap saved...video ads and other videos I wouldn't have bothered capturing.

Another disadvantage of RMC4 is that it's not available for Linux.

The advantage of VDH is that it's easy to use and lets you select what videos you actually want to save. Just click on the VDH icon on the Firefox toolbar, choose what format you want it converted to (I like AVI), and it'll save it to /downloads.  

Another advantage of VDH is that its behavior is the same on Firefox in Windoze and in Linux.

A disadvantage of VDH is that it requires a lot of intervention.  Click on Capture, then choose which video feed to capture (if the site is sending several parallel videos, ads along with the main video, you have to guess which one is the main video), then choose your conversion, then Save As, then minimuze the downloads window that pops up, then minimuze the DOS/ksh window that pops up when the converter starts.

Bottom line?

I'll use both on my Windoze machine, depending on what types of videos I'm capturing.  And I'll use VDH on my Linux machine.  As I said, they both work well, and it's really just a matter of preference.

---

### Post by perspectoff on 2010-10-23
> **Bernie Gallagher said:**
> 

A big disadvantage of VDH, imo, is that you have to let the video play to completion on the site for it to be captured and converted.  



Not true. You're using it wrong.

Let's say you are watching a YouTube (or some site where its legal to download videos) video and you click on VDH to do a download.

Stop the playing video and VDH will download immediately in the background.

You don't need to watch the video for VDH to work.

---

### Post by Bernie Gallagher on 2010-10-23
Okay.  I edited my answer and I'll try it again.  One time, I closed the page during a video, and didn't get the video saved.  Maybe it was just a glitch with that video.

---

### Post by Enigmapond on 2010-10-23
Just so you know...smplayer has this function and is labled "preview". It works extremely well.

---

### Post by lothard on 2011-03-17
> **perspectoff said:**
> Lots and lots.

You can save .flv, .avi from the web using Video Downloadhelper and a myriad of other Firefox plugins.

There are also screencapture programs (like Recordmydesktop).

See, for example:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Screencasts_and_Desktop_Recording](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Screencasts_and_Desktop_Recording)

or

[http://kubuntuguide.org/Maverick#Screencasts_and_Desktop_Recording](http://kubuntuguide.org/Maverick#Screencasts_and_Desktop_Recording)
is there any for google chrome?

---

### Post by heyandy889 on 2011-03-18
Oh, heck yes. This definitely gives me some reading material. :-D I'm hoping to create Khan Academy-style videos for the C language class at my university.

---

