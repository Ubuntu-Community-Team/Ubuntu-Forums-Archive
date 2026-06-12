---
title: "No sound! Having a HDA Intel card :("
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by thamarok on 2006-12-02
EDIT: I solved this by installing alsa-utils from source, see this thread: [http://ubuntuforums.org/showthread.php?t=311166](http://ubuntuforums.org/showthread.php?t=311166)

Hello!

I have made a fresh install of Ubuntu 6.10 Edgy Eft Server Edition and I have installed the latest KDE... Well, everything seemed to be fine fine and I was able to get sound, but then after I installed Cedega and played GTA Vice City, the game crashed and I was not able to get sound from any application!

I have read the Comprehensive Sound Problems thread, but the solutions there didn't help me much. The only way to get sound back is to reboot the computer (restarting the X server or KDE doesn't help)..

On Debian, I used alsaconf, but here on Ubuntu there's nothing like that even if alsa-utils is installed ](*,) 

The no-sound-ness seems to be happening after a program that uses ALSA crashes.. For example, Linux MultiMedia Studio (LMMS) crashes quite often, and when it crashes, I can't get any sound anymore from any application...

Please help me to solve this! I hate it to reboot my computer!
Thanks!

---

### Post by DougieFresh4U on 2006-12-02
I've been having similar sound issue since fresh install last week (Dapper 6.06) using Intel card. Nobody has come up w/solution yet ](*,) :-k

---

### Post by thamarok on 2006-12-02
I guess we are on the same boat then... If Ubuntu would get alsaconf back to alsa-utils, all my problems would get solved!

Hey Ubuntu developers, do you read this? Many people here have problems with their soundcard and they need the alsaconf utility; give me even one _reasonable_ reason why did you pull it out?!

I guess I'll have to hack the Debian alsa-utils package and mod the Ubuntu package so I can have alsaconf again.. When I'm ready I'll post it here so others can have alsaconf.

I just don't understand this [-(

---

