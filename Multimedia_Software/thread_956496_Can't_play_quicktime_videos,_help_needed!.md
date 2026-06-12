---
title: "Can't play quicktime videos, help needed!"
date: 2008-10-23
forum: Multimedia Software
---

### Post by crazyfuturamanoob on 2008-10-23
As title says, I have problems with quicktime .mov videos. When I try to watch them with totem, I can see them. 
But they run for first like 3fps then it starts to slow down, until it freezes. Yes, I have libquicktime1 installed.
Same problem is for gstreamer + firefox + quicktime videos. What is the problem?

Edit:
Tried many other media players, like kaffeine, mplayer, vlc etc. All of them have the same problem.
Some froze on the first 5 frames. Maybe the problem is with libraries? All of them use the same libs.

Edit2:
Got it working some time ago but forgot to edit.

---

### Post by dalebert on 2008-10-27
I'm having this problem as well. I watched a .mov file in Cinelerra and then again in the default player and got the same behavior.

---

### Post by dalebert on 2008-10-27
I opened the Synaptic Package Manager under System->Administration and did a search for "apple codec". Then I chose and installed alac-decoder and it seems to have resolved the problem. Quicktime files are now playing in both Cinelerra and Totem Movie Player. I seem to recall my problem being somewhat sporadic though so I can't be certain the problem is completely resolved. If it resolves it for you, I'll be more confident.

---

### Post by deveraux on 2008-11-16
I am new to the Ubuntu os and having a few problems with playing media.
I have taken the advice and searched for apple codec in synaptic manager.  installed them and now the movietrailer at apple.com does work, however after a few seconds the screen goes black.  I really need quicktime to work because my online lectures are streamed in quicktime.  would appreciate the help of getting this problem fixed.  

thanks,
Deveraux

---

### Post by 3rdalbum on 2008-11-16
Quicktime .mov is only a container format - what we really need to know is what codecs are being used for audio and video in this file. If you install all the codecs into your system (w32codecs and all the gstreamer- ones) you shouldn't run into problems.

If you right-click on the .mov file and choose "Audio/Video" tab you should be told what compressor is being used, and then we might be able to advise better.

---

