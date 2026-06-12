---
title: "Odd sound issues...."
date: 2008-06-20
forum: Multimedia Software
---

### Post by heartfrappe on 2008-06-20
OK folks, I'm new to the Ubuntu world.. not sure if I've done something wrong, but here's my story:

Long time winblows user, recently (about a year ago) I ugraded to Vista on a prebuilt laptop.

A buddy of mine got me into Ubuntu and so I dual booted.

And now, my dilemma:

In windows, my sound works fine. can play music and everything, can use headphones: no problems.

In Ubuntu, sound works with chassis speakers only (not that it's that bad, just want privacy), but when I plug in head phones... nothing... have done updates, have tried switching mixers in the sound properties... no luck...

I'm using a Toshiba Satellite P105 series 17" notebook... any thoughts? feel free to e-mail me at [email]chris.collins04@gmail.com[/email] and let me know if you can help... We've been wracking our brains to no avail.:confused:

---

### Post by heartfrappe on 2008-06-20
Also... a side note... I've tried the alsamixergui fix... no good... also tried the acer fix that was suggested to someone else.. no good.. still looking.. PLEASE HELP!!!!

---

### Post by xc3RnbFO8P on 2008-06-21
You can try this:

> 
"WORKS GREAT !!!
finaly i have sound from the headphones jack

terminal: gksu gedit /etc/modprobe.d/alsa-base
add
options snd-hda-intel model=laptop-micsense

many thanks" - kavatzoulas

This worked for me with a p105-s6177
[https://bugs.launchpad.net/ubuntu/+bug/218817]("https://bugs.launchpad.net/ubuntu/+bug/218817")

---

