---
title: "Need Some Help With Audio Encoding"
date: 2009-07-04
forum: Multimedia Software
---

### Post by StreetWise on 2009-07-04
Hi there, sorry if this is in the wrong section.

Im new to Ubuntu (and Linux) and have a problem, in windows I had some movies in the .avi container that was set at a frame rate of 23.976.

Now what i used to do was de-multiplex the audio re-encode the audio while time stretching it and then remux it back to the video at 25.000fps.

Now the only programme i can find that will time stretch the audio for me in Ubuntu is AviDemux but the problem their is that when it is done the audio sounds terrible, very static, and for the life of me i cant find an alternative.

So if anyone can find an alternative for me please I would be most grateful and if it is difficult set of commands a step by step how to would me most appreciated:p

---

### Post by StreetWise on 2009-07-04
AnyOne Please?

---

### Post by rsambuca on 2009-07-04
You can use Audacity to change the tempo of the audio track without changing it's pitch.  Save the new audio file, and add it back to the video.  I have had to do this a few times with some of my videos.

---

### Post by StreetWise on 2009-07-04
Thanks for the reply.

Do you know how much i would need to adjust the tempo by if i was going from 23.976 to 25.000

Its Ok I Found The Values I Needed.

Thanks Again For Recommending Audacity Looks To Be A Sweet Program.

---

### Post by StreetWise on 2009-07-05
Does anyone know a command that would do this either with FFMPEG or Mencoder.

---

### Post by StreetWise on 2009-07-06
AnyOne?

---

### Post by rsambuca on 2009-07-07
What exactly are you trying to do?  What format is the video in?  What are you trying to change it to?  What format is the audio?...  Perhaps some more info on codecs and containers.

---

### Post by StreetWise on 2009-07-07
> **rsambuca said:**
> What exactly are you trying to do?  What format is the video in?  What are you trying to change it to?  What format is the audio?...  Perhaps some more info on codecs and containers.


the video is XviD in the .avi containter and the audio is in either .mp3 or AC3, the video only needs the frame rate from 23.976 to 25.000 but i can do that with AviDemux. What im really after is a way to time stretch the audio from a 23.976 video so it will match the 25.000 video.

I have tried doing this with Audacity but it takes a long time to do this and most of the time the audio goes out of sync.

Thats why i was wondering if there is a command for mencoder or ffmpeg which will time stretch the audio so i can re-mux it to the 25.000fps video.

---

### Post by rsambuca on 2009-07-07
Can't you just use Avidemux for that?  Under the Audio tab select Film to Pal conversion, or have you tried that already?

---

### Post by StreetWise on 2009-07-08
> **rsambuca said:**
> Can't you just use Avidemux for that?  Under the Audio tab select Film to Pal conversion, or have you tried that already?

I have tried it m8, it gives me really horrible static output in all audio formats i have tried.

So is their really not an easy way of doing this on a linux machine?

---

### Post by rsambuca on 2009-07-08
Well, for the few times I have done things like this, I have just used Avidemux to change the video, and Audacity to change the audio.  I usually had to time shift the audio by -150 milliseconds to sync the video, though. Probably not the most efficient method, but I rarely have to do it so I haven't bothered trying other methods.

---

