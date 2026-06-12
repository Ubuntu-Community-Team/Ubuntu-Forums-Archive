---
title: "Audio 8 DJ Default Output"
date: 2011-11-11
forum: Multimedia Software
---

### Post by vervas on 2011-11-11
Hello,

I have an Audio 8 DJ usb soundcard with 4 input and 4 output channels. The card functions properly but from the sound settings I can only get an output stream on my first channel. From terminal this command ```
speaker-test -c 2 -D plughw:Audio8DJ,0,3 -t wav
``` gives me the desired output (my fourth channel). How can I set this soundcard and channel to be the defaults? I think it has to do with the ~/.asoundrc file but i cannot figure out its syntax and function.

Thanks

---

