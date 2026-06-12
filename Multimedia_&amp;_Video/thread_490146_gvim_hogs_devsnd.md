---
title: "gvim hogs /dev/snd"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by neaj on 2007-07-02
A couple of times I've noticed that sound is gone. Upon investigation it turns out that the sound device is locked by gvim. Weird. Closing gvim frees the sound. In all cases, gvim was editing a /tmp/file created by the mozex firefox extension. It happened after suspend/resume , but I can't remember if this was the case every time.

"""
 jean@klippie:~$ lsof /dev/dsp /dev/snd/pcmC0D0p
COMMAND   PID USER   FD   TYPE DEVICE SIZE  NODE NAME
gvim    12526 jean   86u   CHR  116,5      13835 /dev/snd/pcmC0D0p
 jean@klippie:~$ # close gvim
 jean@klippie:~$ lsof /dev/dsp /dev/snd/pcmC0D0p
 jean@klippie:~$
"""

Has anyone else encountered this kind of behaviour?

This is on Feisty.

---

