---
title: "need some mencoder help"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by Coogan on 2007-07-01
I've been using mencoder to convert dvd's into either divx or xvid format.  But I'm less than thrilled with the results.  I cannot seem to get rid of these jagged lines that keep popping up.  For an example, have a look at the attached picture.

The way I encode them is to use a little container script I wrote that uses options and settings that I pretty much cobbled together from multiple sources.

I realize this is not really the place for mencoder questions.  However the man pages for mplayer and mencoder are incredibly technical; I know the basics like framerates, interleaving, etc, but when they start talking about telecines and B-frames, well that stuff is just waaay over my head.

If anybody can help me with this, I'd really appreciate it.  I'm completely stumped as to how to fix it.

An example of the problem:
[IMG]http://i80.photobucket.com/albums/j191/LSUChris/Clipboard01.jpg[/IMG]

And the settings I use.  I generally use a video bitrate of around 1000.
```
mencoder $CHAPNUM -dvd-device $VIDPATH -oac mp3lame -lameopts abr:br=128 -ovc xvid -xvidencopts min_iquant=1:min_pquant=1:bitrate=$BITRATE:pass=$PASSNUM -vf pp=de -ofps 24000/1001 -o $OUTFILE >> .mencodedvd_status
```
(the variables are supplied as arguments to the script, except for $PASSNUM which is tracked by the script itself)

Coog

---

