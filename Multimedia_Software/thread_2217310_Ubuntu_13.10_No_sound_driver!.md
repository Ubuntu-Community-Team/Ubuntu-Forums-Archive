---
title: "Ubuntu 13.10 No sound driver!"
date: 2014-04-16
forum: Multimedia Software
---

### Post by ehsan-izadi on 2014-04-16
Hi,

I have sound in my Ubuntu 13.10 (32 bit) but there is no sound icon on the system tray and I it does not recognize any sound driver as well!
But how could it be possible to have sound idk!!

I should note after updating last week, there was a problem with my skype sound, and I performed the commands below and after a few days I got the mentioned problem:

sudo sed -i 's/^Exec=.*/Exec=env PULSE_LATENCY_MSEC=30 skype %U/' /usr/share/applications/skype.desktop

Thanks beforehand
Ehsan

---

