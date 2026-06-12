---
title: "No Sound on Fiesty and Toshiba Satellite S6114"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by blahblahyaya on 2008-02-19
I have no sound on my Toshiba Satellite Pro P105 S6114.  Did a full install of 7.10 soon after it came out.  Everything else works but no sound. That was last year.  I'm a patient man, but I would LOVE to get the sound working again.  I have tried the instructions in many of the posts to no avail.  Consider me a Linux neophyte.  Any help would be appreciated.
Some random commands I've seen in other posts: 
dmesg | grep Ubuntu
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)

lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

modinfo snd
filename:       /lib/modules/2.6.22-14-generic/kernel/sound/acore/snd.ko
alias:          char-major-116-*
license:        GPL
description:    Advanced Linux Sound Architecture driver for soundcards.
author:         Jaroslav Kysela <perex@perex.cz>
srcversion:     79885E6C07C5F07B670089C
depends:        soundcore
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           major:Major # for sound driver. (int)
parm:           cards_limit:Count of auto-loadable soundcards. (int)

/etc/modprobe.d/alsa-base
tried: 
options snd-hda-intel model=auto
laptop
3stack

---

### Post by blahblahyaya on 2008-05-17
Upgrade to 8.04 fixed it.

---

