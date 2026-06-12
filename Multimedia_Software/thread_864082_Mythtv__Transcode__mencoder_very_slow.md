---
title: "Mythtv / Transcode / mencoder very slow"
date: 2008-07-19
forum: Multimedia Software
---

### Post by picbits on 2008-07-19
I've managed to get my server pretty much set up with Mythtv and my Nova T-500 DVB card. It all works perfectly apart from transcoding.

I'm using mencoder to transcode the recorded .mpg files to Xvid but I'm getting some very strange results.

Using a VBR of 4000 and quantisation of 4 I did some test.

I recorded a 7 minute show - the raw file came out at 242mb. I set this to transcode as a userjob with the above settings and it took around 5 minutes to transcode - around 30fps. Quality was fine and as expected.

I then recorded a 32 minute show - the raw file size was 1040mb. I set this to transcode with the same userjob and that was over an hour ago. Looking at the mythbackend.log the job appears to be at around 15%

It seems that small files run at a much faster FPS conversion rate than the larger jobs.

I've also noticed that the CPU overhead on the larger jobs is only 5-10% while the small jobs are at 70-80% which ties in with the time taken to transcode the jobs.

I'm running an AMD Sempron 2800+ with 1Gb ram so it should be able to manage more than 2-3fps on encoding a large file. On Ubuntu 8.04 Server with GDM GUI

Any ideas ?

---

### Post by picbits on 2008-07-19
Correction - the input file was only 553mb size on the one that takes its time.

I reran the 7 minute file through Mythtv with the same settings as the 30 minute file while the 30 minute file was still transcoding and it finished again in around 8 minutes. The 30 minute file is still transcoding 2 hours later.

---

### Post by picbits on 2008-07-19
Ok - another update. I think I've traced the problems to the cutlist in nuvexportrc

If I disable the cutlist, I get around 25-30fps on the transcoding. If the cutlist is enabled I drop to around 2fps.

Just testing stuff now on a large recording - I seem to be having audio problems now ......

---

### Post by xc3RnbFO8P on 2008-07-19
Does video sync with audio?

---

### Post by picbits on 2008-07-19
I've had some interesting results.

A couple of recordings have had the audio playback going really slow - around 1/4 of its normal speed.

Another recording has had the strangest problem - its almost like a narration for visually impared people with a bit of audio coming on every now and again describing (very briefly in a couple of words) what the scene is.

Just finishing off a transcoding now after rebooting to see what happens.

---

### Post by picbits on 2008-07-19
Ok - even stranger

I transcoded the file I recorded this morning - it went at a good speed but there was no audio - or so I thought.

I left it playing in the background and suddenly I started getting some kind of sound.

Adverts had no sound but when the program started there was the title music. When the actual program started, there was background sound i.e. peoples footsteps, doors opening and closing etc but no voices.  Cut to adverts - no sound at all - back to program and there is sound again.

Its almost as if there was an extra audio stream that the transcoder has picked up and ignored one of the required audio streams.

Will carry on playing and see what happens

---

