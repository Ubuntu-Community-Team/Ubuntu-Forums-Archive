---
title: "Sound Problem"
date: 2009-09-30
forum: Multimedia Software
---

### Post by Jimoid on 2009-09-30
I have a problem with my sound and have no idea how to fix it, therefore hoping someone here will be able to help me.

Last week I was listening to the radio (BBC iPlayer on Firefox) when I needed to find a file containing a certain string. In a terminal, as root, I did a find command:

```
find / -type f | xargs grep thingINeededToFind
```

The output scrolled on the screen as expected, however after a while the sound output became stuck in a loop. I stopped the audio stream and started it again, but I only heard a crackling noise. Now all I hear from audio output is a crackle in place of the correct audio output. Firefox, the system (e.g. at boot), vlc, rhythmbox etc. all produce the same crackle in place of normal audio output.

The things I have tried so far are restart alsa-utils, reboot and followed the "Sticky: Comprehensive Sound Problem Solutions Guide" at the beginning of the Multimedia and Video category, however none of these have helped.

My guess is that the find and grep commands opened and looked inside an audio related file that they should not have (my fault for running the command as root). I guess that I may need to reinstall some files, but I don't know which. Any and all help gratefully accepted.

The system runs Ubuntu 9.04

jimmy@levin:~$ uname -a
Linux levin 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

---

### Post by sopasakis on 2009-09-30
Hi! I encountered exactly(!) the same problem. I installed ubuntu 9.04 on my laptop about one year ago and everything worked fine - including my ATI sound card - and one day (today), I booted and tried to listen some music but the only thing I hear is an annoying noise... (Its not my ears because others hear the same noise as well!)

I unistalled, rebooted and reinstalled the sound drivers but the bloody problem remains!?! I think, the ubuntu developers should take *seriously* into account that issue! Is there something like system recovery on ubuntu???

---

### Post by ajpearson on 2011-02-03
Did you ever get an answer to this crackle on every audio file - I now have the same problem?

Thanks

Andrew

---

