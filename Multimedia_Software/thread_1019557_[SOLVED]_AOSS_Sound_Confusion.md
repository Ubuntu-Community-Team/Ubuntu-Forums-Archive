---
title: "[SOLVED] AOSS Sound Confusion"
date: 2008-12-23
forum: Multimedia Software
---

### Post by GreaterCore on 2008-12-23
Hi guys,

I have recently upgraded to Ubuntu 8.04 desktop but now AOSS is now giving me headaches. Previously I was able to run a few programs that share the output, and the operating system will just mix them in without any problems.

Currently I am not able to do so. Even with using "aoss" wrapper around it, only one application can output to the speaker. The other applications will not make even a tiny squeak until I quit the program that is locking the sound device, *and* then restart the program I want sound output.

There seems to be this "pulseaudio" thing that I read online, but this is adding to my confusion. What does it do to the sound stream?

Thanks!

---

### Post by markbuntu on 2008-12-23
Pulseaudio is the new sound server for Ubuntu. Unforunately it has been poorly implemented. You can find out about that and how to fix it here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

