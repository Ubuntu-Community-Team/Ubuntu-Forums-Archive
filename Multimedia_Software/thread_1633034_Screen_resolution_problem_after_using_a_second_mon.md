---
title: "Screen resolution problem after using a second monitor"
date: 2010-11-28
forum: Multimedia Software
---

### Post by buvesz on 2010-11-28
Hi,

I'm using Ubuntu 10.10. I'm using a 21.5 inch Benq monitor plugged in the DVI port of a video card (MSI ATI Radeon 5450). After installing Ubuntu, I had no issue, the resolution of the screen was good and configured automatically at 1920x1080. Today I plugged another screen in the VGA plug but then decided not to use it. As a result, next time I started the computer, (with the additional screen unplugged), the resolution of my computer was at 1440 x 900. And I can't change it! When I go to Preferences > Monitors, that is the maximum resolution I can choose. When I go to ATI Catalyst Control Center, it's the same thing, in Display Manager, that is the maximum resolution I can use. Yet when I choose "Digital monitor" under Display Manager, it says that the maximum resolution I can use is 1920x1080.

Anyone has any idea what happened ? and why ? and more importantly, how I could fix this ? (and to keep things easier, smoother on my computer and preferences, I would like to fix this without "forcing" my desired resolution with xrandr for example).

Thanks in advance to anyone that has any clue about this.

---

### Post by buvesz on 2010-11-28
Of course, I had to find the solution 5min after posting that message although I had been at it for one or two hours.

Anyway, I was able to fix it using 

```
sudo dpkg-reconfigure xserver-xorg

```

logging out, logging in and then I could choose my desired resolution again

---

### Post by JC Cheloven on 2010-11-28
Hi,
Ubuntu should adjust the correct resolution. But perhaps something is messed up if for example you connected/disconncted the monitor while running. Try this (which is cheap :) ):
Shutdown // Connect external monitor // Boot into ubuntu // Shutdown again // Unplug monitor // Boot again

Hope this solves it.

EDIT: oops: you solved it while I wrote. Congrats.

---

