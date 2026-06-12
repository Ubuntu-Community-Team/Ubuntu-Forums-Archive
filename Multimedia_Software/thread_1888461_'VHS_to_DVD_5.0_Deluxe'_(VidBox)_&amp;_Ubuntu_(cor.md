---
title: "'VHS to DVD 5.0 Deluxe' (VidBox) &amp; Ubuntu (correct version)"
date: 2011-11-29
forum: Multimedia Software
---

### Post by tnob on 2011-11-29
Greetings all,

A subject frequently recurring on these pages is the small matter of how to transfer VHS tapes to DVD or some or other digital format.

In my case, the general idea is to store VHS tapes, in digital form, on external hard disk. Yet everything previously tried – still in Windows – failed consistently: emailing and word processing the only activities my then system deemed “legal” – which, ultimately, drove me raving mad. At about this point, a friend introduced me to Linux Ubuntu – and the rest is history. 

Or maybe not quite.

Avoiding Windows as best I can, ever since, has proven greatly beneficial to my mental health. In some instances, however,  there is no other option: my very select range of Windows applications still in use, with some regularity – music notation software, mostly –  will either not work in Ubuntu, or find no viable alternative there. Converting VHS, especially, sits most firmly in the former category, in my view,: in Linux,  the effort every bit as cumbersome as whatever else in Windows.

Or even more, perhaps: just visit YouTube, for an avalanche of clips on the very matter: solutions offered spirited all, without a doubt  – some helpful, some less so; but also –  almost without exception – pretty complex. Mindbogglingly so, at times (for a newbie like me in particular). No suggestions whatsoever availabe, though, as to the simplest way from A (capturing VHS tapes) to B (storing VHS tapes in digital form); as far as Linux is concerned, it just doesn't seem to come into the equation. 

The video capturing/editing hardware purchased several weeks ago, however (Honestech's 'VHS to DVD 5.0 Deluxe' – also known as VidBox, for short) – an external interface, essentially – does exactly that. It's affordable; and (dare I say it?) promising – in Windows, anyway. Please don't get me wrong here, though: this is not in any way a plea for returning to Microsoft output. I just desperately want my VidBox to function in Ubuntu; and, moreover, in an uncomplicated, straightforward fashion! 

Browsing Ubuntu forums, one night, I happened to come across an old thread (from 2009), by happy coincidence, in which, interestingly, the very same hardware was discussed (on [http://ubuntuforums.org/showthread.php?t=1332734](http://ubuntuforums.org/showthread.php?t=1332734)). Back then, the general complaint was that the hardware aforementioned didn't do a thing in Ubuntu – the same problem I initially ancountered. But lo and behold: two years on, to wit, VidBox does indeed show, suddenly and intriguingly,  on my PC (in Places --> Computer, to be precise). 

Suddenly, my hopes are up. And I also wonder if this means Vidbox can actually be installed on Ubuntu. But is  this assumption correct?

[At this point, I attempted to insert 2 screenshots of the Vidbox Window upon opening. But, sadly, in vain...]

At this moment, VidBox is only operational in XP. But if you – the wider Ubuntu community out there – happen to know of some clever way of making VidBox actually work on Ubuntu – if this is indeed a viable option – I'd definitely like to hear from you. Pointers to similar, commercially available iexternal interfaces – albeit with Linux support – will be equally welcome, of course. I don't hold my breath, though, in this latter regard: I have been trying on internet, over and over again, but in vain.

I'm also looking forward to a word from the people originally raising this issue, back in 2009. How did you fare since, with respect to VHS convergence In general – and VidBox in particular?  

I'll end with some additional info. 

I own two desktops: the main one, for every-day use, dual-booth (Linux Ubuntu/XP); the other has just XP, for essential music notation software Ubuntu  doesn't support - but it also holds the  software for processing those VHS tapes aforementioned. And my current Ubuntu version,finally, is 10.04).

tnob

---

### Post by gareththered on 2011-12-21
Try:-

[http://linuxtv.org/wiki/index.php/Honestech_Vidbox_NW03](http://linuxtv.org/wiki/index.php/Honestech_Vidbox_NW03)

Works, but you will need to download the source code, patch and compile it!

---

### Post by mocha on 2011-12-22
Is the device you are talking about video 4 linux compatible, meaning does it create a /dev/videoX device when it's plugged in?  If so, it's very easy to capture, just use the v4l2 tools to setup the parameters and then cat /dev/videoX > output.xxx.  I have more info on my gopher site on how to setup and make a script, time limit, cron job, etc.

---

