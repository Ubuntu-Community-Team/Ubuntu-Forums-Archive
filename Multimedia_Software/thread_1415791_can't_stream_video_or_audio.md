---
title: "can't stream video or audio"
date: 2010-02-25
forum: Multimedia Software
---

### Post by tominto on 2010-02-25
Hi all.  I can't seem to stream audio or video from websites (i.e. [http://www.nasa.gov/multimedia/nasatv/index.html?param=public](http://www.nasa.gov/multimedia/nasatv/index.html?param=public))  all I see is a black box, and if I click on the black box I see the words "waiting for video" and then nothing.  This doesn't affect youtube videos.  Anyone have any ideas how to fix this?

Thanks

---

### Post by mc4man on 2010-02-25
I'm on a live lucid cd atm with pretty much nothing installed - was able to get video on the nasa site by installing the gstreamer plug-ins 
(not too much seemed to be going on with the nasa tv atm , static screenshots - all the other videos played fine - both in browser and using totem thru the little arrow box dropdown

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly

```

or additionally inc.  the multiverse ones

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by tominto on 2010-02-25
Thanks for the suggestion, but it didn't help.

I tried following the suggestion in the Comprehensive Multimedia & Video Howto and installed gecko player.  With gecko I don't get "waiting for video" anymore, but when I try to play streaming video, the status bar at the bottom says "connecting..." followed by "cache" in an endless loop.  

Please help!

---

### Post by tominto on 2010-02-26
Ok, I was able to play the videos here: [http://www.apple.com/trailers/](http://www.apple.com/trailers/) as suggested in the how to, but all the videos have a white line running down the left part of the screen.  These seem to be the only videos I can play...with everything else I get the problem mentioned above

---

### Post by tominto on 2010-03-04
Somehow fixed the problem.  I think installing the latest version of flash did the trick.  Uninstalled gecko, and installed vlc and movie player.

---

