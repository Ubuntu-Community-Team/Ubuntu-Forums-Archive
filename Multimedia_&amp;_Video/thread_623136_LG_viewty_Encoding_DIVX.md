---
title: "LG viewty Encoding DIVX"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by waz000000 on 2007-11-25
Hi i have an LG viewty mobile phone that plays DIVX. it comes with a windows drag and drop converter for movies that works like a charm. 

However ive since move over to ubuntu and ive figured pretty much everything out i need to in order to get my things working, the one thing stopping me is this conversion problem ive got. 

i need to encode xvid to divx 320:240 25 or 30fps that's about all i know but ive tried loads of things from vlc to mencoder and i just cant seem to get a working divx (on my mobile). 

Can anyone please give me some advice ive been struggling for a while now and it's driving me mad! 

Many thanks.

---

### Post by lipilee on 2008-02-12
(Never mind me, I thought you had a different problem - sorry.)

---

### Post by morganGDFP on 2008-03-13
I have the exact same problem..please help us out here someone..

---

### Post by weekesd on 2008-03-26
I found this works for me for converting iplayer downloads, should work for other content:

mencoder "The Mighty Boosh: Series 3 - The Crimp.mov" -ovc lavc -oac lavc -lavcopts 
acodec=mp3:abitrate=128 -vop scale=400:240 -ffourcc DX50 -o "The Mighty Boosh - Series 3 - The Crimp.avi"

Important that you use "scale=400:240", "acodec=mp3" and "-ffourcc DX50" I think.

Try this as-is first, and if it works you can use it as the basis of experiments to tweak bit-rates, etc to save space.

---

