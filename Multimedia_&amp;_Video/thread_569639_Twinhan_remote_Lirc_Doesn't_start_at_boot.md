---
title: "Twinhan remote Lirc: Doesn't start at boot"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by cebe11 on 2007-10-07
I have no problem setting up LIRC to understand signals ans control Mythtv and map the keys. 
  However, the only way I can get it to start is to issue this command in a terminal:

Sudo Lirc -H dev/input -d /input/dev/irremote

( I successfully mapped my /input/dve/event2 -->irremote using UDEV rules)

However, I can get to start automatically.

I've tried to create a /etc/init.d/lirc file:

!#bin/bash
Sudo Lirc -H dev/input -d /input/dev/irremote

And then update-rc.d lirc defaults to link it into the boot process but no luck.

The original file in /etc/init.d doesnt seem to do anyting for me?

Suggestions?  I know I'm missing something simple.

Thanks

---

