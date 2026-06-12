---
title: "[SOLVED] *still* can't get (open source) Radeon driver to give direct rendering with"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by jai_mantravadi on 2007-10-18
Note: I realize this is misposted, I meant to put it in Multimedia and graphics. Can one of the moderators please place this there?

Ok... I'm making a new thread because I'm *frustrated* and nobody's replied to my other thread here;

[Re: can't get direct rendering on radeon 9800 (open source driver)]("http://ubuntuforums.org/showthread.php?t=560066")

Short story, neither open nor closed-source drivers will work for 3-D acceleration. I'm running Ubuntu Gutsy (just upgraded with the Release candidate CD, but that's for another thread), and I still can't get it to work. Please see previous thread for more details, but in the mean time can someone decode the cryptic response from glxinfo:
```

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

I've tried setenv (in bash... doesn't work), export and set, and then re-executing glxinfo, and there is no difference in the output! 

Please help, because I *really* *really* would like to be using compiz with gutsy, I was hoping that upgrading would solve the problem, but no dice.

I *have* SWITCHED to Ubuntu, but things like this and lack of support (i.e. dead threads - maybe I'm supposed to make a new thread if my previous one goes dead?), are what keeps me from being able to recommend it to my friends (and help them through the wibbles to get it set up). Thanks for any help!
Jai

---

### Post by Ferrat on 2007-10-19
Hmm how did you install the ati closed drivers? they should work 

did you activate them in restricted drivers section?

---

### Post by jai_mantravadi on 2007-10-19
I followed all the instructions found in:
[Radeon Closed-source driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
After that didn't work I tried the open-source driver. Then I attempted to use [Envy]("http://albertomilone.com/wordpress/?cat=12") When that didn't work, then... I reposted above (after a number of weeks). I've just upgraded to Gutsy and have yet to re-try everything, but if I can figure out why there was a problem with Feisty, then I want to take care of those problems when using Gutsy.
Any ideas? 
Thanks!

---

### Post by jai_mantravadi on 2007-11-23
OK... now that I've tried a fresh install off the gutsy DVD (took a couple of coasters to figure out my CD media was a bad batch), Direct rendering was working with the open-source driver out-of-the box. Compi Fusion took about 2 minutes to install, and even less time to get working. Haven't tried fglrx yet, but I'm not sure that's worth it since I'm upgrading the hardware in a few days :). Thanks to everyone who tried to help me get the [open and closed source] drivers working. Sorry for the frustration. I never did figure out why direct rendering wasn't working, (or how installing a new mouse driver can screw up a graphics card even after reversing the instructions completely).
Jai

---

