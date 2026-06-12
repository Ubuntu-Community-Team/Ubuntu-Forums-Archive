---
title: "&quot;Resetting&quot; Audio?"
date: 2013-11-18
forum: Multimedia Software
---

### Post by djpemberton on 2013-11-18
I'm using Kubuntu 13.10. My sound was working fine before. Now . . . I was given a MS LifeChat LX-3000 headset. I plugged it in and got to work trying to get it to work right. I may get back to trying that at a later time. My more pressing problem now is that I accidently tweaked some settings (don't ask me which) and now my Creative 2.1 system won't make a sound (it worked fine before). In fact, there isn't even 2.1 listed as an option anywhere! The options in Phonon skip right to 5.1. I'm desperate, as all of this working properly is vital for my school and work. Is there any way to make Kubuntu reset/forget all of the sound stuff, redetect everything, and start fresh? I need a solution soon in order to at least get my speakers working like they were. Then, I can worry about the headset.

---

### Post by grier-devon on 2013-11-18
Try 
```
sudo alsa force-reload
```
make sure to reboot once it is complete.

PS - Sorry if I didn't catch it in time but I put "also" when I meant to put "alsa", I fixed it, sorry about that.

---

### Post by oldos2er on 2013-11-18
Moved to Multimedia & Video.

---

### Post by djpemberton on 2013-11-18
> **grier-devon said:**
> Try 
```
sudo alsa force-reload
```
make sure to reboot once it is complete.

That seems to have fixed it! I actually thought I had already tried that due to suggestions I saw elsewhere. Somehow things seem to work now. Thanks.

---

### Post by grier-devon on 2013-11-18
Glad to hear and your welcome

---

