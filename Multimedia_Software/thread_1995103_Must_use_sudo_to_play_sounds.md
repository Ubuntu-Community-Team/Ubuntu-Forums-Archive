---
title: "Must use sudo to play sounds"
date: 2012-06-03
forum: Multimedia Software
---

### Post by Tamalin on 2012-06-03
Hi,
I am unable to play sounds without switching to root.
For instance:
```

$ aplay /usr/share/sounds/alsa/Front_Center.wav # silent
$ sudo aplay /usr/share/sounds/alsa/Front_Center.wav # plays loudly

$ alsamixer
cannot open mixer: No such file or directory
$ sudo alsamixer # opens alsamixer

```

I added myself to the audio and pulse-access groups, but I don't see them listed when I run groups:
```

$ sudo adduser tamalin audio
$ sudo adduser tamalin pulse-access
$ groups
tamalin adm cdrom sudo dip plugdev lpadmin sambashare subversion

```

I found another thread from two years ago [here]("http://ubuntuforums.org/showthread.php?t=1418342"), which found that running 'rm -r ~/.pulse' temporarily resolved the problem, but that didn't work for me.

---

