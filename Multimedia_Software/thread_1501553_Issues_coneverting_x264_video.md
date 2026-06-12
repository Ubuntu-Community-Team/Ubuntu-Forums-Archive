---
title: "Issues coneverting x264 video"
date: 2010-06-04
forum: Multimedia Software
---

### Post by jerome1232 on 2010-06-04
I make backups of all my dvd using handbrake + DeVeDe

This is the first time I've attempted a rip + burn using karmic since I've installed it.

Handbrake rips the video to h.264 encoded m4v videos. DeVeDe will convert them to a burnable iso ready to be played in any dvd player.

DeVeDe uses mencoder as a backend and lately I've had it make 4.5mb files from 1 GB rips, the resulting files from devede don't have any video in them.
I think this is a mencoder problem. But I'm not sure how to go about figuring it out.

I popped open a terminal and ran an encode using devede to see what the output is and it seems like it's just skipping frames. here is a sample of the encode, it's a small 60 second preview.

```
Launching program:  mencoder -noautosub -oac lavc -aid 1 -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -endpos 60.0 -ofps 30000/1001 -vf expand=720:480:0:62,harddup -lavcopts threads=2:vcodec=mpeg2video:trell:mbd=2:sc_threshold=1000000000:cgop:vstrict=0:vrc_maxrate=8500:vrc_buf_size=1835:vbitrate=5001:keyint=12:acodec=ac3:abitrate=224:aspect=16/9 -o /var/tmp/previewfile_01_01.mpg /home/jeremy/Videos/Testmovie.m4v
elemento:  /usr/bin
FAAD: compressed input bitrate missing, assuming 128kbit/s!
Limiting audio preload to 0.4s.
Increasing audio density to 4.

Skipping frame!

Skipping frame!

Skipping frame!

... goes on for hundreds of lines

Skipping frame!

Skipping frame!

SMPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
```

---

### Post by jerome1232 on 2010-06-06
*bump*

I have noticed it only seems to happen with videos I recently ripped using handbrake, however I haven't changed anything in handbrake...

Any way to figure out why mencoder is deciding it wants to skip the frames?

---

### Post by xzero1 on 2010-06-06
Never tried it [mencoder] lately, but I know mplayer has the -v parameter.

---

### Post by JohnAStebbins on 2010-06-07
> **jerome1232 said:**
> *bump*

I have noticed it only seems to happen with videos I recently ripped using handbrake, however I haven't changed anything in handbrake...

Any way to figure out why mencoder is deciding it wants to skip the frames?

I could have something to do with x264's new variable frame rate capability that handbrake now makes use of.  You might try changing your output frame rate from "Same as source" to a specific rate (assuming you are currently using "Same as source").  This will disable variable frame rate output if you are using an up to date nightly of handbrake.

---

### Post by jerome1232 on 2010-06-07
Wow, it seems you sir are quite correct, just did a test rip and that seems to have done it!

Thanks a ton.

---

