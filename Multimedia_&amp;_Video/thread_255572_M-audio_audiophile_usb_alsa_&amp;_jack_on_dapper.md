---
title: "M-audio audiophile usb alsa &amp; jack on dapper"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by Geppo on 2006-09-11
Hi,
recently i decide to jump on ubuntu for my little musician studio. I think that ubuntu-studio is great... but..
i need help to use my audiophile usb.
When i plug it ubuntu recognize it... and then nothing happen.

qtjack , using alsa driver, show me the possibility to choose "USB audiofile".

when i select the integrated sound card, it sound (bad)

can someone help me and post a link (if exist),  tutorial for alsa & jack audiophile usb configuration?

I'm a ubuntu newbie, pheraps i have to recompile the kernel includig right modules?

Thank for yours attention.

p.s. sorry for my bad english :-\"

---

### Post by Geppo on 2006-09-11
seems to be resolved

i search in alsa kernel documentatio and found

 jackd -R -dalsa -dplughw:1 -r48000 -p256 -n2 -D -Cplughw:1,1

....

but the problem now is to set qtjack (and ubuntu studio) for run with this parameter

bye.

---

### Post by majutsu on 2006-09-16
i can't help you totally, but i just got my m-audio keyboards to work.  ubuntu actually DOES recognize these usb devices instantly, it's just alsa and jack that need to be configured properly.  i got it all to work using qjackctl and patchage.  it just took fiddling and testing.  you are discovering this too.  i have to set it up eveytime though, i found no way to automate the links.  let me know if you do.

---

