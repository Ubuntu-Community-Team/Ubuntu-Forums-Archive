---
title: "Lossless DVD Backup (onto Hard Drive)"
date: 2008-08-19
forum: Multimedia Software
---

### Post by otheracco on 2008-08-19
OK, I did a search for 'lossless dvd' and didn't get any good results, but if anyone sees an answer to this question please post it.

What I need to do is pretty simple, however I have questions about getting it truly lossless.
I need to backup a few work related DVD's to my hard disc, but I want them to be 100% lossless.

I've been able to get great results by making them into .iso, but I want to know if uncompressed vob files are truly lossless.

It would be best for me to have vob files.

P.S. I need them lossless because they will be projected in a conference room, a lossy format would should imperfections on a 150" screen.

---

### Post by molochi on 2008-08-19
As long as you aren't **re-encoding** the video you shouldn't encounter loss of data. Copying the directories from the DVD to a harddrive is bit for bit whether you create an iso or just copy/paste the directory structure.

---

### Post by otheracco on 2008-10-15
I've been adding more and am running out of space.

I've also been reading about converting the source DVD's to a lossless format and am in way over my head. I've heard good things about logarith and I've seen great compression results with MLC.  

Are these truly lossless codecs?  I find it hard to believe that you can take a 7GB movie and encode it with MLC into half (or less) the size without losing quality.

---

### Post by chaumurky on 2008-10-15
The video on your DVD's are already compressed with a lossy encoder - MPEG2. The term 'lossless' usually refers to encoding from an uncompressed source. In your case using one of these encoders will result in a much larger file but absolutely no gain in quality. Also, every time you re-encode you will suffer a quality reduction. I would suggest you aquire an external harddrive and leave the files as they are.

---

### Post by otheracco on 2008-10-15
I know DVD's are already lossy with mpeg2 compression.

Is there anything I can use to transcode my VOB's to shrink them?
I don't care about losing quality per say, but I do care about perceptively losing quality.  To simplify, quality loss isn't a big deal as long as it's not noticable.

I've read that multi-pass compression uses certain algorithms that compress based on parts of the screen that don't change... There are other things I've read too that I don't remember at the moment.

I know programs like DVDFab shrink your DVD's to your chosen quality settings... How do they do it?  What is a good cut-off, in percentage, for quality?  In other words, how much can you knock the quality down without noticing it?

---

### Post by chaumurky on 2008-10-15
That can be subjective really. How you 'spend' your required bitrate (and ultimately filesize) comes down to preference: I'd prefer a lower resolution and lower detail to blocking and ringing. Others de-interlace to single frame and get a saving there. As far as encoders go look for ones with motion compensation and other goodies to wring as much quality as you can. Multipass helps too. I've had a lot of success with xvid but I hear H264 is v.good too. For proggies, have a play around with 'AVIDemux' (in the repositories). I use 'k9copy' (it uses 'mencoder' coupled with some good presets).

---

