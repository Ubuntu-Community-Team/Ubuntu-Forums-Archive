---
title: "Why i can't install compiz?"
date: 2010-08-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-08-28
When i try to install compiz i get:


compiz:
 Depends: compiz-gnome but is not about to be install or
 	compiz-kde but will not install
 Depends: libcompizconfig0 but is not about to be install.

The pharsing might not be accurate because i am translating it 
back from hebrew but you get the point.

Thanks in advance.

---

### Post by ronacc on 2010-08-28
it means that the dependencies are not available , probably not built yet , try again later .

---

### Post by aviramof on 2010-08-28
And does compiz do the same for everyone here? i even purged compiz ppa and tried the version in the main repositories but no luck.

---

### Post by andrewthomas on 2010-08-29
No problems here 
```

||/ Name                                      Version                                   Description
+++-=================================-===================-==============================================================
ii  compiz                            1:0.8.6-0ubuntu5    OpenGL window and compositing manager
ii  compiz-core                       1:0.8.6-0ubuntu5    OpenGL window and compositing manager
un  compiz-core-abiversion-20091102   <none>              (no description available)
ii  compiz-fusion-plugins-extra       0.8.6-0ubuntu1      Collection of extra plugins from OpenCompositing for Compiz
ii  compiz-fusion-plugins-main        0.8.6-0ubuntu2      Compiz Fusion plugins - main collection
ii  compiz-gnome                      1:0.8.6-0ubuntu5    OpenGL window and compositing manager - GNOME window decorator
un  compiz-gtk                        <none>              (no description available)
un  compiz-kde                        <none>              (no description available)
ii  compiz-plugins                    1:0.8.6-0ubuntu5    OpenGL window and compositing manager - plugins
un  compiz-wrapper                    <none>              (no description available)
ii  compizconfig-backend-gconf        0.8.4-1ubuntu5      Compiz Fusion configuration system - gconf backend
ii  compizconfig-settings-manager     0.8.2-0ubuntu1      Compiz configuration settings manager
ii  libcompizconfig0                  0.8.4-0ubuntu3      Settings library for plugins - OpenCompositing Project
``````
ii  xserver-xorg                                  1:7.5+6+xserver1.9                            the X.Org X server
ii  xserver-xorg-core                             2:1.9.0+git20100821.79ee78de-0ubuntu0sarvatt  Xorg X server - core server
ii  xserver-xorg-video-ati                        1:6.13.99+git20100825.e9928fe0-0ubuntu0sarvat X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-radeon                     1:6.13.99+git20100825.e9928fe0-0ubuntu0sarvat X.Org X server -- AMD/ATI Radeon display driver
```

---

### Post by VinDSL on 2010-08-29
> **aviramof said:**
> And does compiz do the same for everyone here?Working fine here, aviramof...  ;)

10.10 Alpha 3

---

### Post by aviramof on 2010-08-29
Problem solved by purging compiz* and then reinstalling it but with no fglrx compiz still doesn't work properly but thanks for the help.:)

---

