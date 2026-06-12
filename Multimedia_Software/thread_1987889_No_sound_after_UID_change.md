---
title: "No sound after UID change"
date: 2012-05-26
forum: Multimedia Software
---

### Post by dj1202 on 2012-05-26
Hey all,
I recenlty changed my UID and now i cannot get any sound. aplay lists my sound card but the sound icon on the toolbar does not show that i have any sound devices. I re-added my user to pulse, pulse-access, and sound groups but that has not helped. I am not sure how ubuntu loads these. Its wierd because aplay lists them correctly. I hope someone might be able to point me in the right direction. 

Here is a link to my sound diagnoses from alsa:
[http://www.alsa-project.org/db/?f=ca5a4bedb70f45479155f7a5904d2fb82db9767d]("http://www.alsa-project.org/db/?f=ca5a4bedb70f45479155f7a5904d2fb82db9767d")

Thanks for the help and suggestions.

on an unrelated note i also have a radeon hd 7850 and would like to enable hdmi out for sound as well... i have yet to figure out how to do that either. Thanks again.

---

### Post by Yellow Pasque on 2012-05-27
Have you tried removing the user's pulse configuration files so that fresh ones are generated?
```
rm -rf ~/.pulse*
pulseaudio -k
```

---

