---
title: "Asus pro5daf alsa jack problem"
date: 2011-01-17
forum: Multimedia Software
---

### Post by zonah on 2011-01-17
Hi!
I've recently started to use headphones with my laptop, an Asus-pro5daf, everything works except for the little issue where my speakers should turn off when i plug in the headphones, I find this pretty disturbing. 

So what have I been trying to do to fix this? Well, for starters I tried to manually compile a newer Alsa-driver but I ended up with a broken driver in the end so I did a fresh install, I've also tried to edit my /etc/modprobe.d file with two different arguments one beeing "options snd-hda-intel model= asus" and the other "options snd-hda-intel model= via vt1708s", but neither of them worked. I've also tried to play around with the options in alsamixer but nevertheless I could not get my speakers to be quit. 

My aplay-l list shows the following:
card 0: SB [HDA ATI SB], unit 0: VT1708S Analog [VT1708S Analog]

Does anyone have a few pointers for me? I would certanly appreciate it!
Thanks in advance!

---

