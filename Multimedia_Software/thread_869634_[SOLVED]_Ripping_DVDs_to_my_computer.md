---
title: "[SOLVED] Ripping DVDs to my computer"
date: 2008-07-25
forum: Multimedia Software
---

### Post by TroyDowling on 2008-07-25
Hey forum goers,

So, I've built up a fairly large DVD collection over time and I want to start ripping the DVDs to digital files so that I can store them on my dandy new Xbox Media Center. (Hey, I had an old xbox and a cheap intuition, what can I say?). If at all possible, I would like to have the movies in nice sized files around the 700MB mark like those you can find from unscrupulous sources a la BitTorrent networks. I've been trying to accomplish this with DVD::Rip for a while and I'm getting nowhere. Inevitably I run into strange problems that never seem to end. I also read about two programs to accomplish this on Windows (DVDecryptor and AutoGK), but if I can at all avoid it, I would not like to install Windows at all. Can any one give me help with what I'm trying to do. If it's an issue with legality let me know? I wasn't sure when I posted this thread and I know that if it is an issue it probably won't be appreciated in the forums! However, I personally don't see the problem with it because I own the movies anyways. Thanks in advance.

Oh, and also, I presume that the DVDs have security features to prevent pirating thereof. They range to very new like 'I Am Legend' to a little older like 'Gladiator' or 'Saving Private Ryan' and 'Minority Report'. Any help on the matter would be *greatly* appreciated.

Troy.

---

### Post by kpkeerthi on 2008-07-25
Try acidrip. Available in synaptic.

---

### Post by TroyDowling on 2008-07-25
Mm, thanks for the tip. I quite like AcidRip's interface. However, when I start a rip, it inevitably fails with a "Mencoder was interrupted" error. dvd::rip didn't give me a specific error most of the time, rather it have me useless info that always changed. Could there be a problem with my installation of MEncoder by any chance?

Version:
```

MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

```

I know my chip supports SSE3 as well... Hmm.

I browsed the man pages for MEncoder, haha, I was quite frankly blown away at the scope of this program... I definitely don't want to have to tinker with the countless flags and options, but if anyone possibly knew some good "recipes" for it, or a cookbook on MEncoder that would be pretty awesome.

Thanks,
Troy.

---

### Post by TroyDowling on 2008-07-27
Bumpity bump.

I tried experimenting with MEncoder to see what I could accomplish. In the long and short of it, I came up with a command that should do what I'm wanting in this thread. Rip a DVD to my computer. The command I used was:

```

mencoder /dev/scd0 -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=630 -vf scale -zoom -xy 640 -oac mp3lame -lameopts br=128 -o Movie.avi

```

Every time I run that however, I get the following error after a vast amount of "AC EOB Marker is absent" errors:

```

Error while decoding frame!3.21fps Trem:   0min   0mb  A-V:0.000 [6071:0]
Pos:   2.3s     70f ( 0%) 13.40fps Trem:   0min   0mb  A-V:0.000 [6071:0]
Too many audio packets in the buffer: (70 in 8400000 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 6071.012 kbit/s  (758876 B/s)  size: 1747163 bytes  2.302 secs  70 frames

```

If I try and use the -ni flag, MEncoder just tells me that the flag doesn't exist! Right now I'm experimenting with a tool called 'dvdbackup' but it doesn't look to do what I want anyways... I'm quite at my wits end with all this ripping business. Does anyone have any suggestions? If I can't find a solution by Monday, I''ll just dual-boot my old XP license for a while, while I rip my library.

Troy.

---

### Post by TroyDowling on 2008-07-28
**Bonehead Mistake Alert**

So, I solved my problem today. I'm still kicking myself a bit for not immediately thinking of it. The reason that all attempts failed at ripping and transcoding the DVDs was because I didn't have the appropriate codecs and tools installed. It hit me like a tonne of bricks while I was tinkering around with different container formats for a movie I was trying to rip when I thought about it. The Mediubuntu repository has everything you would need to solve this problem. [Head over there](https://help.ubuntu.com/community/Medibuntu) for a detailed guide on installing everything you need to fix the problem I had.

On a side note, I found that the best way to rip movies was not with those tools above. I produced far superior quality rips by first backing the dvd up with 'dvdbackup' and then transcoding the results of that with HandBrake. Obviously, substitute your own input and output paths.

```

dvdbackup -i /dev/scd0 -M -o /media/Storage/Movies/myMovie

```

Which creates a decrypted copy of the DVD on your hard drive. The video files (.vob files) are fully playable in MPlayer and VLC at this point. Then I made it into a suitable format using [HandBrake](http://handbrake.fr/). Note, I dropped the handbrake executable onto my path so I could run it like normal using the command:

```

mv HandBrakeCLI /bin/handbrake

```

```

handbrake -i /media/Storage/Movies/myMovie/VIDEO_TS -f avi -o /media/Storage/Movies/myMovie.avi --preset="Classic"

```

Again, substitute your own values for the -i and -o flags or as you see fit. This takes the input from the decrypted DVD files and transcodes them into an avi file using the presets for a Classic film. This is just the method I use anyways it works perfectly for me. Grab what you need below:

dvdbackup - in the repositories under the universe I believe
HandBrakeCLI - [here](http://handbrake.fr/?article=download)
HandBrake Documentation (A great bookmark!) - [here](http://trac.handbrake.fr/wiki/CLIGuide)

---

### Post by TroyDowling on 2008-07-28
One last note/workaround. I've found that sometimes DVDs fail to backup with dvdbackup straight from the disk. By first copying the disk to an image file, it seems that dvdbackup is able to complete. When the disk is inserted and mounted, you can right click on the icon on the desktop and choose "Copy Disk" then choose to a File Image. Or utilize Linux's low-level copy command dd.

```

dd if=/dev/scd0 of=~/Desktop/myMovie.iso

dd if=[where the movie is] of=[where you want the image]

```

Most movies come on a dual layer DVD so expect the size of the image to be around 8GB and the time for the copy to be roughly 15 minutes. Also, just as one last minor note, I'm not sure if this affects anything because Handbrake is smart enough to make the decision itself, but when I run the dvdbackup tool, I now tell it to rip only the first title (which is usually the main feature). Of course this saves a little time in that step as well. Just add the "-t 1" flag or the built in "-F" flag (for feature) to the dvdbackup command and you should be good.

I hope this helps someone! I've seen so many half baked guides on this subject and the area of support is so weak it seems.

---

