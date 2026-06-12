---
title: "qsynth can't start"
date: 2011-07-22
forum: Multimedia Software
---

### Post by iamanidiot123 on 2011-07-22
Hi all.  I'm trying to get rosegarden to start.  I've started qjackctl with the following error:

```
daniel@daniel-desktop:~$ qjackctl
Error: "/tmp/ksocket-daniel" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-daniel" is owned by uid 1000 instead of uid 0.
klauncher(3383)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(3383)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(3383)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(3383)/kio (KLauncher): SlavePool: No communication with slave. 
```

And a window labeled 'JACK Audio Connection Kit [(default)] Stopped.' pops up anyway, and it appears to be the main window.

Now I try to start qsynth.  I get the following error:

```
daniel@daniel-desktop:~$ qsynth
qsynth: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
daniel@daniel-desktop:~$
```
and nothing happens.  If i try to start rosegarden, i get the splash and an error message, and then nothing happens( not even a freeze).

Am I doing the right thing? Help!

And, also, i'm new to ubuntu forums, so I wasn't sure where to post this.

System: Kubuntu Release 11.04, Kernel Linux 2.6.38-10-generic, GNOME 2.32.1

EDIT: Okay, now qjackctl starts without an error message, but the problem is still the same (can't start qsynth or rosegarden)

---

### Post by Perfect Storm on 2011-07-22
This may be better in the Multimedia section. Thread moved.

---

