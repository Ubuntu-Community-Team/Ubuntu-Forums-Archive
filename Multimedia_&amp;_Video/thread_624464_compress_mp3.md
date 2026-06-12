---
title: "compress mp3"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by briansvgs on 2007-11-27
I have been using my laptop as my primary mp3 player for a while, and haven't been watching the bitrates of my mp3s for a while. When I go to make an mp3 cd using k3b or brasero now, I can only fit just over 100 songs on a disk as compared to around 300 that I was able to fit before. Is there an easy way to recursively go through the folders and change the bitrates of my mp3s to 64 or 128kbps?

Thanks,
Brian

---

### Post by briansvgs on 2007-11-27
I saw this in another entry on the forum: for x in [ `ls -1 *.mp3` ]; do lame --preset 32 $x new32-${x}; done, but it doesn't work because of spaces in my filenames. I think that the periods interrupt it as well.

---

### Post by rsambuca on 2007-11-27
64kbps???!!!  I can barely stand to listen to the poor quality of 192kbps mp3's!!!  I think you need to clean the mud out of your ears. :)

---

### Post by briansvgs on 2007-11-27
lol.Even still, I still think that I should be able to put more than 100 songs on a single cd, and my cd only plays mp3s and the Atrac3 format.

---

### Post by rsambuca on 2007-11-27
I don't know how you would go about changing your existing ones, but the lame encoder settings on soundjuicer for my mp3's is

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux

You would of course change the bitrate=192 part.

---

