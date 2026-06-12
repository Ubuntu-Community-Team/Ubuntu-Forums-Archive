---
title: "Switiching from ATI to Nvidia"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by rimbaud on 2007-04-01
Hello

I bought a machine second-hand and installed edgy, but could never get the ATI card to work properly.  Eventually I gave up and bought an Nvidia 6200 card, which does 3D acceleration fine with the proprietary driver, but I can't get the direct rendering to work.  I think the problem might be that there is still ATI stuff on the system, even though I have looked just about everywhere.

glxinfo | egrep "glx (vendor|version)"

indicates GLX 1.4 Nvidia for server but GLX 1.3 ATI for the client

Is there anyway I can convince the system to update the client GLX to be nvidia and the latest version?


By the way, I don't want to come across as an INTEL fanboy, but I have an integrated chipset on my laptop and everything works perfectly: beryl, wi-fi the lot (well except hibernation).

Thanks

Jon

---

