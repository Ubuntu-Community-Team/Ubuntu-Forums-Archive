---
title: "No Sound in 7.04., Toshiba Laptop, Tried every other fix from every thread."
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by acabrera on 2007-05-05
I'm about to set this computer on fire.

I've installed Ubuntu 7.04 on my Toshiba Laptop and have tried everything to get it working

I tried the /etc/modprobe.d/alsa-base options snd-hda-intel model=auto thing

I've tried it with model=toshiba, model=3stack, model=6stack-digiout, model=fujitsu, model=ihateyou... nothing works

I've tried the soundstartfix hack. Nothing.

I'm starting to think it's a permissions problem, I've read elsewhere that the user has to be part of the audio group, but when I go to System -> Administration -> Users and Groups -> Manage Groups, I don't see any mention of an audio group. Am I doing something wrong? Should I just try doing a fresh install of Ubuntu? Please help.

---

### Post by meng on 2007-05-05
I feel your frustration. Have you tried other versions of ubuntu on this laptop, e.g. 6.10, 6.06?

---

### Post by John Azelvandre on 2007-05-05
My Feisty 7.04 just died.  It was working (system sounds, at least) when I first installed it, yesterday.  But now -- nothing.  And sound apps, such as Rhythmbox crash and exit if I try to play somethin g.

The only thing I changed were video card settings ... (?)

---

### Post by meng on 2007-05-05
My own experience:
Something about my laptop (a 4-year old Dell) doesn't like kernel 2.6.20+ and will refuse to complete the bootup sequence. It's a good thing Edgy is doing the job already.

---

### Post by John Azelvandre on 2007-05-05
I found something that worked for me:

Re-installing libxine-extracodec.  (Actually it wasn't installed, so I installed.)  Now everything works.

I hope it stays that way! :guitar:

---

### Post by andreigbs on 2007-05-05
where do you get that codec from exactly and how do you install it?  another toshiba laptop is in dire need of this fix.  not to mention i closed the lid to put it to sleep and it didn't want to come out of standby, nor could i force it to shut down and restart.   for a few minutes i thought i'd be having to buy a new HD or new laptop.  if someone has some step-by-step fix for getting this codec installed, we'd appreciate it.

---

### Post by John Azelvandre on 2007-05-05
Installing (or reinstalling) the libxine-extracodec package is simple:  Under System/administration, open the synaptic package manager.  Search for 'libxine-extracodec' and once you find it, check for installation/reinstallation, and 'apply marked changes.'  Synaptic does the rest.  Hopefully that will help your situation.

As far as the sleep problem, I don't know much about that.  Perhaps you should turn off the sleep option until you're able to find a more permanent fix.  Look under System/Power management and look at the options.  Choose something more benign for what happens when you close the lid, like "do nothing" or "blank screen."

Good luck!

---

### Post by rockingmtranch on 2007-05-05
This one finally worked for me:
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

