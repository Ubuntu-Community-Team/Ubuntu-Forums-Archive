---
title: "Feisty: XMMS high CPU usage"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by make on 2007-04-23
I just finished moving one computer from openSuSE 10.2 to Ubuntu 7.04 and ran into a problem that SuSE did not have: XMMS is consuming a lot of CPU time. When XMMS is on the CPU utilization is always at minimum 30 %, often even 100 %. Everything else runs really slow.

I could renice XMMS, but that'd probably disturb playing music and cause nasty breaks. The strange thing is that when XMMS doesn't even have a playlist open or play anything, it still uses 30 - 100 % of the CPU. Other programs playing sound and/or video don't have this issue.

Kernel: 2.6.20-15-generic #2 SMP x86_64 GNU
XMMS: 1.2.10 (x86_64) from Feisty repos
Output plugin: ALSA

I was using the same 1.2.10 version on openSuSE with no problems. openSuSE was the 32-bit version, though, now I am running the 64-bit Feisty and XMMS. Switching XMMS away to some other program is out of the question as it has some plugins (SingIt for example) that won't work with Amarok or others. The plugins are not the cause for the high CPU utilization though, I've checked that.

---

