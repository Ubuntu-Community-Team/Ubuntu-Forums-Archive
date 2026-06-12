---
title: "Totem player, incredibly slow playback, no sound"
date: 2008-11-07
forum: Multimedia Software
---

### Post by Sashin on 2008-11-07
My Totem player can't seem to play any file. When I try to play a video, it goes about 20x slower than it should and has no sound. If I try to move the slider it says some internal error occurred.

I've tried uninstalling and reinstalling, nothing seems to work.

---

### Post by Sashin on 2008-11-07
Bump

---

### Post by cor2y on 2008-11-07
which version of totem , with which backend (totem-gstreamer or totem-xine) is this?
What version of ubuntu?
What is the file type, avi, wmv, mov, mpeg, dvd disc etc?
Did you run totem via the terminal to see what error is generated during playback?

---

### Post by Sashin on 2008-11-08
All formats lag. I'm using Hardy, and the one from synaptic is the version. It's been like this since installing I think which wasn't too long ago.

It worked fine with my last installation.

---

### Post by Sashin on 2008-11-08
Bump!

---

### Post by cor2y on 2008-11-08
Still didn't give me any indication of which backend totem is using or what errors if any happen when launched from the terminal..
But if its the default install of totem then gstreamer will be the backend.
Heres something to try via the terminal
```
sudo apt-get remove totem-gstreamer;sudo apt-get install totem-xine libxine1-ffmpeg
```
Then try playback and again.
Also did you try video playback with other video players to see if its related to totem or if its system wide?
For example using mplayer or vlc instead of totem

---

### Post by andras artois on 2008-11-08
Why not just use VLC? It plays everything perfectly fine.

---

### Post by Sashin on 2008-11-08
Changing to the xine backend didn't work. Now I have new errors, it says I need to install plugins to play most things, however when I play MP3 files I get the same error as before.

I am able to play most files in KMPlayer. But I'd rather use Totem for music and things.

---

### Post by Sashin on 2008-11-08
Bump

---

### Post by nwadams on 2008-11-08
if you have firefox open at the same time it does that sometimes. For me it works fine if I close firefox when trying to watch a video...for whatever reason it doesn't like firefox.

---

### Post by Sashin on 2008-11-09
I don't know why but after installing "totem-mozilla" it now works almost full functionality.

However, some files (particularly big flv files) still say "Internal error occurred" when I move the slider.

---

### Post by Sashin on 2008-11-09
Wait a minute, it had nothing to do with those plugins.
It's virtual box, when I'm running it my Videos don't work. Why would that be?
I'm on Virtual box almost all of the time on another workspace thanks to 3Ds Max and After effects for the convenience of it.

---

### Post by Sashin on 2008-11-09
Can anyone solve this newfound issue?

---

### Post by nalle on 2008-11-09
I have the same issue. Totem goes slow and it and VLC won't play sound at all if firefox has used sound or I have any music playing program on like Audacious.

It would be nicer to get a proper fix for this than just turning all other programs off to watch a movie or a clip.

---

### Post by cor2y on 2008-11-09
If its a firefox issue then its probably related to libflashsuport and pulse audio.
Follow these guides.
Hardy Heron 8.04 : [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)
Intrepid Ibex 8.10 : [http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse](http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse)

---

