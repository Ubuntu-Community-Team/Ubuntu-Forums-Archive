---
title: "Mplayer cuts off last 1 or 2 seconds of mp3 / wav files"
date: 2009-05-05
forum: Multimedia Software
---

### Post by bademeister on 2009-05-05
Hi all,

I have just noticed that mplayer seems to cut off the last 1 or 2 seconds of audio files (tested with mp3 and wav files). This is especially annoying if the files are only 2 or 3 seconds long!

To reproduce try the following:
1. Download [http://www.leo.org/dict/audio_en/epiphany.mp3]("http://www.leo.org/dict/audio_en/epiphany.mp3")
2. Replay with mplayer (if you have it as your bowser plugin, just clicking the above link should do it).
3. Replay with some other mp3 player (say totem or rhythmbox).

When I do this with mplayer, I hear "epiph", but replaying the mp3 with some other player, I hear the entire word.

Thanks in advance for your help
cheers
Paul

---

### Post by andrew.46 on 2009-05-05
Hi bademeister,

I downloaded your file but using the svn MPlayer:

```
andrew@skamandros~$ mplayer | head -n1
MPlayer SVN-r29242-4.2.4 (C) 2000-2009 MPlayer Team
```

The entire file played flawlessly. I assume you are you using the repository MPlayer?

Andrew

---

### Post by bademeister on 2009-05-05
Hello Andrew,

yes, my mplayer is from the repo. 
your command gives
```

$ mplayer | head -n1
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team

```

thanks 
Paul

---

### Post by x33a on 2009-05-05
maybe crossfading is enabled?

---

### Post by bademeister on 2009-05-05
Hello x33a,

this might be the case, but where do I disable it? I couldn't anything in the preferences. I also installed smplayer but nothing was to be found there either.

Something funny: smplayer complained that mplayer wasn't the newest version, but I installed the current version from the jaunty repos.

thanks

Paul

---

### Post by x33a on 2009-05-05
ubuntu repositories don't have the latest version of mplayer.

to get the latest mplayer and smplayer, add these repositories

# smplayer, mplayer repo

deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) jaunty main

as for the crossfading issue, i also couldn't find any option for the same in mplayer preferences, so maybe it doesn't have crossfading.

---

### Post by andrew.46 on 2009-05-05
Hi bademeister,

> **bademeister said:**
> Something funny: smplayer complained that mplayer wasn't the newest version, but I installed the current version from the jaunty repos.

SMPlayer is complaining because the version of MPlayer in the Jaunty repository is almost 2 years old and *badly* out of date. The creator of SMPlayer has been good enough to provide a much more recent copy of MPlayer in a PPA:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

and this might be well worth trying if only to get the full word from your file :-).

Andrew

---

### Post by bademeister on 2009-05-05
Hey guys,

I just installed the mplayer from the above mentioned launchpad repo and it works great now. Thanks for pointing this out. I hope the newer version makes it into ubuntu real soon now ;)

thanks
Paul

---

