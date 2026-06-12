---
title: "&quot;Analog headphones&quot; (front panel jack) won't fly!"
date: 2010-12-13
forum: Multimedia Software
---

### Post by gewone on 2010-12-13
Hi guys!

First off, I'm running Ubuntu 10.10 (Maverick).
Now, switching to "Analog headphones" output won't do anything.
The volume bar is automatically set to MUTE every time I plug something (3.5mm-isch) into the jack though.
So, I'm unmuting it and pulling the volume lever up. Still no audible sound.


[I]```
gewoh@rax:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: VIA VT1708S

gewoh@rax:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
```[/I]

Any ideas?
Everything of interest.

Ty in adv~
Regards~

---

