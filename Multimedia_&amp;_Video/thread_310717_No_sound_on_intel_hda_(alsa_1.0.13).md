---
title: "No sound on intel hda (alsa 1.0.13)"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by clauck on 2006-12-01
Hi everyone!

My name is claudio and i'm a Ubuntu newbie, even if i have some experience on Debian.
I recently installed ubuntu 6.10 on my notebook asus f3jc mb with audio Intel 82801G (ICH7 Family) (rev 02) (intel high definition audio): the audio seems work, but no sound from speakers. Following old threads on this, i installed alsa 1.0.13, but none...could someone help me?

sorry for bad english!


claudio

---

### Post by Underscore on 2006-12-01
Hey. I am also having the same problem. Anyone can help? I got a toshiba P100-195 Portuguese /though I think the p100series exists all over the world/

I also have no sound in speakers. My logitech wireless headphones work though :S

---

### Post by greenie9 on 2006-12-02
ive got the same problem, i have an ASUS F3J laptop... im using 6.10

its infuriating...

](*,) 

i have heard that u need to install some an alsa, but i neither know where to find this, or how to install it

if someone knows how to fix it, and is willing to give an easy step by step guide for all of us ubuntu newbie, it would be greatly appreciated!!! :D

(nb i cant get sound through headphones...)

---

### Post by clauck on 2006-12-02
Hi guys, happy news for us!

i found this bug report that solved my problem

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2480](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2480)

at this moment i only added

*options snd-hda-intel model=uniwill-m31*

to my /etc/modprobe.d/alsa-base. This only fixes speaker features, but can't make headfones work (hope that reading all bug report will fix this).

Stay tuned and post your results,


clauck

---

### Post by DougieFresh4U on 2006-12-02
Well I have The Intel problem also!! Headphone & PCM sliders work** but** no speakers or Master switch  working. I also tried that fix last nite and nada :mad:

---

### Post by Underscore on 2006-12-02
hmmm. adding that line still didn't work for me. Debian and gentoo also have the same problem...

---

### Post by greenie9 on 2006-12-03
nope, didnt work for me :(

---

### Post by TrendyDark on 2006-12-03
is there a way to just completely remove these modules?

---

### Post by shutterbc on 2007-01-28
I'm having a similar problem with alsa 1.0.12rc1... everything actually worked fine until a kernel image update.  This is with a Dell D620.  OSS still works, but no sound on Ubuntu startup since it's using alsa.

---

