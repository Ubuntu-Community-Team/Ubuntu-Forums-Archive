---
title: "[HELP] Sound comes through the headphone."
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by fairlady350z on 2007-05-22
Hi all,

First of all I'm new here and to the linux world as well. I'm one of those people who is quite dissapointed with Windows and decided to give Linux a try.

So, I have this sound problem since last weekend, it's been a few days. I've been digging up a lot of articles including those with a similar issue. But none of them solves it yet.

I finally able to get the sound working although only through headphones. If I unplug the headphones, there is no sound at all.

Here's my spec:
Dell m2010
Soundcard: hda-intel
Chip: Sigmatel STAC9221 A1

I tried firing up alsamixer, make sure none of them is muted. I tried almost everything but none of them seems to work out. One other thing, I don't see the headphone option under the preference, so I don't know how to disable that.

I also did get the latest alsa driver as well.

This linux thing is way beyond me, so I'd be so appreciated if someone can help me out with this problem.

Thank you in advanced

---

### Post by teaker1s on 2007-05-22
while I dont know the exact answer, I can tell you that the hda-intel sound does sometimes require configuring to laptop model to work correctly.
look
[http://ubuntuforums.org/showthread.php?t=239995&page=2]("http://ubuntuforums.org/showthread.php?t=239995&page=2")
look at post by	
**pseudonym**

---

### Post by fairlady350z on 2007-05-22
Hi 

Thanks for a quick respond.

I did come across this post and give it a try, but I still have the same issue.
I just noticed this morning, however, that if I plug-in my external 5.1 speaker into this special audio connector (using an adapter that supports s/pdif), it works. But not the notebook speaker though.
However they are the same my notebook has 5.1 speaker thing, so I use 5stack instead.

I did try some other stuff like 6stack, 6stack-dig, auto, dell, ref, laptop, etc but to no avail.

Oh one more thing though, when I was compiling the alsa-driver, i got an error when installing alsa-utils. Do I need to start over and try compiling again?

thanks

---

### Post by fairlady350z on 2007-05-22
The problem still persists.
Should I just give up and get a new box with compatible hardware?

It's trully disapointing how this piece of machine I bought so exepnsive from Dell, can't even handle linux properly.

Thanks alot

---

### Post by teaker1s on 2007-05-24
I would pm pseudonym and see if he/she has any suggestions.
Secondly I've have a HDA Intel based Nvidia sound on my laptop, my advice is try reinstalling alsa- then if that doesn't work, maybe contact the alsa project for some guidance.

I understand your fustration-my sound has been broken with updates on my debian system several times (ubuntu is  based on debian)

---

### Post by E2002 on 2007-12-18
Hi Fairlady,
I got the same problem with exact the same spec:
Dell XPS M2010
Soundcard: hda-intel
Chip: Sigmatel STAC9221 A1

Did you solved the problem? 

Best regards

---

