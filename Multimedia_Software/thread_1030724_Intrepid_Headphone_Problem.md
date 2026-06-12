---
title: "Intrepid Headphone Problem"
date: 2009-01-04
forum: Multimedia Software
---

### Post by atngplusultra on 2009-01-04
So.
on 8.10, I cannot get my computer to recognize my headphones. Fortunately, this means that plugging them in doesn't mute my speakers. Still, I want to get these things working.

I'm running Intrepid on a Toshiba laptop that gave me sound troubles on Hardy, so, I ***have*** tried all the old methods for fixing the problem. It seems to be more of a pulseaudio issue.

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Any vague suggestions would be great. Except, I've gone through psyke83's long tutorial, and probably whatever else there is. So, this is a completely new problem, I think.

---

### Post by IQRules on 2009-01-04
Is it just add this to /etc/modprobe.d/alsa-base or options,

something like "options snd_hda... **[COLOR="Red"]model=laptop[/COLOR]**"

---

### Post by atngplusultra on 2009-01-04
> **IQRules said:**
> 
something like "options snd_hda... **[COLOR="Red"]model=laptop[/COLOR]**"

I actually hadn't tried "laptop" at all. I'd done "lenovo" and that was fruitless in the past.

I just tried "laptop," though, and no luck there either.

I think I'll just have to deal with it until Jaunty and see if it's taken care of with that kernel.

---

### Post by IQRules on 2009-01-05
Is it Lenovo 3000 N100?

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100)

---

### Post by atngplusultra on 2009-01-06
nope, the "laptop-eapd" clause also did nothing.

---

### Post by IQRules on 2009-01-06
Try this, [http://ubuntuforums.org/archive/index.php/t-823552.html](http://ubuntuforums.org/archive/index.php/t-823552.html)

---

### Post by atngplusultra on 2009-01-07
Thanks! ending "model=" with either "auto" or "3stack" did end up working, and I'd read that 3stack wouldn't work. Ha.

Although, like in that thread, I cannot control my headphones separately from my speakers; i.e., I can't mute the speakers without also muting the headphones. But, I'll settle with this for the time being.

I also added the "position-fix=1" to the line in alsa-base, but that hasn't seemed to change things.

---

