---
title: "sound so quiet"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by rase on 2007-05-14
hi, 
my problem is: sound in my ubuntu 7.04 is so quiet. it is playing music, all sounds, but everything is so quiet. i can not turn master up in alsamixer. i have toshiba satellite A105-S4084. in earlier ubuntu were everything good and playing properly.
please help me. what should i do???

---

### Post by encompass on 2007-05-15
Could you tell us what sound card you have?

---

### Post by rase on 2007-05-15
hi,

i have Intel sound card:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by encompass on 2007-05-15
I am trying to think... 
If I am not mistaken, this is a know bug.
Make sure that you have your sound totally up.  I mean... turn everything on and see what happens.
I will google in the mean time and see if I find the bug with your card.

---

### Post by rase on 2007-05-16
i have everything totally up. it will not help, if i reinstall ubuntu. hmm?

---

### Post by encompass on 2007-05-16
So the sound worked before? in this same version of ubuntu?

---

### Post by rase on 2007-05-16
no, sound works in ubuntu 6.06. when i installed 7.04 it is not working properly, sound is quiet.

---

### Post by encompass on 2007-05-16
This is a regression...
The current work around is found here...
[http://baheyeldin.com/technology/linux/ubuntu-edgy-6-10-to-feisty-7-04-upgrade-sound-and-video-issues.html](http://baheyeldin.com/technology/linux/ubuntu-edgy-6-10-to-feisty-7-04-upgrade-sound-and-video-issues.html)
To make it clear...
open this file as root (with sudo)
/etc/modprobe.d/alsa-base
and add this line to the very bottom
options snd-hda-intel model=3stack
reboot and enjoy.... at least we hope...

---

### Post by rase on 2007-05-16
Thank You Very Much!
It Is Working Properly.
Thanks Once More.

---

### Post by encompass on 2007-05-16
Your welcom... Looks like the bug is because the changed the chip slightly, and it affected yours.  They should have it fixed permenently in the next version.  Gutsy.  Let hope.

---

### Post by hondaman on 2007-05-16
I have exactly the same sound on my toshiba, a p105-9337, and the 3stack option in alsa-base did not help me unfortunately.

Any other ideas?

---

### Post by encompass on 2007-05-17
and your sure that it is the same chipset? AKA the exact same card?

---

