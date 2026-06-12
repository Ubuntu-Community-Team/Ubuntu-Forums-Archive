---
title: "Sound through network usign ESD"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by infinito on 2007-05-22
Hi!

I have to computers connected via ethernet, ind i want to hear what computer1 is playing on computer2 speakers.

If I do killall esd; esd -tcp -public on second computer and set the ESPEAKER env var in first computer it works fine. But i want ESD to listen for tcp connections automatically.

I've added above options to esd.conf, but it doesn't work. I must kill esd and restart it again passing the commandline options to get it work.

This is my /etc/esound/esd.conf
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-tcp -public
```

Any idea how can i fix this?
Thanks in advance!

---

