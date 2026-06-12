---
title: "[SOLVED] Asus My Cinema P7131 Hybrid - No Sound"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by startherepodcast on 2007-07-10
Hi,

I have an Asus My Cinema-P7131 Hybrid tv Capture Card which seems to be recognized ok in Feisty. I am trying to use mythtv but when I try to watch tv i get a picture but no sound. I have tried most of the solutions for this card that are posted on this forum but with no luck. It seems that in tvtime you can fix the problem by entering a command but with mythtv this would restrict the multimedia functions (i.e Playing DVDs). I was wondering whether there may be another command that would enable me to hear the sound of my capture card and the other sounds.

Thanks,

Adsized

---

### Post by RayVad on 2007-07-22
[http://ubuntuforums.org/showthread.php?t=476263&highlight=tvtime+sound]("http://ubuntuforums.org/showthread.php?t=476263&highlight=tvtime+sound")

---

### Post by startherepodcast on 2007-09-25
Hi,

So in the end i solved it!!

All I had to do was to enter in the terminal:

```
alsamixer -c[MY_DEVICE_NUMBER]
```

(where your device number is your video card, you may need to try a few numbers) and turn up the volume.

If your sound is not working I strongly suggest trying this.

Hope This Helps Someone,

Adsized

---

