---
title: "Distinct Headphone Slider/Control in ALSA"
date: 2008-12-01
forum: Multimedia Software
---

### Post by Sören on 2008-12-01
Hello dear fellows,

In the alsamixer of my system there are present a PCM as well as a MASTER slider. Notably, there appears to be no seperate slider for my headphone as it only gets switched on after an actual headphone got plugged.

This usual behaviour is all fine and dandy, however, the issue I was wondering about is whether it is a limitation of simply my sound card, that there just can't be two sliders for headphone and speakers seperatly, or if I may carry out a reconfiguration of ALSA in such a way that I obtain two distinct controls through ALSA.

My main purpose is that, when I unplug my headphones, my speakers do not produce any sound immediately except for when I have explicitly allowed this through the control in the alsamixer.

Due to the entry in proc my sound card appears to be the following:

```

 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfebfc000 irq 1

```

Thanks very dearly for any response!

---

