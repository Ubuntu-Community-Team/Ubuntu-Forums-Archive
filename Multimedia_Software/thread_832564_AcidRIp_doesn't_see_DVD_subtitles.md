---
title: "AcidRIp doesn't see DVD subtitles"
date: 2008-06-17
forum: Multimedia Software
---

### Post by Shampyon on 2008-06-17
I've tried a bunch of different apps to convert my DVDs to XVid, and the best results I've gotten are with AcidRip. My problem: I have a fair few foreign language movies, so ripping the English subtitles is important, but AcidRip doesn't see the subtitle tracks in any of my ISOs.

I've gotten .srt's from opensubtitles.com, but I've got no idea how to add the .srt to the video in AcidRip, not as soft- or hard-subs.

Failing taking the subs directly from the ISO, is there a way to use AcidRip to add an external subtitle file?

---

### Post by Shampyon on 2008-07-05
Bumping and clarifying.

I messed up when I said "not as soft- or hard-subs." That's pretty obviously impossible. Really should proof-read before I post.

I should have said *"Not as a separate subtitle file, nor as hard-subs."*

It's odd, because I can see the subtitle tracks when I open the ISO in k9Copy, but AcidRip doesn't see them at all.

---

### Post by Shampyon on 2008-07-26
Bump again. Over a month and still no clues. Haven't found any other resources that have given me even the slightest clue as to why AcidRip doesn't detect the subtitles from ISOs.

---

### Post by llama320 on 2008-07-26
I don't have an alternate solution, but I use AcidRip too, and it recognizes my subtitles, so maybe we can fix that problem instead of finding an alternative.

So I imagine you already know what I'm about to say, but just so that we're on the same page:

1) Make sure to mount the ISO
```
mkdir /tmp/bar
sudo mount -o loop -t iso9660 foo.iso /tmp/bar
```

2) choose, under video path: /tmp/bar
3) Under "other stuff" in the general tab, subtitles should be offered beyond a simple <None>

****

Okay, so assuming that's business as usual...have you tried putting in an old-fashioned DVD and seeing if that DVD has subtitles? Does acidrip *ever* give you subtitle options?

Also, have you tried uninstalling, cleaning up your system, and then reinstalling?
```
sudo apt-get purge acidrip
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install acidrip
```

also, you can go into synaptic to make sure that all the dependencies are there. They should be: perl (>=5.6.0-16), libgtk2-perl, lsdvd (>=0.10), mplayer, mencoder. Apt-get should take care of these, but just to make sure

Hope I gave you some ideas. I have no idea what the actual problem might be, but maybe this'll be a start

---

### Post by llama320 on 2008-07-26
Also, I was just thinking about it
and since AcidRip is based on mplayer, you can look at the massive man file for mplayer. I browsed it for a moment, and it seemed like if you were motivated you could probably figure it out.

```
man mplayer
(THEN..)
/OSD/SUBTITLE
```
should get you to a useful place

---

### Post by Shampyon on 2008-07-27
Oh, you're kidding! *Mounting the ISO.* That's all it took! I was opening the ISO directly with AcidRip. Since it detected the movie and was able to convert it I just assumed There was no difference between the way it treats normal ISOs and mounted ones. Mounting it and opening the directory, it detected everything. Four weeks of wringing my hands wondering what was wrong and it was *that simple!*

Thanks for your help :)

(Yeesh, where's my "how embarrasing" emoticon...)

---

### Post by llama320 on 2008-07-27
glad I could help

enjoy

---

### Post by ziemowitzima on 2012-09-05
This was posted long time ago, but I have similar issue and I dont know how to solve it ...
i am trying to rip a DVD (from DVD disc not image.iso) wit subtitles.
I can see option under "other stuff" to choose subtitles.
But still DVD is ripped but without subtitles...

I hope it is solvable ...

best
Z

---

### Post by oldos2er on 2012-09-05
Old thread closed.

It's best for both you and people attempting to help you if you stick with one question per thread. I've moved your other post to its own thread [here]("http://ubuntuforums.org/showthread.php?t=2053689")

---

