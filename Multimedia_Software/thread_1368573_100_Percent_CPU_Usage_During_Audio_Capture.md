---
title: "100 Percent CPU Usage During Audio Capture"
date: 2009-12-30
forum: Multimedia Software
---

### Post by adampaetznick on 2009-12-30
The following command induces a cpu workload of 100%.
*'arecord foo.wav'*

In this case, arecord and pulseaudio processes combine to consume all free cpu cycles.  Sometimes, arecord must be killed via 'kill -9'.  The audio captured with arecord can be played back without incident and with only moderate cpu usage.

Also concerning is that simply opening the gnome sound preferences window also induces a cpu workload of 100%.  

For both arecord and gnome-sound-preferences, there are repeated messages in /var/log/messages of the following form:
*pulseaudio[PID]: ratelimit.c: XXX events suppressed*

Anyone else have similar issues or suggestions for debugging?

My system is:
Lenovo IdeaPad S12 (VIA Nano)

amixer info
Card default 'VT82xx'/'HDA VIA VT82xx at 0xf5500000 irq 17'
  Mixer name    : 'Realtek ALC269'
  Components    : 'HDA:10ec0269,17aa6002,00100004'
  Controls      : 17
  Simple ctrls  : 11

If it helps to have any additional info, let me know and I'll be happy to provide it.

---

