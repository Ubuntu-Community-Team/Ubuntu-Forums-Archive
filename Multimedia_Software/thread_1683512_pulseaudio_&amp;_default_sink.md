---
title: "pulseaudio &amp; default sink"
date: 2011-02-07
forum: Multimedia Software
---

### Post by rog-denis on 2011-02-07
Hello.

I can't set default sink in pulseaudio. I've tried to find a solution here or using google, but without any success.

Setting default sink with pacmd doesn't take any effect: 'pactl stat' shows the setted sink as default but sound always comes from the sink #0
At the same time if I start padevchooser an set default sink with 'Default Sink' -> 'Other' -> 'sinkname' sound comes from 'sinkname' but 'pactl stat' shows sink #0 to be default

I'm using 10.10

Any suggestions?

Thank's

---

