---
title: "Left Channel Crackle"
date: 2008-09-18
forum: Multimedia Software
---

### Post by mattgen88 on 2008-09-18
Since I've installed Ubuntu I've been dealing with this problem, I can get it fixed every so often but it often reemerges.

The left sound channel on my computer (XPS 400, Intel Pentium D dual core, integrated sound card - SigmaTel Stac92xx)

generally I do this to fix the issue:
# apt-get install libncurses5-dev gettext libncursesw5-dev speex libspeex-dev liba52-0.7.4-dev libsamplerate0-dev jackd jack-rack libjack0-100.0-dev checkinstall build-essential linux-headers-$(uname -r)
# apt-get install mercurial automake1.4
# mkdir alsa
# cd alsa
# hg clone [http://hg-mirror.alsa-project.org/alsa-driver](http://hg-mirror.alsa-project.org/alsa-driver) alsa-driver
# hg clone [http://hg-mirror.alsa-project.org/alsa-kernel](http://hg-mirror.alsa-project.org/alsa-kernel) alsa-kernel
# cd alsa-driver
# ./hgcompile
# sudo tar zvcf oldsound.tgz /lib/modules/`uname -r`/kernel/sound/*

However it seems to come back and not always work. Also sometimes it is solved by hibernating the computer and waking it back up.

Its a weird problem that seems to also affect a lot of macbooks with the same processor.

I was curious if anyone knew a permanent solution or fix that will always work, or even just an explanation as to why it happens.

---

### Post by mattgen88 on 2008-09-18
bumping this for hope that someone has any ideas.

---

