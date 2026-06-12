---
title: "Decibel Audio Player..."
date: 2012-08-21
forum: Multimedia Software
---

### Post by omelette on 2012-08-21
**Decibel** is a great little no-frills player, and maybe I'm missing something but even though I'm pretty sure it uses my Apple-format-enabled Gstreamer, I can't get it to play aac-format files.  Not unless I change their extension to 'mp3' or 'ogg' that is!!!

I can't believe this is an oversight or that this hasn't been moaned about by others, so why has the developer opted to the censor the aac-format by filtering this extension, particularly since it's Gstreamer that is doing the actual playing?  And more importantly is there a simple way around it?

---

### Post by omelette on 2012-08-25
Turns out this app is written in Python which was not too painful to hack to allow the playing of *.aac files.  What's immediately apparent is that although the files play perfectly, they seem to use a different 'header' format, the result of which is that track number, artist, album and length are all 'unknowns' in the playlist - only the track title is shown correctly!  I did a search for aac header-specifics to attempt a better bodge but couldn't find anything.  Maybe this is the reason why the developer hasn't included aac support, although I doubt it...

Anyway, I managed to (finally) build a new Deb package with the modification, mainly thanks to this - [link]("https://help.ubuntu.com/community/PythonRecipes/DebianPackage") - and may be downloaded at the below link by anyone interested.

[http://ubuntuone.com/7JXj3Y7XN4crgGUyWmwc31]("http://ubuntuone.com/7JXj3Y7XN4crgGUyWmwc31")

---

### Post by omelette on 2012-10-30
I was feeling bored so i thought I'd add one more comment to this.

Turns out the 'problem' lies with Python's 'mutagen'.  Or not as the case may be - the files with an 'aac' extension are 'raw' ADTS aac-format data which contain no 'meta-data' such as Artist, album etc, so the only data mutagen could extract would be file-length (which it currently doesn't).  In fact, this was raised with the developer as far back as 2009 and has ever since been a low-priority item on the 'TO-DO' list. Link: [http://code.google.com/p/mutagen/issues/detail?id=14#c4](http://code.google.com/p/mutagen/issues/detail?id=14#c4)

It doesn't of course excuse the fact that Decibel is the only multimedia player I have come across that ordinarily will not allow the playing of raw aac files.  Which in my experience are not as uncommon as the above link would suggest - the most obvious example being the stream-captured output of  aac-streams by Streamripper...

---

### Post by omelette on 2012-12-16
Does anyone know how to display the 'Volume Icon' in the Decibel player?

Below are two pics, the first taken straight from the Decibel web-page, showing a little Volume-icon visible in the Play/Pause button area, specifically, directly on the right-hand side of the "Remaining time" counter.  The other picture is what I see when I run Decibel - no Icon!

The reason I need this is that Decibel has a really annoying 'feature' where for some reason it occasionally starts with the audio disabled.  It is possible to adjust the volume via the Preferences/Sound settings but they don't 'stick' and need to be set every time Decibel is started.

---

### Post by anejo on 2013-05-01
Hey... this reply is way, way overdue!
I am sure by now you have this one figured out... but for posterity's sake, the solution is really simple:
add this to the launcher's properities
      --volume-button
 to force a display a volume slide on the app

---

### Post by omelette on 2013-08-28
.....as is my response to your reply! :D :D :D

So if you ever read this, thank you!!! I never did figure it out - your solution works a treat!

---

