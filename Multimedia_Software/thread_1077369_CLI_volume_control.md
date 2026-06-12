---
title: "CLI volume control"
date: 2009-02-22
forum: Multimedia Software
---

### Post by Pimterry on 2009-02-22
Does anybody know how to set the volume for a specific channel on the command line? I'm not talking about alsamixer, where I have to go the channel and set it by hand, I want to be able to mute the side channel with something like ```
somecommand -c side mute
```

I'm trying to write a teeny weeny script that mutes my speakers and unmutes my headphones (which are always plugged in) when run, so I can map it to a key and stop mucking about with the volume control.  Everything's going through PulseAudio. Thanks!

---

### Post by Pimterry on 2009-03-01
Bump.

---

### Post by ink_rus on 2010-12-23
Use
> amixer sset Master toggle
read more [there]("http://www.howtogeek.com/howto/linux/create-a-shortcut-or-hotkey-to-mute-the-speakers-on-linux/")

or use *ossmix*

---

