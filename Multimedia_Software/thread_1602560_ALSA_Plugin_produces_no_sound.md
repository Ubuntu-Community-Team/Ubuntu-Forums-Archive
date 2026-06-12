---
title: "ALSA Plugin produces no sound"
date: 2010-10-21
forum: Multimedia Software
---

### Post by Stephen_at on 2010-10-21
I've no problems with sound on my laptop - it all works fine but Flash produces no sound at all.

I've got the Pulse audio applet running and when I'm using Rhythmbox it shows that on the playback tab and you can see the signal on the signal bar.

Viewing Flash videos shows the ALSA Plugin but shows no signal on the signal bar.

I'm sure it must be something simple - I'm running 10.04

---

### Post by Stephen_at on 2010-10-26
Anyone got any ideas or suggestions? Looking round it seems to be a common problem with no single solution and I've just about run out of ideas.

Or do I just accept that Flash under ubuntu 10.04 is always going to be mute?

---

### Post by CGANIERE on 2010-10-26
I've got the same problem.

---

### Post by alexandari on 2010-10-26
Sounds idiotic but,check out if your PCM is all the way up

```
alsamixer
```

---

### Post by rayfos on 2010-10-26
I am having the same problem:

Dell inspiron 530S no sound after boot
Ubuntu 10.04 makes the usual sounds with boot but is silent after that. Loss of boot capability happened after installing and removing about 3 audio programs. After the total re-install on whole disk, it boots up OK but is soundless except for initial boot sound.

Comprehensive Sound Problem Solutions Guide v0.5e has been followed with no resolution of problem.

Code:

alsamixer

Shows the bars etc. I don't know what it means or what to do with this.  I haven't figured how or what to do with it!

Any other suggestions/help would be much appreciated.
Thanks

:)

---

### Post by Mia1990 on 2010-10-26
The only problem on the alsa sound i know of is if your using a dial up modem there is a special driver out if your using that kind of modem sorry i don't know the name of it.

---

### Post by CGANIERE on 2010-10-26
Solved!
I had an old Shockwave flash plug-in in my mozilla directory. Once I moved it to the trash, the more up to date plug-in (installed through synaptic) took over.

Flash Aid helped me find what was going wrong.

[http://ubuntuforums.org/showthread.php?t=1491268&highlight=sound+flash+videos&page=7](http://ubuntuforums.org/showthread.php?t=1491268&highlight=sound+flash+videos&page=7)

---

### Post by Stephen_at on 2010-10-30
> **alexandari said:**
> Sounds idiotic but,check out if your PCM is all the way up

```
alsamixer
```


Oh it was - I'd turned everything up to full and everything was working fine apart from Flash.

Then yesterday someone sent me a link with a Youtube video in it and the sound was there and very loud.

I have no idea what made it work again because I'd not changed anything between it not working and it suddenly working again.

---

