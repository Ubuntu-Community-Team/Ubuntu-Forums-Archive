---
title: "Flash and pixie hollow"
date: 2008-12-18
forum: Multimedia Software
---

### Post by dardack on 2008-12-18
So my daughter likes to play disney's pixiehollow.com, a game based off the new tinkerbell movie.  Anyways, before i upgraded her laptop to Ubuntu 8.10 she played fine.  As of updating to 8.10, it no longer works, and comes back with an error message of:
Your fairy log-in information wasn't recognized-please try again.  

I tried it on my work computer with windows and it logs in fine.  I've tried my other ubuntu boxes (they were already 8.10 for awhile now) and same error occurs.  Does anyone know why this is happening?

---

### Post by tlbj6142 on 2009-01-11
I, too, am having the exact same problem.  Anyone figure this out yet?

---

### Post by Hizoomi on 2009-01-14
OMG same here :-)

Except that I'm using Ubuntu 8.04.1.

I also sent a link to this thread to the support folks along with my note, so hopefully it will be resolved soon.  Works fine on Mac with Firefox, and (gak) Windows with IE7, of course.

---

### Post by dardack on 2009-01-21
Anyone figure this out?  I've tried everything my little knowlege could think of.

---

### Post by dr.jose on 2009-01-22
I found a solution that worked for me, hopefully it works for you too.
I had one system on which it worked and one on which it didn't, so I went looking for the difference.  I checked about: plugins in firefox on the two systems and saw a difference.  On the system that didn't work, (An Eee PC with ubuntu-eee 8.04.1) flashplugin-nonfreebeta was installed.  I installed flashplugin-nonfree instead, and the problem went away.

---

### Post by dardack on 2009-01-23
I"ll check that but think the nonfree is installed and not the beta.  Although, she didn't have problems on 8.04 only 8.1, hope jaunty fixes it or maybe i'll regress her machine.

---

### Post by grumpy_old_troll on 2009-01-31
This happened to me, also.

She was running an unpatched eee pc she got for Christmas with I think firefox 2.0.0.14, and I don't know what flash build.  It was freezing on her, so I upgraded to firefox 3.0.4 (by using synaptic/mark all and clicking all the oks).

After that, she said it gave this message for all her fairies, and showed me the top one.  I tried the bottom one and it worked fine.  She played for a while, but now we get the same message with all the fairies.  We tried logging out and back in, but it's still failing.

She's sad now :(  We'll keep trying.  Any further information would be much appreciated.

---

### Post by sciman67 on 2009-05-22
I can confirm the problem. I tried installing the flashplugin-nonfree, but that did not resolve the problem.

---

