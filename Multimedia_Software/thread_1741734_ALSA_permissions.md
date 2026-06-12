---
title: "ALSA permissions"
date: 2011-04-28
forum: Multimedia Software
---

### Post by Nate B on 2011-04-28
Everything was working great about 3 hours ago on my maverick machine.

Then my clumsy fingers typed:
chown -R someuser:somegroup .*

and before I had noticed the dot, I hit enter, and BAM, half my system was owned by someuser before I could stop it.

Needless to say, after much banging of head against wall, I managed to chown everything back to root (namely, /sbin, /etc, /lib, and some stuff under /usr). I 

apt-get --reinstall install

-ed a pile of packages, including ALSA. Unfortunately, now, ALSA doesn't work for non-root users. That is, 

sudo aplay /usr/share/sounds/alsa/Noise.wav

works fine, but as an unprivileged user, it spits out

"cannot find card '0'"

Although adding my users to the audio group might work, I'd read many places that this is no longer the solution to these problems.

So that leaves me with the question - where should I look to find my hosed permissions?

---

### Post by Nate B on 2011-04-28
Okay, I got lucky, and noticed that the ACLs weren't set in /dev/snd

Just in case anyone happens upon a similar problem, I managed to fix it:

sudo setfacl -m u:username:rw /dev/snd/*

If anyone sees a problem with this, please respond, I want to make sure I did this right...

---

### Post by Yellow Pasque on 2011-04-28
I think you got it right. Here's my /dev/snd permissions:
```
/dev/snd$ ls -la
total 0
drwxr-xr-x   3 root root      240 2011-04-28 12:13 .
drwxr-xr-x  20 root root     4400 2011-04-28 12:13 ..
drwxr-xr-x   2 root root       80 2011-04-28 12:13 by-path
crw-rw----+  1 root audio 116,  5 2011-04-28 12:13 controlC0
crw-rw----+  1 root audio 116,  8 2011-04-28 12:13 controlC1
crw-rw----+  1 root audio 116,  4 2011-04-28 12:13 hwC0D0
crw-rw----+  1 root audio 116,  7 2011-04-28 12:13 hwC1D0
crw-rw----+  1 root audio 116,  3 2011-04-28 12:13 pcmC0D0c
crw-rw----+  1 root audio 116,  2 2011-04-28 13:40 pcmC0D0p
crw-rw----+  1 root audio 116,  6 2011-04-28 12:13 pcmC1D3p
crw-rw----+  1 root audio 116,  1 2011-04-28 12:13 seq
crw-rw----+  1 root audio 116, 33 2011-04-28 12:13 timer
/dev/snd$ getfacl -a seq
# file: seq
# owner: root
# group: audio
user::rw-
user:*username*:rw-
group::rw-
mask::rw-
other::---
```

---

