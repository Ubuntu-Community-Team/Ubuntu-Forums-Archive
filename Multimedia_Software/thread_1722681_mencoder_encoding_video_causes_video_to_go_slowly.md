---
title: "mencoder encoding video causes video to go slowly"
date: 2011-04-06
forum: Multimedia Software
---

### Post by kthardin on 2011-04-06
Basically since my attempts at trying to get avisynth to work in linux with avidemux are a failure of spectacular proportions I've attempted to continue on with my transcoding project with mencoder.

This leads to the output video actually going extremely slow.  As if it were in slow motion.  Obviously this puts the audio out of sync, and the audio in fact ends well before the video actually manages to get about 80% of the way through.

My command line looks like this:

mencoder 00000.MTS -o test.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2000 -vf scale=848:480 -fps 60000/1001

Which appears to be the standard command line for this sort of encoding.  I'm new at this utility and completely at a loss to even begin to know if I've even seen relevant information in regards to this problem let alone any other tweaks that may be required.  I am also getting some strange messages during output:

2 duplicate frame(s)!
Pos:  39.4s   1324f (34%) 59.84fps Trem:   0min  12mb  A-V:0.010 [499:383]
Too many video packets in the buffer: (538 in 33569013 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

The duplicate frames pop up as either 1 or 2 duplicate frames.  What's that mean?  This only starts popping up about 30% of the way in, though it does not seem to affect encoding any more than is already being done.  The -ni options doesn't seem to do anything when used.

Any ideas?

---

