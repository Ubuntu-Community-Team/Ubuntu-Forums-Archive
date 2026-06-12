---
title: "Cinelerra clip gain way too high"
date: 2011-01-02
forum: Multimedia Software
---

### Post by neanderslob on 2011-01-02
Hey all,

I've had great luck with Cinelerra in the past and really haven't found any vidoe editing software that compares but, in 10.04, I've found that any clip I put into my storyboard has the track's gain jacked up ridiculously.  It's not a matter of Cinelerra's volume as far as I can tell, it's that it sees the clip's volume as being super high and exclusively on the left channel.  Any one know how to fix this?

Thanks in advance

---

### Post by neanderslob on 2011-01-17
Bump?

---

### Post by BicyclerBoy on 2011-01-17
There isn't some weird monaural audio setting is there ?
(not used Cinelerra)

High level on one channel could occur if L & R were added together into one channel without compensation.

Does it not like your audio files ?

HE-AAC v1 & v2 has a mono fall-back mode in AAC LC decoder..

Maybe you need a later/unstripped ffmpeg or libfaad libfaac livavcodec

---

### Post by neanderslob on 2011-01-17
Thanks for the ideas, I'll look into them.  I really don't think it's my audio files.  I used exactly the same ones as I did in an earlier project back when it was still behaving well and I still had the same problem.  With regard to the codecs, they're up to date as far as 10.04 is concerned but maybe this version of Cinelerra expects more?  Possibly?  I'll play around with it.  Thanks for giving it your best shot!  :guitar:

---

