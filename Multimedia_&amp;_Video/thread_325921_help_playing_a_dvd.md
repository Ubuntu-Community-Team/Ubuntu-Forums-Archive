---
title: "help playing a dvd"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by doucheone on 2006-12-26
I'm trying to play a dvd I just bought, and I just can't seem to make it happen. When I first popped it in, totem gave me this

```
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
```

So I tried a couple of other players like Ogle and Mplayer with similar results. So I looked around the forum and tried using automatix and installing the dvd codecs through that. Unfortunately, nothings changed.
Any ideas?
thanks

---

### Post by bruenig on 2006-12-26
You do need to install  libdvdcss if you haven't already, not sure if automatix does that or not. It should if it is worth anything. But still after that, I found that vlc is best for dvd playback.
```
sudo apt-get install vlc
```
It is in universe so make sure you have that enabled.

---

### Post by doucheone on 2006-12-26
How do I check if I have libdvdcss installed? (sorry, total newb)
I have vlc, but alas, it's not happening with that either.

---

### Post by doucheone on 2006-12-26
I figured out how to check for that file, and I do have it installed

---

### Post by bruenig on 2006-12-26
For vlc, did you put the disc in, then open vlc, file>open>disc then select the disc location? That has never failed for me. And assuming you have the right codecs, I don't see why it would.

---

### Post by doucheone on 2006-12-26
that's what I'm doing, it's not happening.
thanks for the advice though

---

### Post by doucheone on 2006-12-26
okay so I installed more codecs through automatix, and I can get the dvd working up until I choose an episode and press play, then:

**gxine** crashes
**totem** says I may not have libdvdcss installed, which I do and stops at that point.
**mplayer** won't even open it saying "Fatal error! could not initialize video filters (-vf) or video output (-vo)
**ogle** starts playing the an audio commentary track for about 5 seconds then stops, but the video remains at the menu
**vlc** plays the same audio as abover but for longer, then it goes into the episode, but with no video and the audio skipping every couple of seconds

---

### Post by ngdias on 2006-12-26
I installed libdvdcss2 manually and nothing.
Then I installed Automatix2 and still nothing.

I'm using AMD64 version and currently thoggen dvd ripper says 'maybe you don't have libdvdcss installed' and it shows up in the Synaptics Package Manager...

---

### Post by eeried on 2006-12-29
Read everything at the back of your DVD; if it says copy control somewhere, then perhaps you'll never be able to read your DVD (=DRM). Try to read it on a DVD player connected to a TV set.

---

