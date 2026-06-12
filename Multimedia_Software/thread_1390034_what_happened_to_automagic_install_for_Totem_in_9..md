---
title: "what happened to automagic install for Totem in 9.10?"
date: 2010-01-25
forum: Multimedia Software
---

### Post by manfromthezoo on 2010-01-25
Alright, here's one for you, pop-pickers.

Many months ago I disposed of an infested XP build on a friend's machine and replaced it with 9.10 - winning a complete convert in the process, who won't be looking back :D

This weekend I'm due to do another in the same family (they like it too).

Now, I did a 'test-run' on a lappy, to make sure that the automatic codec download and install feature was still working in Totem - you know, the one that goes 'ah, I can't play this, but click and we'll be good to go' whenever it encounters a restricted format it can't decode.

So, I did my base install, grabbed 152MB of updates down, applied 'em all, and off I went. Re-booted, then did my usual trick of hitting up Apple's trailers section to trigger the option to install the codecs. Which normally works a charm.

Only now it doesn't. Totem pops up with the generic movie logo, and doesn't even bother trying to stream. Yes, I've been through installing the ubuntu-restricted-extras package via command line, been through the Medibuntu process etc. And yes, also found forum posts dating back to June last year detailing that Apple were fiddling with agent IDs and dropping any connections to Gstreamer. However, this must have got fixed as I was able to do this in November last year.

Anyone have the skinny on this situation?

---

### Post by manfromthezoo on 2010-01-25
Aaah - plot thickens.

Just tested Apple trailers from two previously known-good 9.10 machines.

Same problem. I think Apple are playing silly buggers.

---

### Post by ajgreeny on 2010-01-25
To get Apple trailers tp play you need to kid the trailer site into believing you are running a system other than linux, ie windows or applemac, which you can do with the User-Agent extension for firefox.

Make a new agent called Quicktime, or something (doesn't matter what you call it as long as you recognise it) and complete the boxes as shown in my attachment.  When you want to play a trailer use that agent and you should be OK again.

I can't help with your totem question, which I don't think is linked to the trailers problem, I'm afraid as I always add the codecs before I do anything else when I install ubuntu, so have never used the codecs search system that you speak of.

---

### Post by manfromthezoo on 2010-01-25
Thanks, Al.

At least I can now get Totem to pop-up again when hitting the links. I guess now I have to investigate why trailers aren't then automatically streaming.

Have to admit, from reading around a bit since then, I didn't realise Apple borked support for Linux users like this from time to time. :o

---

### Post by mc4man on 2010-01-25
Atm some of the urls aren't what they appear to be, ex 
```
http://movies.apple.com/movies/fox/avatar/avatar-tlrf_720p.mov
```
is really 
```
http://www.apple.com/movies/fox/avatar/avatar-tlrf_720p.mov 
```

Edit (now the above is working fine in firefox/chrome thru the totem plugin
It appears they've been changing the address's over the last day or so

---

### Post by manfromthezoo on 2010-01-25
Hhhm. That's interesting, but I'm still stuck here - now I'm not convinced it's a codec issue - I can view trailers from Trailer Freaks etc with no issue.

Confusingly though, at least one of you still seems to be able to stream video. Gah. This reminds me of the bad old days.

---

### Post by loose555 on 2010-08-15
I notice on my monitor that both Xorg and plasma are taking most of  my computer resources even when no activity takes place: On the average I  would say that palsma takes about 50% of CPU and Xorg about 10%. This  is on an Intel Core2 Duo CPU's computer. My screen resolution is  1920x1200.
 I upgraded from Kubuntu 8.10 (completely up-to-date) to Kubuntu 9.04  on the day of the official release, using the alternate disk image for  the upgrade. About half the upgrade was taken from the CD I burnt, the  last half straight from the repository. That happened following a  restart of the upgrade process.

---

