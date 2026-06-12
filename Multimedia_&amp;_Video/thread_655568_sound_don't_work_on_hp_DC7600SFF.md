---
title: "sound don't work on hp DC7600SFF"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by um07 on 2008-01-01
PLEASE COULD :


someone help me get sound on a HP DC7600 SMALL FORM FACTOR . it use the realtek sound. please could provide dummy proof gude on how to install sound on dc7600.


thank you

---

### Post by um07 on 2008-01-04
bump  any1 please help, i dont want go back 2 windows xp!

---

### Post by um07 on 2008-01-06
bump ???


anyone please i cant live without sound !


i am going to windows xp  if i dnt get sound by wtuesday :(

---

### Post by Yellow Pasque on 2008-01-06
Put the following into the /etc/modprobe.d/alsa-base file.
```
options snd-hda-intel model=hp
```

If that doesn't work, try following the OSSv4 guide linked in my signature.

---

### Post by Jab0rnal on 2008-02-17
Temüjin,

I have also got the same computer as in this thread.

The above didn't work for me but following the OSS4 link on your sig seems to have enabled the sound. Nice work.

A few queries, when booting my comp the sound doesn't work until i get logged in, i.e. the login sound doesn't work, no big deal i know, i just wondered why?

Secondly, once the default sound icon (from top right) is removed there is no way of changing the system volume. Is there a way of keeping this icon and having it function correctly or does it simply not work with the OSS4 method.

Many thanks again for fixing my issue.

Cheers,
Jab0rnal.

---

### Post by Yellow Pasque on 2008-02-17
Jab,
Go to Systems -> Preferences -> Sounds and make sure everything is set to OSS, including the mixer.

To use the default sound icon, you need to download the patch I pointed to in the guide. Just  save the file and open it like normal. The directions are included in the README and are fairly simple.
> ADDENDUM: Volume Control Patch The current gstreamer-based volume control in GNOME is incompatible with OSSv4, meaning your mouse wheel and media buttons won't work. To remedy the issue, try Clive Wright's [patch](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=). (AMD64 version [here](http://ubuntuforums.org/attachment.php?attachmentid=55770&d=1199848927)).

You can also right-click on the panel/menu bar at the top of your screen and select 'add to panel' -> Custom Application Launcher, and use the command: ossxmix. This should create an icon that you click once to bring up the OSS mixer app.

---

### Post by Nick w on 2008-03-17
OSS4 worked a treat

thanks very much

---

### Post by Yellow Pasque on 2008-03-17
> **Nick w said:**
> OSS4 worked a treat

thanks very much
Aye. It's nice to see Ubuntu users on the other side of "the pond" :p

---

