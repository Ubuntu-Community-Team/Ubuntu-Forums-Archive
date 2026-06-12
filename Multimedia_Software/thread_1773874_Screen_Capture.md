---
title: "Screen Capture"
date: 2011-06-02
forum: Multimedia Software
---

### Post by TheExposedOne on 2011-06-02
I know this issue has been posted several times but none seem to fit to my likings
I have tried:
Istanbul
gtk-recordmydesktop
VLC
XvidCap
RecordItNow
Tibesti
GLC
 
These all lag



I used to use Kazam but since the natty upgrade, it hasn't been updated
The unstable build lags also
 
This is for games so a speedy non resource hogging screen recorder would be good
 
Also i've tried fraps in wine, big NO
I have tried Hypercam, also big NO
 
If someone could recommend me a good screen recorder
Thanks

---

### Post by Bonster on 2011-06-02
For games recording people usually use '**glc**' is like fraps for linux. Its a commandline tool. Search online if u want to learn how to use it

---

### Post by FakeOutdoorsman on 2011-06-02
I use this: [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026).

---

### Post by TheExposedOne on 2011-06-03
ffmpeg seems a too long winded, for a short video
I checked glc but the site seems to be down and it doesn't seem to be in the repos

edit: the site was moved checking it out now thanks
edit2: It's way too long winded, is there an easy app with a simple record and stop button, that also doesn't cause lag
edit3: trying out tibesti
Edit4: It lags also
Edit5: I like ffmpeg actually, it doesn't lag too much!

A little help need, it records from mic but doesn't record the speakers
and is there a way to set the framerate it records at?

Edit6: I can change it so it records system or mic audio, but how can i do both

---

### Post by Bonster on 2011-06-03
you can use vlc to allow u to record both mic and speaker, just run this command

> vlc alsa://plughw:0,0

if it fails try this, and repeat again

> killall pulseaudio

and setup your pulseaudio and sound mixer to enable mic

---

### Post by FakeOutdoorsman on 2011-06-03
> **TheExposedOne said:**
> and is there a way to set the framerate it records at?
Step 1 from the link above includes the *-r* option which adjusts your frame rate. Note that your computer may not be able to handle high values.

> **TheExposedOne said:**
> Edit6: I can change it so it records system or mic audio, but how can i do both
I'm not sure. You might want to ask this on the screencast guide thread.

---

### Post by Joseph Schwenker on 2011-06-03
I'm being frustrated by this, too. Best utility I've ever came across is Kazam Screencaster, but it's clearly not for games, and it works horribly with them, though it does record them. I just tried recording a video of Lugaru with GLC, and I can't even get it to encode. It keeps throwing an error. 
I went on the #glc channel on freenode, no response. Their website is down, and the program itself is horribly documented.
What we need is for either someone to put a really good guide out for GLC, or someone needs to give GLC a major makeover.

---

### Post by TheExposedOne on 2011-06-04
Can i disable real-time encoding in ffmpeg

---

### Post by TheExposedOne on 2011-06-05
bump, i would like to know as it would greatly improve the frame rate of the video

---

