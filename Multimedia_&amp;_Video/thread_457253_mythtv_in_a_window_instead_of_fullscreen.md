---
title: "mythtv in a window instead of fullscreen"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by jba6511 on 2007-05-28
Is it possible to set mythtv to run in a window instead of in fullscreen? I would like it to be in a resizbable window that can sit on my desktop while I watch so that I can perform other tasks as well. Played around with some of the settings but ended up messing up mythtv, and doing a reinstall. Thought I would ask first this time.

---

### Post by newlinux on 2007-05-28
Yes, depending on which theme you are using:

Utilities/setup->Setup->Appearance

On the second screen check box to run Mythfrontend in a window

[http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#Screen_settings](http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#Screen_settings)

---

### Post by JEDIDIAH on 2008-06-27
> **newlinux said:**
> Yes, depending on which theme you are using:

Utilities/setup->Setup->Appearance

On the second screen check box to run Mythfrontend in a window

[http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#Screen_settings](http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#Screen_settings)

This method will also work and doesn't require any configuration from within MythTV. I use this with my toolbar icon (launcher).

mythfrontend -w -geometry 1280x720

---

