---
title: "problem AVI"
date: 2009-05-06
forum: Multimedia Software
---

### Post by Bigneil on 2009-05-06
i am struggling get an avi to work properly. they usually play on my pc and on my laptop and also on my dvd player.  this one plays on my desktop after i downloaded VLC. but i cant get it working on my laptop but most anoying of all it wont play on the dvd player. So, i tried converting it with avidemux to see if it would play,still no luck. any ideas?

---

### Post by andrew.46 on 2009-05-06
Hi,

Looks like h264 video in an avi container which is not the ideal mix. Have you used FFmpeg before? It would not be a huge task to convert this file to an mp4 container by simply copying the video over and either copying or transcoding the ac3 sound. I am not familiar with avidemux, can it copy both streams to mp4?

Andrew

---

### Post by khelben1979 on 2009-05-06
I made a search on ffmpeg on sourceforge.net and [here's]("http://sourceforge.net/search/?type_of_search=soft&words=ffmpeg") the result.

[Vive]("http://sourceforge.net/projects/vive/") seems like a good application from the list (haven't tried it myself).

---

### Post by Bigneil on 2009-05-06
thanks for your advice guys,  i will try and convert it to mp4 with avidemux, if doesn't work i'll look up the ffmpeg stuff (great link by the way):guitar:.

---

### Post by xc3RnbFO8P on 2009-05-06
I use **Devede** to convert video files to play in my standalone DVD player.
Non of the codec in Avidemux works in my DVD player.

---

### Post by Bigneil on 2009-05-06
> **Ringi said:**
> I use **Devede** to convert video files to play in my standalone DVD player.
Non of the codec in Avidemux works in my DVD player.

Devide ? i never heard of it before. although my dvd player can play AVI files  i do get the odd one that will not play. perhaps the answer is to convert them into proper DVD's with Devide.  i will give it a try  thank you:)

---

### Post by acimmarusti on 2009-05-06
Try installing codecs. Open up a terminal and do:

```

sudo apt-get install ubuntu-restricted-extras

```

Try again

---

### Post by mikeonthebeach on 2009-05-08
what is a good program for playing avi files

---

### Post by acimmarusti on 2009-05-08
A lot of people use either vlc or mplayer, but I find totem provides everything I need. For all of them, you need codecs first. You can get them by getting the package: ubuntu-restricted-extras as I outlined before

---

### Post by Bigneil on 2009-05-09
Hi all,   i have been using that DeVeDe program. i like it very much. i turned my problematic AVI into an ISO and burned it using K3B and it plays very nicely on my stand alone DVD player.   thanks again for all you advice!:)

---

