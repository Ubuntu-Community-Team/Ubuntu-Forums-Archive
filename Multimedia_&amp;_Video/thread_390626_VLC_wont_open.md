---
title: "VLC wont open"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by Hurons on 2007-03-22
Hello

I cannot get VLC to open anymore:

~$ vlc
VLC media player 0.8.6 Janus
[00000001] main private error: no memcpy module matched "any"
[00000013] main interface error: no interface module matched "hotkeys,none"
[00000013] main interface error: no suitable interface module
[00000001] main private error: interface "hotkeys,none" initialization failed
[00000014] main interface error: no interface module matched "screensaver,none"
[00000014] main interface error: no suitable interface module
[00000001] main private error: interface "screensaver,none" initialization failed
[00000015] main interface error: no interface module matched "any"
[00000015] main interface error: no suitable interface module
[00000001] main private error: interface "(null)" initialization failed

Any ideas?

Thanks in advance

---

### Post by dando80 on 2007-03-22
It might be easiest to completely remove vlc using "apt-get remove vlc" and then reinstall it. It might even be a good idea to install apt-build and then do "apt-build install vlc"

---

### Post by BiGBeN_87 on 2007-04-11
I get excactly the same output when trying to start vlc from the console and reinstalling it does not work for me.

---

