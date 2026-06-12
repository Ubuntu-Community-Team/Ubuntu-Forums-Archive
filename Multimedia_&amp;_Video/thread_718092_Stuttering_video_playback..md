---
title: "Stuttering video playback."
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by click170 on 2008-03-07
I'm experiencing stutter when playing video in VLC.  I've got a fast system so speed and memory are not the problem.  It happens with more then just one file.

I've tried changing the video output modules but that didn't seem to work.

I tried DMA but I'm using SATA drives.

I've tried copying the file off of the RAID-0 array that it was playing from but that had little affect, it only reduced the messages in VLCs log slightly.

Below I've attatched a bit from the log file.  Does anybody have any advice on how to un-gibble this?


main warning: computed PTS is out of range (7395), clearing out
main warning: timing screwed, stopping resampling
main warning: PTS is out of range (-3761), dropping buffer
main warning: output PTS is out of range (18265), clearing out
main warning: input PTS is out of range (7662), trashing
main warning: buffer is 54001 in advance, triggering downsampling
main warning: output PTS is out of range (9442), clearing out
main warning: input PTS is out of range (30846), trashing
alsa debug: recovered from buffer underrun
main warning: resampling stopped after 10401006 usec (drift: 15816)
main warning: PTS is out of range (-35644), dropping buffer
main warning: output PTS is out of range (6989), clearing out
main warning: input PTS is out of range (22910), trashing
main warning: buffer is 58537 in advance, triggering downsampling
alsa debug: recovered from buffer underrun
alsa debug: recovered from buffer underrun
main warning: resampling stopped after 7436708 usec (drift: 39500)
main warning: buffer is 47356 in advance, triggering downsampling
main warning: resampling stopped after 1408924 usec (drift: 31814)
main warning: buffer is 42647 in advance, triggering downsampling
main warning: resampling stopped after 1016112 usec (drift: 38376)
main warning: buffer is 44233 in advance, triggering downsampling
main warning: resampling stopped after 4611540 usec (drift: 31462)
main warning: PTS is out of range (-25323), dropping buffer
main warning: buffer is 63728 in advance, triggering downsampling
alsa debug: recovered from buffer underrun
main warning: computed PTS is out of range (29261), clearing out
main warning: timing screwed, stopping resampling
main warning: PTS is out of range (-36461), dropping buffer
main warning: output PTS is out of range (36836), clearing out
main warning: input PTS is out of range (29524), trashing
main warning: buffer is 94020 in advance, triggering downsampling
alsa debug: recovered from buffer underrun
alsa debug: recovered from buffer underrun
main warning: computed PTS is out of range (11386), clearing out
main warning: timing screwed, stopping resampling
main warning: output PTS is out of range (12934), clearing out
main warning: input PTS is out of range (11645), trashing
main warning: buffer is 92562 in advance, triggering downsampling
alsa debug: recovered from buffer underrun
main warning: resampling stopped after 12647439 usec (drift: 38620)
main warning: buffer is 40919 in advance, triggering downsampling
main warning: resampling stopped after 6979424 usec (drift: 22476)
alsa debug: recovered from buffer underrun
main warning: computed PTS is out of range (102552), clearing out
main warning: PTS is out of range (80131), dropping buffer
main warning: output PTS is out of range (119608), clearing out
main warning: PTS is out of range (48146), dropping buffer
main warning: PTS is out of range (24857), dropping buffer
main warning: PTS is out of range (6879), dropping buffer
main warning: PTS is out of range (-23359), dropping buffer
alsa debug: recovered from buffer underrun
main warning: PTS is out of range (-37750), dropping buffer
main warning: output PTS is out of range (5093), clearing out
main warning: input PTS is out of range (26429), trashing
main warning: buffer is 64167 in advance, triggering downsampling
alsa debug: recovered from buffer underrun
main warning: computed PTS is out of range (15433), clearing out
main warning: timing screwed, stopping resampling
main warning: output PTS is out of range (36910), clearing out
main warning: input PTS is out of range (15684), trashing
main warning: buffer is 64105 in advance, triggering downsampling
alsa debug: recovered from buffer underrun
main warning: computed PTS is out of range (187287), clearing out
main warning: timing screwed, stopping resampling
main warning: PTS is out of range (123046), dropping buffer
main warning: output PTS is out of range (208488), clearing out
main warning: PTS is out of range (91113), dropping buffer
main warning: PTS is out of range (62964), dropping buffer
main warning: PTS is out of range (32220), dropping buffer
main warning: PTS is out of range (-3616), dropping buffer
main warning: PTS is out of range (-35610), dropping buffer
main warning: PTS is out of range (-28929), dropping buffer
main warning: input PTS is out of range (227584), trashing
main warning: computed PTS is out of range (195426), clearing out
main debug: audio output is starving (77430), playing silence
alsa debug: recovered from buffer underrun
main warning: computed PTS is out of range (14998), clearing out
main warning: PTS is out of range (19176), dropping buffer
main warning: output PTS is out of range (15026), clearing out
main warning: PTS is out of range (-12809), dropping buffer
main debug: audio output is starving (25640), playing silence

