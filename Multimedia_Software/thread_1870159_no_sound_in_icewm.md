---
title: "no sound in icewm"
date: 2011-10-26
forum: Multimedia Software
---

### Post by _Ouroboros_ on 2011-10-26
I started off with xubuntu, removed many packages and installed lubuntu, in accordance with the psychocats suggestions ( [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde) ).  I installed icewm as my window manager and have since proceeded to configure ubuntu to boot into text only, without starting X automatically, and I also disabled some non-essential services via sysv-rc-conf ( I left pulseaudio enabled ).

Everything is working fine, apart from the fact I now have no sound in icewm.

Sound, however DOES work in bash on tty1-6, when I play something using mplayer from the command line.  Correct me if I am wrong, mplayer is using ALSA?

Any suggestions?

I am starting icewm by invoking ```
$ xinit /usr/bin/icewm-session
```

---

### Post by _Ouroboros_ on 2011-10-26
Hmm...

I just found out that if I play a video in IceWM, and switch to tty1 while it is playing (the tty I invoked xinit from), I can hear the sound of the video in tty1, but it is silent again when I go back to IceWM/X on tty8

o_O

Also, if I re-install LXDM, and enable booting to X automatically, IceWM has no issues with the sound.

---

