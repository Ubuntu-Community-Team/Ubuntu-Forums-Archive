---
title: "Sound nowhere to be found"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by muz1 on 2006-08-19
Hi.
I am hoping that this post helps others not just myself.
My situation is this. I am using my onboard sound and it has stopped working.  I don't mean that linux will not detect it because it has. Everything on my system says the sound is working. I can just not hear anything.](*,) 
I went through the [Comprehensive Sound Problem Solution]("http://www.ubuntuforums.org/showthread.php?t=205449") and all went well. The sound came back. Then it happened again. After an auto update. I went back in to the /etc/modules and nothing had changed since it was working.

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
snd-via82xx

So what am I doing wrong? What is blocking the sound. Is there a module that could be missing? Wouldn't it have told me?

If anyone has any ideas, please let me know. I work with sound alot and I don't want to have to go back to windows.

Thanks heaps.
muz

---

### Post by avtolle on 2006-08-19
At the risk of being so wrong... Have you right-clicked the speaker icon to see if your sound output is muted?

---

