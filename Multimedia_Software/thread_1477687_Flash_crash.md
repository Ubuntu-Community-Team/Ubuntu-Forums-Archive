---
title: "Flash crash"
date: 2010-05-09
forum: Multimedia Software
---

### Post by dcroxton on 2010-05-09
I'm having an interesting problem with flash video.  There are two versions in synaptic, the Adobe version (which appears to be the Ubuntu preference) and the flashplugin-nonfree.  If I uninstall my existing one and install the other one, flash works -- once.  After I stop and restart firefox, it doesn't work anymore (no sound + picture freezes after about 2 seconds, firefox freezes and has to be restarted).  It doesn't work again until I uninstall the existing flash plugin and re-install the other one.

The crazy thing is that *both* versions are obviously working fine until firefox restarts, so there is obviously no fundamental problem like hardware incompatibility.  If I could only figure out what changes after shutting down firefox...

BTW, this is 32-bit.  I ran firefox with --debug on and got the following messages (repeated many times):

[New Thread 0x236cb70 (LWP 16545)]
ALSA lib pcm_pulse.c:732:(pulse_prepare) PulseAudio: Unable to create stream: Too large

mmap() failed: Cannot allocate memory

---

### Post by dcroxton on 2010-05-10
Ideas?

---

### Post by nitstorm on 2010-05-10
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by dcroxton on 2010-05-13
I found another thread that said to create a symlink in ~/.mozilla/plugins.  All the solutions I tried (including installing the plugin directly from Adobe) involved putting a file directly in the plugins directory.  I have no idea why the symlink helped, but it solved the problem.

---