---

### Post by uberlube on 2008-03-07
Do you have the restricted extras enabled. They are in the repositories if you dont.

---

### Post by click170 on 2008-03-07
Could you be a tad more specific?

I believe the answer is yes, as I've enabled all the repos that come in the default config.

---

### Post by Bubba64 on 2008-03-07
Check out this post.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by click170 on 2008-03-07
> **Bubba64 said:**
> Check out this post.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

No luck with any of the relevant instructions in that post.  Lots of packages installed though, so probably solved alot of problems I hadn't had a chance to run into yet.  Thanks!

That post suggested that I set the Video Output Module to Vx from X11 as I had last had it, and I noticed that the messages appeared a bit faster with Vx as opposed to X11, which had a bit of a delay before it started doing the same thing (occasional jitters and the messages in the log).

I've included the log from when I stop the video playback.  It provides a bit more info and for all I know could be relevant.

Any more ideas?



Log:
alsa debug: recovered from buffer underrun
main warning: resampling stopped after 302956 usec (drift: 20084)
main warning: buffer is 42917 in advance, triggering downsampling
main warning: resampling stopped after 246955 usec (drift: 19042)
main warning: buffer is 42875 in advance, triggering downsampling
main warning: resampling stopped after 407117 usec (drift: 21959)
main warning: buffer is 41792 in advance, triggering downsampling
main warning: resampling stopped after 223014 usec (drift: 12917)
main debug: control type=0
main debug: control: stopping input
main debug: closing input
avi debug: free chunk avih
avi debug: free chunk strh
avi debug: free chunk strf
avi debug: free chunk LIST
avi debug: free chunk strh
avi debug: free chunk strf
avi debug: free chunk LIST
avi warning: unknown chunk (not unloaded)
avi debug: free chunk LIST
avi debug: free chunk ISFT
avi debug: free chunk LIST
avi debug: free chunk JUNK
avi debug: free chunk LIST
avi debug: free chunk idx1
avi debug: free chunk RIFF
avi debug: free chunk JUNK
avi debug: free chunk LIST
main debug: removing module "avi"
main debug: removing module "access_file"
ffmpeg debug: ffmpeg codec (MPEG-4 Video) stopped
main debug: removing module "ffmpeg"
main debug: killing decoder fourcc `XVID', 0 PES in FIFO
main debug: removing module "a52"
main debug: killing decoder fourcc `a52 ', 0 PES in FIFO
main debug: removing module "a52tofloat32"
main debug: removing module "bandlimited_resampler"
main debug: thread 2992077712 joined (alsa.c:714)
main debug: removing module "alsa"
main debug: removing module "float32tos16"
main debug: removing module "float32_mixer"
main debug: thread 2943835024 joined (input/input.c:412)
main debug: garbage collector destroys 1 vout
main debug: removing module "xvideo"
main debug: thread 2952858512 joined (video_output/video_output.c:461)

---

### Post by Bubba64 on 2008-03-07
I have VLC installed but I never useit  except for the installed adds codecs I use totem mplayer or even better smplayer but I have never tried to play a dvd but just streaming or captured video or music or cds

---

### Post by ronsonk on 2008-06-07
I have stuttering video (and sound) in Totem.  I found that I have to set my Movie and Music sound option to Pulse. If I ALSA it stutters.

---

