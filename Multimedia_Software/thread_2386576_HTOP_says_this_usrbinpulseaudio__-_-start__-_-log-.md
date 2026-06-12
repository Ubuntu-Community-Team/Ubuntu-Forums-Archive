---
title: "HTOP says this /usr/bin/pulseaudio  - -start  - -log-target=syslog"
date: 2018-03-07
forum: Multimedia Software
---

### Post by jimbean on 2018-03-07
HTOP says this /usr/bin/pulseaudio  - -start  - -log-target=syslog 
with a minus -11 highlighted in red in the NI column 
and a computer lockup for a second or two
every time i move a card in aisleriot the great card game in linux {Ubuntu 17.10}
  
i dont like to use any nvidia drivers they cause troubles 
i have disabled pulse audio and all works well except no sound
I am browsing the trouble shooting sound now guide you guys have and its great
but i dont allway`s see things that are right in front of me so why im reading for the second time i put this on the forums 
any help thanks

---

### Post by TheFu on 2018-03-07
I found that telling pulseaudio to NOT use shared memory fixed issues I had.  It was crashing 10x a day.  Don't know if that will help you or not. Can't hurt to try.
File is ~/.config/pulse/client.conf

Setting is:
```
enable-shm = no
```
Of course, really should look at the logs for any pulse issues to actually know what is causing it.

Also, this only works if the system is actually using pulse. Lubuntu doesn't. Other flavors might not either.

---

