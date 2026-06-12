---
title: "gtick sound problem"
date: 2009-06-21
forum: Multimedia Software
---

### Post by harrybazeegar on 2009-06-21
Hi,

I use gtick as a metronome on my ubuntu box. 
But I noticed that no other sound can play while gtick runs, and gtick fails if other media players (eg: vlc) is running.

Now, I know that Linux has some issues with its sound mixing, what with OSS, ALSA, PulseAudio, and everybody's brother and sister being involved.

For some time, I went along with it, and did not try running gtick along with other media players.

Today, I read [http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html) , and if it is to be believed, OSSv4 has sound mixing built in automatically.

So as replies of this question I'd like to have answers that reflect the current state of Ubuntu's sound system (whether it supports OSS or ALSA or whatever). Also, I'd like to know when all of Ubuntu's sound mixing problems would be history.

jrh

PS: I use Ubuntu 8.10. I've not had time to upgrade to 9.04 yet, I plan to do that soon. Are these problems gone in 9.04 already?

---

### Post by harrybazeegar on 2009-06-21
By the way, GTick uses the file /dev/dsp for sound output, not the PulseAudio server. So is this purely an OSS problem?

---

### Post by harrybazeegar on 2009-06-23
/bump

hello, all.. anybody home?

---

### Post by mindo on 2009-06-25
Hi!

You need to install oss support for alsa

```
sudo apt-get install alsa-oss
```

and then run GTick like this: 

```
aoss gtick 
```

and everything should work :)

---

### Post by gacb on 2011-09-16
You might want to try gtklick instead. I have the same problem with Gtick, but just had to change the preference to default sound to get gtklick working.

---

