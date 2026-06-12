---
title: "Hardy: Firefox/Flash No Sound Issues."
date: 2008-04-29
forum: Multimedia Software
---

### Post by LinuxLovesMJ on 2008-04-29
I've noticed that there is no sound in firefox while playing flash videos such as youtube. I've installed flash plugin nonfree, libflashsupport, and still no luck. I've also tweaked around with the firefoxrc file and still no sound. My sound does work for amarok, but for firefox, there is no sound at all. Any suggestions? I've tried almost everything posted on this forum and still no luck! 

Thank you.

---

### Post by GottaBeKD on 2008-04-30
I was struggling with the same issue (sound worked fine in Amarok, not in Firefox+Flash).  This worked for me:

System->Preferences->Sound

On the Sounds tab, disable "Enable software sound mixing (ESD)".

Then I killed pulseaudio:

```
sudo killall pulseaudio
```


(I should note that I'm using ALSA, and so assumed you might have been trying ALSA as well.  It has worked in the past, I'm sticking with it.  I don't know much about pulseaudio).

---

