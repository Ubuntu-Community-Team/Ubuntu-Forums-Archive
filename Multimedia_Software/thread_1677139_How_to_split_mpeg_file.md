---
title: "How to split mpeg file"
date: 2011-01-28
forum: Multimedia Software
---

### Post by YigalB on 2011-01-28
I need to split (and only split - so it's not really "editing") mpeg file to several mpeg files.
What's the easiest way to do that with Ubuntu?

---

### Post by howefield on 2011-01-28
The included Pitivi ?

Applications > Sound & Video > Pitivi Video Editor

---

### Post by sydbat on 2011-01-28
> **howefield said:**
> The included Pitivi ?

Applications > Sound & Video > Pitivi Video EditorUgg...

@OP - How about trying Kdenlive. Much more intuitive and useful than Pitivi.

---

### Post by vanadium on 2011-01-28
Not a good idea because that involves transcoding, which takes a lot of time and involves quality loss.

You probably could use mencoder or ffmpeg to extract parts of an mpeg stream to a new mpeg stream without transcoding. avidemux would allow to do this graphically, and will probably be your best bet.

I know there are also specialized mpeg tools that certainly can take care of that, but I am not familiar with these. Type "mpegsplit" in the terminal, and you will already get a hint: indeed mpgsplit from the mpgtx package probably does the job.

---

### Post by FakeOutdoorsman on 2011-01-28
> **YigalB said:**
> I need to split (and only split - so it's not really "editing") mpeg file to several mpeg files.
What's the easiest way to do that with Ubuntu?

FFmpeg can do this easily. See my example and explanation in [Simple utility to trim/crop a video file that actually works?](http://ubuntuforums.org/showpost.php?p=6806574&postcount=2)

---

### Post by shantiq on 2011-01-31
How to split or trim a video with ffmpeg explained

**[====>here]("http://www.youtube.com/watch?v=uVB7Y6m4GCQ")**

---

### Post by nanonils on 2011-05-19
I want to split surgical videos that range from 15 to 60 minutes into 14-minute chunks for youtube upload (doesn't count towards my Google account storage quota and is easy to manage and share; upload of 500 MB takes amazingly only 1 minute where I am).

I spent about 1 hour trying to get mpgtx to work but I continue to get "wrong format" and other cryptic errors (maybe because mpeg 2 is "experimental": [http://linux.die.net/man/1/mpgtx](http://linux.die.net/man/1/mpgtx)).

Moving on to ffmpeg how can I do this in a straightforward way without having to just chop of 14 minutes then 28 minutes, etc? To give you an idea of the task, I have around 460 GB with hundreds of mpg videos half of which exceed the 15 minute limit.

Mpgtx sounded like the ideal program as one apparently simply has to specify the number of chunks. I'm very familiar with all the nice desktop editing programs but I can't do this for hundreds of videos.

Many thanks!

---

### Post by nanonils on 2011-06-08
OK, thanks, this command does the trick very nicely and within seconds. I found that all the GUI programs (Avidemux, KDEnlive) require re-rendering of the fragments:

ffmpeg -i input.mpg -ss 00:00:10 -t 00:00:30 out1.mpg -ss 00:00:35 -t 00:00:30 out2.mpg

---

### Post by MartyBuntu on 2011-06-08
> **nanonils said:**
> I found that all the GUI programs (Avidemux, KDEnlive) require re-rendering of the fragments:

You can split/cut with AviDemux without re-encoding.

---

### Post by nanonils on 2011-06-14
Excellent! Thank you for that tip. I didn't realize one can simply select the segment and "save"! KDEnlive requires rendering (unless I overlook that here as well). I was close to loosing it. 

The command line tool somehow only creates a first file for me and screws up the second part. Tinkered with it for hours and couldn't fix it. 

I just found that our surgical recorder has the hidden ability to automatically create new files at a preset time without noticeable lag between segments. This is one nice way of getting around YouTube upload limits that are currently at 15 minutes. They can then be shown seamlessly as a "playlist" and the cloud storage is free, upload for 1 GB takes amazingly less than 1 minute where I am. We're currently producing about 10 videos or 8 GB each week. I'm glad I won't have to manually fix them anymore in the future.

---

