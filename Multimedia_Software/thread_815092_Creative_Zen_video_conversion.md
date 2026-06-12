---
title: "Creative Zen video conversion"
date: 2008-06-01
forum: Multimedia Software
---

### Post by Benjamin_Vedder on 2008-06-01
Hello

I have an Creative zen portable media player with the ability to play XVID-encoded videos. Then problem is: i can encode videos and play them, but i CANT seek in the video. BUT, when i put the same video on an SD-card and put in the player then i CAN seek in the video. 

When i encode videos i use mencoder with these parameters:
```

mencoder "$INPUT" -o "$OUTPUT" -aid 0 -sid 0 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=800:vhq:keyint=250:threads=2 -ffourcc XVID -vf scale -zoom -xy 320 -oac mp3lame -lameopts cbr:br=192

```

I use gnomad2 to transfer the video, and i have seen other people with the same problem, but unfortunately i could not find any solution for this.

[http://www.anythingbutipod.com/forum/showthread.php?p=220306]("http://www.anythingbutipod.com/forum/showthread.php?p=220306")

I dont think it is gnomad2, because when i transfer the video back to the computer from the player the video becomes seekable again.


Another problem i have encountered is that im not able to re-encode movies with vorbis audio codec. The conversion works fine for some minutes, and then stops with the error:
```

Pos: 236.8s   6306f (24%) 134.00fps Trem:   2min  92mb  A-V:0.063 [624:191]
Too many audio packets in the buffer: (4096 in 1081043 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

```

This only and allways happens when the movies i try to re-encode have the vorbis codec for the audio.


Any ideas? Help much appreciated.

---

### Post by Benjamin_Vedder on 2008-06-01
BTW, has anyone successfully converted seekable videos for the creative zen? If yes, how did you accomplish that?

---

### Post by Benjamin_Vedder on 2008-06-08
Bump.. still not found a solution for the seeking, but made some progress. When i copy one of the videos that came with the zen to my computer, rename it and copy it back, its not seekable anymore. It does not matter if i use gnomad2 or mount the zen as an device to copy the video, the video JUST WONT BECOME SEEKABLE!!. I have wasted so much time on this now, and not solved it. Can anyone help me, or is there nothing i can do about this?

---

### Post by daw3b on 2008-06-10
> **Benjamin_Vedder said:**
> Can anyone help me, or is there nothing i can do about this?
Hi, i think there's no solution until now.
The only workaround I found to made video seekable in ubuntu is use your
zen as massive storage and copy the video to the SD card

---

### Post by ikus060 on 2008-06-18
Hi Benjamin,

I have a similar problem with iPod and it's not related to the video it self but to the application I use to transfer the video to my iPod. Maybe it's the same problem for you.

---

### Post by ben::zen on 2008-07-04
Have you ever stopped the video just after starting, then gone back into the video? (I have a Zen Vision:M, and this works for me, but other ones might work differently.)

---

### Post by mcallenSchmee on 2008-07-27
Banshee works, but you must use a version that handles video. Version 1.0 from getDeb works. [http://www.getdeb.net/app/Banshee](http://www.getdeb.net/app/Banshee)

---

### Post by Emess on 2008-08-19
My Zen is also unable to seek video's when transferred with Gnomad2. Howver if I pause, exit, and re-enter the video, it fixes itself and seeks normally. Some video's, even just pausing and starting again fixes it without exiting. Hope that helps anyone~

---

### Post by anthony.phipps on 2009-02-20
same. gnomad2 fails to transfer the index data. im still looking for a solution...

---

