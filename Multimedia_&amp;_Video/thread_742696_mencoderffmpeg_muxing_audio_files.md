---
title: "mencoder/ffmpeg muxing audio files"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by jjhoal on 2008-04-01
Hi , I am trying to use ffmpeg and mencoder to achieve audio muxing, (well I'm not sure if that is how it was called). Based on my googling and forum reading, most of the muxing is overlaying an audio to a video file if I am not mistaken. 

Well what I am trying to achieve here is to merge/mux/mix (Dunno how it is called) two audio files whether for example:

 audio1.mp3 + audio2.mp3 = combineAudio.mp3 wherein the two audio will play at the same time, from the very beginning. I tried to use: cat audio1.mp3 audio2.mp3 > combinedAudio.mp3 and I did merge them but they wont play together, its just they were concatenated, the 2nd audio will play after the other. What I need is to play them at the same time in one file... I hope I made myself clear here. :)

I do believe that is possible but I dont know how to achieve it. What should be the right syntax to do it? 

Thanks and my Regards,
Jjhoal

---

### Post by soga_genzo on 2008-04-03
[sox]("http://packages.ubuntu.com/gutsy/sox") should be able to do this. Install it from the repositories, then:
```
sox -m file1.mp3 file2.mp3 output.mp3
```

---

