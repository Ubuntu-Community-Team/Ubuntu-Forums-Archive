---
title: "Problems with SB Live/emu10k1 under 8.10"
date: 2008-11-02
forum: Multimedia Software
---

### Post by gotfork on 2008-11-02
EDIT:  This problem has been resolved.  I recently did the following command found at [https://help.ubuntu.com/community/SoundTroubleshooting#Basic%20Troubleshooting%20Steps]("https://help.ubuntu.com/community/SoundTroubleshooting#Basic%20Troubleshooting%20Steps")

```
 sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic 
```

Amazingly this is all I needed to do, although who knows if this would have worked several weeks ago when I started having this problem.  I hope this can help other people who have similar problems!  Original post is as follows:


Howdy, thanks in advance for any help you can provide.

A few months ago the on-board sound card on my computer died and I installed a SoundBlaster Live 5.1 card, which I was able to get to work after a bit of tinkering and unfortunately I don't remember exactly what I did.  However, while updating to 8.10 last night I accidentally clicked to replace my custom /etc/modprobe.b/alsa-base file and now my sound doesn't work.

Alsa-info is here:  [http://www.alsa-project.org/db/?f=8fac8dd52a6a4d66cca553ef2aeb37e508bb48e3]("http://www.alsa-project.org/db/?f=8fac8dd52a6a4d66cca553ef2aeb37e508bb48e3")

Steps taken so far:


[LIST]
[*]aplay -l fails.
[*]lspci -v lists my sound card
[*]sudo modprobe snd-emu10k1 fails with: FATAL: Module snd_emu10k1 not found. FATAL: Error running install command for snd_emu10k1
[*]Followed the "getting drivers from a fresh kernel" step on [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") which produced no change
[*]Followed the "alsa driver compilation" step on the same page.  I used the module-assistant and it failed with the following error:
[/LIST]

```
make[3]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;
 &#9474; /usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/alsa-driver       &#9618;
 &#9474; CPP="gcc -E" CC="gcc" modules                                              &#9618;
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.25-2-386'          &#9618;
 &#9474; make[3]: Makefile: No such file or directory                               &#9618;
 &#9474; make[3]: *** No rule to make target `Makefile'.  Stop.                     &#9618;
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.25-2-386'           &#9618;
 &#9474; make[2]: *** [compile] Error 2                                             &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646;
 &#9474; make: *** [kdist_image] Error 2         
```

Anyone have any ideas?  I seem to not remember having the same problem before.  Thanks again,

Alex

---

### Post by gotfork on 2008-11-02
Also tried the "using drivers from alsa project" step on the same guide page.

---

### Post by gotfork on 2008-11-03
Shameless bump =/

Edit:  Also tried and failed to switch over to OSS and use that.

---

### Post by gotfork on 2008-11-04
Attaching logfile from uxchecker

---

### Post by gotfork on 2008-11-05
3 day bump =/

---

### Post by gotfork on 2008-11-09
1 Week bump =/

I think I've exhausted all the possible fixes I can find on websites/this forum, and it seems like lots of other people are having similar problems with 8.10.  Is this a known bug, and does it seem possible that I might be able to revert back to 8.04 until this gets fixed?

---

### Post by gotfork on 2008-11-19
2 week bump, and none of the updates since then seem to have made a difference.  I guess I'll revert back to 8.04 this weekend...

---

### Post by gotfork on 2009-01-03
Solved without reverting, see first post!

---

