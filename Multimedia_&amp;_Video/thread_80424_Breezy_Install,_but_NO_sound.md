---
title: "Breezy Install, but NO sound"
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by iNerdSure on 2005-10-22
I have been searching and trying different solutions for 2 weeks without success. Anyone out there has experience to share on breaking the (no) sound barrier.
Tried tweaking in alsa etc. Can't play music CDs and movie DVDs. Skype works but only in text chat. 

11:~$ lsmod | grep snd
snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
11:~$

May be compelled to switch to other distro, or worst of all the other O$.
:(

---

### Post by thomax on 2005-10-22
sudo kuser

double click on your username > groups > list everything but root

ok > ok and you have sound ;)

---

### Post by iNerdSure on 2005-10-22
[QUOTE=thomax]sudo kuser

double click on your username > groups > list everything but root

ok > ok and you have sound ;)[/QUOTE]

Sorry, I'm quite a Linux newbie. Don't quite understand your solution.

---

