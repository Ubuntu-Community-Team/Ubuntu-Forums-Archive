---
title: "ffmpeg/mtv format"
date: 2011-01-22
forum: Multimedia Software
---

### Post by mystmaiden on 2011-01-22
I'm still trying to find out if my coby mp3 player will actually play mtv video files as is advertised.

ffmpeg -formats does list mtv 

but the only command I really ever used was one to convert a vid to an mp3 so I tried

```
ffmpeg -i test.mp4 -acodec copy output.mtv
```

it returns 

```
Unable to find a suitable output format for 'output.mtv'
```

I can't find any mtv files online for purchase or free for that matter, so I know this is all pretty obscure but shouldn't there be a way to convert them since ffmpeg lists mtv format? Anyone have suggestions?

thanks

mystmaiden

---

### Post by ron999 on 2011-01-22
Hi

There are some mtv samples here:- [http://samples.mplayerhq.hu/mtv/]("http://samples.mplayerhq.hu/mtv/")

mtv doesn't show up in my list of ffmpeg formats, but I can play the samples using ffplay and VLC

Edit
Yes it does show _**MTV**_ format supported for decoding.

---

### Post by mystmaiden on 2011-01-22
Thanks for the reply. I tried to dl one of the samples but it showed up looking like a text file. I tried it in the player but it said 'unknown format'.  

looks like its back to the drawing board

---

### Post by BicyclerBoy on 2011-01-22
Right mouse click: Save link as blah....

ffmpeg -i filename

Input #0, MTV, from '/mythstore/storage/Videos/Santana__Im_Feeling_You_www_mympxplayer.org.mtv':
  Duration: 835:42:24.00, bitrate: 0 kb/s
  Stream #0.0: Video: rawvideo, rgb565le, 96x64, 16 fps, 16 tbr, 16 tbn, 16 tbc
  Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 0 kb/s

ffmpeg -formats e  (| grep MTV)
D  MTV             MTV format
This means ffmpeg only decodes MTV , not an encoder for MTV.
So you cannot use this program to make MTV files.

---

### Post by mystmaiden on 2011-01-24
Thanks for the reply, BicyclerBoy. I did right click and save link as, not sure why it looked and behaved like a text file... 

> This means ffmpeg only decodes MTV , not an encoder for MTV.
So you cannot use this program to make MTV files.

Thanks for that, too. I was mistakenly under the impression that if it was listed you could do either. I haven't found anything that actually will work to convert to mtv files with linux yet. I'm not sure how much time I'd spend watching little tiny videos on my mp3 player, just would have been nice to check it out. 

appreciate the help :)

mystmaiden

---

### Post by BicyclerBoy on 2011-01-24
There is/could be/should be a conversion program for Win95 that comes with the player..
Try installing with Wine (on Linux)...

MTV coby video max 96x64 at 15fps.

---

### Post by mystmaiden on 2011-01-26
thanks again, I'll give it a try as soon as I get wine up and running :)

---

