---
title: "ATI X1700 fglrxinfo assistance please."
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by touchwood on 2007-10-30
I would appreciate some assistance as I have spent most of the day trying to configure the new ATI driver. I have compiled the new fglrx driver from source. But when I do fglrxinfo I get -

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

I have Disabled_modules = "fglrx" but it seems the old driver is still being loaded.

Thanks

---

### Post by Forceflow on 2007-10-30
Well of course ... you want to load the fglrx driver, but you listed it as disabled ...  :)

---

### Post by touchwood on 2007-10-30
Thanks - I know that. I was trying to stop the default driver starting instead of the new ATI driver. Do you know how I can make the ATI driver load instead of the default.

---

