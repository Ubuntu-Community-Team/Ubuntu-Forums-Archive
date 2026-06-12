---
title: "pulseaudio startup error"
date: 2008-08-20
forum: Multimedia Software
---

### Post by pulse00 on 2008-08-20
Hi all,

i'm trying to get pulseaudio to run on ubuntu 8.04, but when i try to start it i get the following error:

```
E: mutex-posix.c: Assertion 'pthread_mutex_unlock(&m->mutex) == 0' failed at pulsecore/mutex-posix.c:98, function pa_mutex_unlock(). Aborting.
Aborted

```

After searching the web for a solution, i mostly found that the reason would be a broken libtool version, namely 1.5.22. After upgrading everything should be ok:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/165220](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/165220)
[http://osdir.com/ml/audio.pulseaudio.general/2007-10/msg00038.html](http://osdir.com/ml/audio.pulseaudio.general/2007-10/msg00038.html)

However my installed version of libtool/libtdl3 is 1.5.26-1. There is no
newer version available in the package manager.

One other solution mentions uninstalling everything pulseaudio related, and reinstalling again. When uninstalling pulseaudio related stuff there's an ubuntu-desktop dependency though, which i'd rather not remove i guess ;)

Anyone knows what i could do to get pulseaudio work ? 


thanks !

---

