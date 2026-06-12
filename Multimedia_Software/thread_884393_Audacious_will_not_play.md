---
title: "Audacious will not play"
date: 2008-08-08
forum: Multimedia Software
---

### Post by linko47 on 2008-08-08
My music runs just fine in amarok, but not audacious.  I have installed, reinstalled, removed all configs, reinstalled again, nothing works.  I receive this error (when I press the play button) when audacious is run in the terminal:

```

linko@X61:~$ audacious
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

```

Thanks for any help fellow ubuntu'ers

Edit:

Just tried on my girlfriends xubuntu laptop, and I get the exact same error....

---

### Post by gandaran on 2008-08-09
remove audacious-crossfade if it's installed and install ubuntu-restricted-extras.

---

### Post by markbuntu on 2008-08-09
Change the output plugin in Preferences/Audio to pulse audio or alsa.

---

### Post by linko47 on 2008-08-09
> **markbuntu said:**
> Change the output plugin in Preferences/Audio to pulse audio or alsa.

Thanks! 
Thanks!
Thanks!

Changed to alsa, did the trick!

---

### Post by spisek on 2008-08-11
> **markbuntu said:**
> Change the output plugin in Preferences/Audio to pulse audio or alsa.

Thanks, works perfect. Thanks also to your mother and father!

---

### Post by mrgedman11 on 2009-01-05
although noone probably cares, i had the same problem, and a quick search led me to this thread.  changed to alsa, and BAM! music with little overhead :)

thanks guys

---

### Post by ohgodnotanother1 on 2009-02-02
Changing the output/plugin to ALSA helps me to play audio files. Before the audio file wasn't playing at all.

However now I see the file playing in Audacious but I don't hear a single sound. Does this sound familiar to anyone?

If yes, please also post the solution here:
[http://ubuntuforums.org/showthread.php?t=1057101](http://ubuntuforums.org/showthread.php?t=1057101)

**EDIT: I had to disable the on-board audio chip in the BIOS and on the next boot-up all sounds worked fine.**

---

