---
title: "Natty: Video Codecs No Sound Sync &amp; Hangs System"
date: 2011-05-11
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2011-05-11
Hello,

Since I upgraded to Natty, I have been having many problems with lack of sound and picture synchronization, and the OS hangs repeatedly always requiring a full reboot.

Also, I recently rebuilt ***ffmpeg*** from scratch for desktop recording/podcasting; and I suspect the souce-built version was replaced during the upgrade.  How do I prevent this from happening in the future?

I have been having the most problems with the ***.avi*** format.

Here is the metadata from one of those videos:

**Video**

  *Dimensions:*   480 x 368   

  *Codec:*           XVID MPEG-4

  *Framerate:*     30 frames per second

  *Bitrate:*           N/A

**Audio**

  *Codec:            *MPEG-1 Audio, Layer 2

  *Channels:        *Stereo

  *Sample rate:   *48000 Hz

  *Bitrate:*           192 kbps

[IMG]http://www.bestshareware.net/howto/img1/how-to-remove-pixellation-from-video-1.jpg[/IMG]

---

### Post by coljohnhannibalsmith on 2011-05-12
Hello,

I just recently read an article on Ubuntu Screencasting and it stated that one or more of the SOX packages is required.  So I added some.  In fact I added all I could find; and the video pixelization and sound-sync problems seem to have disappeared.  Actually, I still get ocassional pixelization; but this goes away immediately; and the sound sychronization remains good...

I've attached a screenshot of the SOX packages I've added; but I suspect:

***libsox-fmt-ffmpeg***

may be the package that corrected this problem.

Can anyone shed some light on why this may have been the solution, or why not???




Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-12
Still having codec problems, just with different videos

---

### Post by andrew.46 on 2011-05-16
> **coljohnhannibalsmith said:**
> Also, I recently rebuilt ***ffmpeg*** from scratch for desktop recording/podcasting; and I suspect the souce-built version was replaced during the upgrade.  How do I prevent this from happening in the future?

Perhaps have a look at the packaging strategy used by Fakeoutdoorsman in this FFmpeg guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and adapt it to your own needs?

---

### Post by coljohnhannibalsmith on 2011-05-16
> **andrew.46 said:**
> Perhaps have a look at the packaging strategy used by Fakeoutdoorsman in this FFmpeg guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and adapt it to your own needs?

[COLOR=Blue]***You think that's air you're breathing now?***[/COLOR]


Thanks man, I'll give it a look...

No, mostly nitrogen...  As my father used to say, ***"Wake up and smell the nitrogen."***:D

[IMG]http://redsquarepools.files.wordpress.com/2010/09/smelly.jpg[/IMG]



[COLOR=Blue]***Thanks Hannibal***[/COLOR]

---

