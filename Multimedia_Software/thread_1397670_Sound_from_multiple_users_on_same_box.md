---
title: "Sound from multiple users on same box"
date: 2010-02-03
forum: Multimedia Software
---

### Post by Hichhiker on 2010-02-03
Ok, for various (mostly security) reasons I was experimenting in running certain apps as a different user id (on Karmic).

I can get X to forward to my main session without a problem but I cannot get the sound to work. Sound works fine in my main session, but when I run sound as another user I get plenty of errors like:

[PHP]
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
[/PHP]I am not a big linux GUI person, so I have rarely dealt with sound systems under Linux. What is the simplest way to get this to work in a relatively secure way? (I do realize that my security is already a bit compromised by allowing the secondary user access to X, but that can't be helped)

Thanks.

-HH

---

### Post by machineghost on 2010-02-04
Bump.  The same thing is happening to me, only I actually have multiple users running (my girlfriend and I use different users to keep our preferences/bookmarks/etc. separate).  Very curious to hear if there is a fix.

---

### Post by reto on 2010-02-05
occasionally it works, but mostly it doesn't :(

currently sound works for the user I logged in, as well as for root but not for other users (all in the audio group) when doing su or sudo -u.

cheers,
reto

---

### Post by reto on 2010-02-05
interestingly sound also works when logging in the user that doesn't have sound with su or sudo on the terminal i get with ALT-SHIFT-F1.

well, programms like espeak work, but no sound in a skype or firefox started that way (setting DISPLAY to ":0.0".

---

