---
title: "trying to make my cs46xx sound card work with skype"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by sal on 2005-11-08
can anyone give me an idea as to getting a cs46xx sound card to work with skype?

here is the output of lspci:
0000:01:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

now here is what i have in my asound.conf:
pcm.cs46xx {
   type hw
   card 0
}

ctl.cs46xx {
   type hw
   card 0
}

now everything seems to work except skype. the funny thing is i can record in audacity with no problems but cant get skype to work at all.

im runing kubuntu-desktop with kde 3.5b1.
tia.

here is how i configured the card:
./configure --with-cards=cs46xx --with-sequencer=yes;make;make install

as per:
[http://www.alsa-project.org](http://www.alsa-project.org)

---

### Post by sal on 2005-11-08
bump

anyone?

---

