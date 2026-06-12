---
title: "Embedding a .srt subtitles file into a .avi video file"
date: 2009-06-16
forum: Multimedia Software
---

### Post by mammalsauceman on 2009-06-16
I have a .avi video file, and a .srt subtitle file to go with it. I want to show this to my friend on his comp. but he uses a mac, and uses quicktime for his videos (which does not support external subtitle files. Does anyone know a piece of software that can embed subtitles into videos. I tried AVIDEMUX, but that doesn't work. Any help appreciated!

---

### Post by ohzopants on 2009-06-16
I don't think .avi files support embedded subtitles.  I know for a fact that .mkv files do.

You will likely need to transcode the file into an mkv.  Handbrake is a fantastic utility for doing this, but it does not support proper subtitle "embedding" it hard burns the subtitles into the file. (see here: [http://trac.handbrake.fr/wiki/Subtitles](http://trac.handbrake.fr/wiki/Subtitles))

Now that I've typed the long solution, here's the easy one: tell your friend to download VLC, it is cross platform and reliable and it supports external subtitles.

---

### Post by gigaferz on 2009-07-19
[http://en.flossmanuals.net/Avidemux/OverlayingSubtitles](http://en.flossmanuals.net/Avidemux/OverlayingSubtitles)


it didnt work for me..... but still you can try

---

### Post by matamoscas on 2009-07-20
I was a long, long time mac user, and tbh, quicktime stinks for viewing avi, divx, or anything non-apple.  The best thing to do, if you can, is convince them to download and use mplayer. It works great on the mac, and does not have the same limitations of the quicktime player.

---

### Post by _Q_ on 2009-07-20
Does anyone know how to embed vobsubs (idx+sub) into an avi file?
Possibly with mencoder, but how? (since it doesn't recognize idx+sub combination with the -sub parameter, and the -vobsub parm. is only for Mplayer) :/

---

### Post by vinan on 2009-12-26
Hi there

Fellow this utube guide, 

Avidemux

[http://www.youtube.com/watch?v=mNt6mEQ658s](http://www.youtube.com/watch?v=mNt6mEQ658s)  :guitar:

cheers 
Vinan

---

### Post by aala on 2010-08-04
For embedding subs into .avi video...

```
transcode -i videofile.avi -x mplayer="-sub subfile.xxx" -o outputfile.avi -y xvid
```

for more explicit help!...
```
transcode -h |more
```

---

### Post by beliyyal on 2010-08-06
> **aala said:**
> For embedding subs into .avi video...

```
transcode -i videofile.avi -x mplayer="-sub subfile.xxx" -o outputfile.avi -y xvid
```

for more explicit help!...
```
transcode -h |more
```

Hey, this worked for me, but the output file was smaller than that of the original video file. Is this normal? And will it affect quality?

---

### Post by cereja on 2010-09-22
Worked for me too, but the audio sync was gone...
 
How to preserve the audio sync ?
 
My audio was delayed by about 3 seconds on the beginning of the film, but much more than this at the end. A simple 3s lead time was not successfull !

---

### Post by emathias on 2010-11-24
> **gigaferz said:**
> [http://en.flossmanuals.net/Avidemux/OverlayingSubtitles](http://en.flossmanuals.net/Avidemux/OverlayingSubtitles)


it didnt work for me..... but still you can try


It didn't worker for me in the first time either.

But I selected the font by hand (the default one didn't exit in my system ) and now it works.

Hope this helps.

---

### Post by Salahare on 2011-10-15
> **cereja said:**
> Worked for me too, but the audio sync was gone...
 
How to preserve the audio sync ?
 
My audio was delayed by about 3 seconds on the beginning of the film, but much more than this at the end. A simple 3s lead time was not successfull !
The problem there is actually your frame rate. You'll need to set it to as close to the original frame rate of your video in order to maintain audio sync - the average is 30fps, but 24- and 25fps are almost as common. Being still very new to shell commands, I do not know exactly how to specify that...

---

### Post by andoni on 2011-10-21
> **cereja said:**
> Worked for me too, but the audio sync was gone...
 
How to preserve the audio sync ?
 
My audio was delayed by about 3 seconds on the beginning of the film, but much more than this at the end. A simple 3s lead time was not successfull !
I've got exactly the same problem... could someone shed some light on this?

---

### Post by andoni on 2011-10-23
> **Salahare said:**
> The problem there is actually your frame rate. You'll need to set it to as close to the original frame rate of your video in order to maintain audio sync - the average is 30fps, but 24- and 25fps are almost as common. Being still very new to shell commands, I do not know exactly how to specify that...
Does someone know how to do this?

---

