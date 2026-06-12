---
title: "/dev/sound/dsp - device is busy???!"
date: 2005-10-28
forum: Multimedia &amp; Video
---

### Post by kreso on 2005-10-28
Whenever I run a second program that uses sound, I get this message in the console:

/dev/sound/dsp - device is busy

Can't two applications share a sound output and mix them before playback?

This worked fine on hoary.

Any leads?

---

### Post by DarkB on 2005-10-30
i also have this problem (two applications can't produce sound at the same time) ... namely realplayer and skype won't work fine. if one is the running the other complains about the sound being busy

this is starting to get annoying .... i need help

---

### Post by Antioch on 2005-10-30
Hmm, I recall a thread on the gentoo forums that dealt with how to mix the sound. Unfortunatley I've yet to see one here.

Im trying to fix it, so when I do I'll write something up.

---

### Post by Antioch on 2005-10-30
[http://www.ubuntuforums.org/showthread.php?t=44753&highlight=sound+mix](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=sound+mix)

I think that should do the trick.

---

### Post by Antioch on 2005-10-30
Hey, are you guys running Breezy or Hoary? Because I just switched my BMP to use ALSA and now gaim and BMP work together flawlessly. Much better than when I used that old gentoo hack (ie, there are no sound crackles). It should work for xmms as well, I believe theres an option for it. In any case, switch as many of your programs to ALSA if youre using breezy and things seem to work out of the box. 

This is due to the fact that Breezy uses the new ALSA, v1.09, which has dmix enabled out of the box. It also produces a far better mixed sound than the other method I posted above.

If you read that thread it should explain some things. What I believe happens in breezy is that youve got new ALSA, and a lib that forwards all ESD to ALSA (which is why gaim works at the same time as ALSA). 

Anyways, read that thread I posted before if you want to keep on using Hoary, upgrade to breezy, or try using backports to get newer ALSA libs.

---

### Post by Gaming_Junkie on 2005-11-01
[QUOTE=Antioch][http://www.ubuntuforums.org/showthread.php?t=44753&highlight=sound+mix](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=sound+mix)

I think that should do the trick.[/QUOTE]

I have tried that out before, and the only thing it got me was a lot of frustration and no sound at all.  I'm pretty sure I used the instructions word for word.  I tried that on Hoary, and now on Breezy, but never got it to work.  I wouldn't recommend it to anyone else.

---

### Post by iH8forcedRegistration on 2005-11-01
Take a look at [this page in the alsa wiki]("http://alsa.opensrc.org/index.php?page=DmixPlugin")

I'd recommend trying to use the configuration they provide in part 6 with the pcm.default line uncommented. If that doesn't help, run these commands the next time you get that device busy message and paste their output:

```

ps -A | grep esd
ps -A | grep artsd
sudo fuser -v /dev/snd/* /dev/dsp

```

---

### Post by kreso on 2005-11-02
what I don't understand is why didnt they include this obviously necesary thing in breezy?

---

### Post by eier on 2008-03-16
hi, i had the same problem,my solution was closing steam.

---

