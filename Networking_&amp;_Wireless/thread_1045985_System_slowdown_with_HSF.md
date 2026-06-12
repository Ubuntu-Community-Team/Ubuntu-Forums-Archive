---
title: "System slowdown with HSF"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by The Godfather on 2009-01-21
Dear friends

I am experiencing some issues related to a softmodem driver coded by
linuxant ([www.linuxant.com](www.linuxant.com)). I have an ac 97 type soft modem installed
in this laptop I use (acer travelmate 2423wxm).

The installation was fine, I even included an Alsa patch issued by the
linuxant team.

The only problem is that after a bit of time that it runs, all of a
sudden the whole system slows down to a crawl, so much so that I have
to issue a sudo killall pppd command, and then re-connect again.
Sometimes even this is not enough, and I have to issue a sudo
hsfconfig command and re-configure the modem.

The cpu usage then drops down from 100% back to reasonable levels and
normal operation can resume again. However, after a while things slow
down again. For instance right now I am typing this offline, as with
the driver on and active, the cursor would not even be blinking.

I have tried using "sudo top" to get a realtime idea of exactly what
processes are stressing the machine so much when online, and usuall
they are X.org and Firefox, which together take the processor up to
100%. If I issue a "sudo killall pppd", then after a little while,
values get back down to normal.

I have tried different browsers, thinking it was firefox causing this,
but the results are the same.

I am attaching a text file of the same above, plus various system outputs which may help in understanding the problem.

Any ideas out there?

---

