---
title: "Audio player time slides don't move"
date: 2010-12-22
forum: Multimedia Software
---

### Post by bro brian on 2010-12-22
I don't know if this is a codec thing or what....
I'm listening to some music or 2 different programs; Totem movie player, and Rhythmbox music player. I noticed that I cannot advance the music track with the "time slider". Does anyone have any idea as to why this might be?
  All ideas / hunches are most welcome!

PS. The time slider WILL work with a video, just not an mp3

---

### Post by bro brian on 2010-12-24
Actually, what I originally called the "time slide" is actually called the **Seekbar**. I also found the fix for this (or workaround). Go here: _[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/373534](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/373534)_

  This is what is actual post (#30) on the thread:

                 I had the same problem (and it affected Totem and all media players too).  I want to also confirm that installing gstreamer0.10-plugins-ugly solved my problem. For ubuntu/linux noobs that don't understand what that means, open up Terminal and type this:
 =================================================
sudo apt-get install gstreamer0.10-plugins-ugly
=================================================


**The above post fixed my problem! Now, the Seekbar works. **

---

