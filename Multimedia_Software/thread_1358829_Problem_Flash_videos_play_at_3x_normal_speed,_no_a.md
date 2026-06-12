---
title: "Problem: Flash videos play at 3x normal speed, no audio"
date: 2009-12-18
forum: Multimedia Software
---

### Post by bartonski on 2009-12-18
I'm having a couple of problems playing flash videos: the playback is about 3x normal speed (46s Flash video plays in 15 seconds), also I'm not getting any s
ound.

I used the command 'sudo aptitude install ubuntu-restricted-extras' to install flash (along with all the other neat stuff in that package).

I ran 'locate flash' to make sure that I didn't have any other versions of flash installed. I haven't dug through this in excruciating detail, but I don't th
ink that I have (definitely don't have gnash installed, haven't tried the adobe.com installer yet)


Any thoughts?

Details on my investigation so far:

Hardware        : Toshiba A305-6916
Ubuntu version  : Ubuntu Karmic Koala, 9.10
Web Browser     : Firefox 3.5.5

(From about:plugins)
Shockwave Flash :
    File name: libflashplayer.so
    Shockwave Flash 10.0 r42
MIME Type                       Description        Suffixes     Enabled 
application/x-shockwave-flash   Shockwave Flash         swf     Yes

Flash installation method: sudo aptitude install ubuntu-restricted-extras

Google Searches tried:
ubuntu 9.10 flash videos playing fast 
(No relevent results)

ubuntu flash videos playing fast 
        Videos playback 2x too fast, no audio under vmware
        [http://ubuntuforums.org/showthread.php?t=1141211](http://ubuntuforums.org/showthread.php?t=1141211)


linux flash videos playing fast 
        Older version of firefox/linuxmint install
        [http://forums.linuxmint.com/viewtopic.php?f=49&t=26054](http://forums.linuxmint.com/viewtopic.php?f=49&t=26054)

---

### Post by LuisGMarine on 2009-12-18
Are you using 32-bit Ubuntu or 64-bit?  If you are using 64-bit follow this guide ...

[http://ubuntuforums.org/showthread.php?t=1352617]("http://ubuntuforums.org/showthread.php?t=1352617")

Good luck!

---

### Post by bartonski on 2009-12-18
32 bit. Sorry, should have mentioned that.

---

### Post by bartonski on 2009-12-18
Ok, interesting turn of events. I tried to fire up rhythmbox, and I find that it's doing the same thing. I'm thinking that something's gotten messed up in the audio department, and the flash video is trying to sync to the audio.

... Rhythmbox **was** working a couple of days ago though...

---

### Post by bartonski on 2009-12-18
I'm guessing that the last time that I used Rhythmbox was before I installed Ubuntu-Restricted-Extras. I'm not saying that this is what caused the problem [as a matter of fact, I'm not even going to guarantee that I used it before I installed that package], but I'm just bringing it up as a posibility.

---

### Post by bartonski on 2009-12-18
Solved.

I had set the output device in sound preferences to "RV635 Audio device [Raedon HD 3600 Series] Digital Stereo (HDMI)" rather than "Internal Audio Analog Stereo".

Once I set this back, Rhythmbox worked, as did YouTube videos.

I believe that I had been playing around with the audio devices in an effort to get the built in microphone working on my laptop (this was very much a 'press and guess' affair).

I hope that helps someone else out along the line...

---

### Post by michael37 on 2009-12-19
+1

I actually found Skype to be a good test for the working audio input and output devices, as well as a webcam.  It really lets you pick a device and see which ones work and which one don't.

---

### Post by achusonline on 2011-11-15
> **bartonski said:**
> Solved.

I had set the output device in sound preferences to "RV635 Audio device [Raedon HD 3600 Series] Digital Stereo (HDMI)" rather than "Internal Audio Analog Stereo".

Once I set this back, Rhythmbox worked, as did YouTube videos.

I believe that I had been playing around with the audio devices in an effort to get the built in microphone working on my laptop (this was very much a 'press and guess' affair).

I hope that helps someone else out along the line...
thanks.. that worked great!!!
same problem though i didnt set my output audio device myself.. something changed it and then the whole video playback speed got messed up...

---

### Post by CaptainFuzzyFace on 2012-01-10
Would just like to add my thanks for this thread. Changing my sound back from the HDMI device to the normal audio device fixed mine too.

---

### Post by Charles Merriam on 2012-02-21
FYI, this appears to be a known bug:  [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/657586](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/657586)

---

### Post by ablian on 2013-04-18
> **bartonski said:**
> Solved.

I had set the output device in sound preferences to "RV635 Audio device [Raedon HD 3600 Series] Digital Stereo (HDMI)" rather than "Internal Audio Analog Stereo".

Once I set this back, Rhythmbox worked, as did YouTube videos.

I believe that I had been playing around with the audio devices in an effort to get the built in microphone working on my laptop (this was very much a 'press and guess' affair).

I hope that helps someone else out along the line...thanks a lot .really really helpful

---

### Post by wildmanne39 on 2013-04-18
Thread closed. Please do not post in old threads.

---

