---
title: "Acer 4520 sound issue"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by marslert on 2008-02-17
I have made the sound worked by following step,

> Added the following line in /etc/modprobe.d/alsa-base :
options snd-hda-intel model=acer
- Added the following line to /etc/modules
snd-hda-intel
- compiled alsa-driver from source (when doing this step, it is important to run "configure step" using "./configure --with-cards=hda-intel".
- compiled alsa-lib from source
- compiled alsa-utils from source

However, all the sound volume that I adjust (let say I set to no sound). The sound will revert back to maximum level at my next reboot.

Any idea on the setting need to take?

---

### Post by marslert on 2008-02-18
Hi,

Anybody can help me on first post question?

Here my 2nd question,

- My screen color will revert to dark color during startup screen. But, it will back to normal color after I login to system. How to get rid on this?

Kindly help.

---

