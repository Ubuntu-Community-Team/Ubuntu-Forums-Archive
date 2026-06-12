---
title: "Tried multiple sound fixes but still no luck. Help would be appreciated."
date: 2012-06-20
forum: Multimedia Software
---

### Post by jm2567 on 2012-06-20
Hi I've just installed Ubuntu 12.04 but I'm having trouble getting my onboard sound card recognised (rather old: Realtek ALC655). I've tried purging ALSA and Pulseaudio and then reinstalling but I'm having no luck. The report says that no sound card is detected. The thing is, I used Ubuntu on this machine years ago and seem to remember having sound. Any ideas welcome. I've put the report at the bottom. Thanks guys.


[http://www.alsa-project.org/db/?f=138fa64590b45782b40697f4a5859e46929e6bd1](http://www.alsa-project.org/db/?f=138fa64590b45782b40697f4a5859e46929e6bd1)

---

### Post by jm2567 on 2012-06-21
Any help?

---

### Post by BicyclerBoy on 2012-06-21
The alsa script should have reported the alsa driver version..
That seems to be missing/be the problem because the kernel driver should not be missing in a normal ubuntu kernel build.

I would suggest re-installing the alsa packages.

Could try booting a previous kernel (from grub) if you can...

---

