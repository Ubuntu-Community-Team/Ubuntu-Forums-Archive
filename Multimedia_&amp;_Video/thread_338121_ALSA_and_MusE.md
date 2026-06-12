---
title: "ALSA and MusE"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by Kossilar on 2007-01-14
Hello, 

> 
I just installed MusE on my system, but when I run it I get the following error:

MusE failed to find a Jack audio server.

MusE will continue without audio support (-a switch)!

If this was not intended check that Jack was started. If Jack was started check that it was started as the same user as MusE.

I click "OK" and:

> MusE failed to initialize the Alsa midi subsystem, check your configuration.

I'm using a Realtek HI Definition onboard soundcard. Its attached to my P5WD2 premium motherboard. 

Does anybody have any idea what's causing this problem? :-k 

Sound works fine in all the regular applications.

Thanks.

---

### Post by Kossilar on 2007-01-16
*bump*

---

### Post by yippy on 2007-01-17
I got past that point by just loading the Alsa sequencer module:
$ sudo mod-probe snd-seq

But now I get a segmentation fault.  Maybe yours will work!

---

### Post by Kossilar on 2007-01-17
Thanks for the post. But I don't have mod-probe... Do you know where I can  get it?

---

### Post by sgx on 2007-01-21
> **Kossilar said:**
> Thanks for the post. But I don't have mod-probe... Do you know where I can  get it?
check in /sbin for modprobe (without the - ) I never had a distro come without it...
You may have to add a path statement to /home/usr/bashrc file, create it
first if you have none...

PATH=$PATH:$HOME/bin:/bin:/sbin:/usr/bin:/usr/lib/dssi:/opt:/usr/sbin:

yours may include what directories you like, each directory separated by a :
hope this helps...

---

### Post by Kossilar on 2007-01-23
Ah HA! It started. Thanks a lot. Maybe now I can figure out how this Jack Server thing works.

:) Thanks

---

