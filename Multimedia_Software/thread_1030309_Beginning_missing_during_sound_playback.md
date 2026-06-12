---
title: "Beginning missing during sound playback"
date: 2009-01-04
forum: Multimedia Software
---

### Post by DjNDB on 2009-01-04
Hi. 
I have an annoying problem. Whenever audio is played back via optical output the first 2 Seconds are missing. It works fine under Windows or via Analog output.
It seems like the sound device is initialized for a while every time and then shut down.

How can i get my optical output working properly?

- I am using the onboard sound of my GigaByte GA-MA78GM-S2H
- Ubuntu 8.10
- Advanced Linux Sound Architecture Driver Version 1.0.18a

---

### Post by DjNDB on 2009-01-18
I just found the solution. It was caused by a pulseaudio module. I just had to comment it out in 

/etc/pulse/default.pa

```
### Automatically suspend sinks/sources that become idle for too long
#load-module module-suspend-on-idle
```

---

### Post by mackerman on 2009-06-04
I have the same motherboard and using the optical audio out on Ubuntu 9.04.  I cannot get any audio out of the device.

Could you please provide me with some resources for fixing this issue?

Thanks!

---

