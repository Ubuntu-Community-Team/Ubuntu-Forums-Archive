---
title: "Help me please turning my videos to joint stereo without re-encoding them"
date: 2015-08-28
forum: Multimedia Software
---

### Post by barki2 on 2015-08-28
I've made a mistake, so only the left audio channel had been working during the digitalization of old VHS recordings.
So now I have a lot of DVDs or MKVs with this error. I'd like to make them joint stereo (so to duplicate the channels).

**The best would be to make my MKV videos joint stereo without re-encoding them.** If this does not work, then how can I edit MPEG-2 (VOB) files to make them joint stereo before converting them to MKV format?

I'm using HandBrake for conversion, but also have Avidemux GTK installed. I've tried to extract the audio track but only copying that is permitted in Avidemux.

Any help would be appreciated.

---

### Post by tgalati4 on 2015-08-28
Install *vlc*.  Play a video track.  Go to the *audio* tab and select *left*.  See if sound comes out of both speakers.  This would be a mono signal from the left channel but played on both left and right speakers.  Now select *right* channel.  You should get no sound at all since the right channel is not recorded.

So, how many videos do you have to re-encode?  Are the Agony Units worth re-encoding?  Wouldn't instructions to configure *vlc* (since it is multiplatform) be easier if you are sending the videos out?

Use the 80/20 Rule.  Out of the entire video collection, how many are really important (20%)?  Just re-encode those.

Because of the way audio is interspersed with the video in the file, I don't know of a simple way to make a left track into stereo without re-encoding.

---

### Post by coldraven on 2015-08-28
If it was me I'd just press the "Mono" button on my amp.

---

### Post by FakeOutdoorsman on 2015-08-28
If you must re-encode the audio here's the most basic ffmpeg command to [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) (re-mux) video and downmix the audio to mono:
```
ffmpeg -i input -c:v copy -ac 1 output
```
If that works you can then use a bash for loop to do them all.

However, I'd probably re-digitize if having the original and correct audio layout is a requirement, or just use the player/playback system to play it in an acceptable manner as already suggested.

---

### Post by barki2 on 2015-08-28
Thank you for the answers.
Finally I decided to digitize those VHS recordings again, checking the sound this time. I'm 1/3 way through by now.

---

