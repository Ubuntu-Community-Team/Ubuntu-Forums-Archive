---
title: "Sox, lame and mp3 support"
date: 2011-01-16
forum: Multimedia Software
---

### Post by danpaluska on 2011-01-16
prompt$sox mix2.wav soundstrack.mp3
sox FAIL formats: can't open output file `soundstrack.mp3': SoX was compiled without MP3 encoding support


so i have seen a lot of other posts about this issue but none had an answer for me. i've run sox on numerous other mac and linux machines and never had a problem with .mp3 stuff provided i have lame and libmad installed.

but on my current machine (ubunut 10.10) i can't seem to get sox to do anything with .mp3 despite having lame installed, reinstalling sox, etc. 

any tips?

thjanks,
dan

---

### Post by andrew.46 on 2011-01-16
Support for encoding with lame has been deliberately removed by the sox packagers. Perhaps this old post might help out, I have not tested it under more recent Ubuntu versions though (I see a version bump to 14.3.1 for starters):

[http://ubuntuforums.org/showpost.php?p=9859875&postcount=8](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8)

Andrew

---

### Post by danpaluska on 2011-01-17
that worked great! thanks!:popcorn:

---

### Post by andrew.46 on 2011-01-17
Great news, I am glad that mini guide still has some use :)

Andrew

---

### Post by rkircher on 2013-02-19
> **andrew.46 said:**
> Support for encoding with lame has been deliberately removed by the sox packagers. Perhaps this old post might help out, I have not tested it under more recent Ubuntu versions though (I see a version bump to 14.3.1 for starters):

[http://ubuntuforums.org/showpost.php?p=9859875&postcount=8](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8)

Andrew
I followed your mini guide at [http://ubuntuforums.org/showpost.php?p=9859875&postcount=8](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8) to get sox mp3 encoding working on Debian AMD64 Squeeze, and it worked without a hitch - thanks for that fine post.

Thereafter Debian update notifications were received for sox-14.3.1 that were identified as "strict".  If I install these updates will the "strict" Debian licensing agreement cause me to loose the sox mp3 output encoding?

While I was running Ubuntu 11.04 the same vintage sox worked with mp3 output.  It was the switch to Debian Squeeze that lost the mp3 capability with sox, so I am afraid it's Debian's "strict" policy that effects whether or not mp3 works.  Any comments would be appreciated.

---

### Post by andrew.46 on 2013-02-19
Times have changed since these old posts :). For Ubuntu I believe that the sox package now links _dynamically_ against libmp3lame which is to say that if you install libmp3lame sox will use it for mp3 conversion. This could be true of the Debian package as well but I cannot test this I am afraid...

---

### Post by wildmanne39 on 2013-02-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

