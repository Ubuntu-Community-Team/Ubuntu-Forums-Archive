---
title: "Wireless Icon Disappeared - how to reinstall network config tool"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by JTech 452 on 2012-05-17
I was recently trying to swap the default gnome bluetooth manager for blue man, and so I uninstalled the gnome bluetooth manager to force the transition.

After that, my wireless button disappeared from the panel. I have tried adding the "notification area" applet to the panel again, but it does not include the wireless icon.

I might just reinstall the OS anyway, but if someone knows how to fix this, that would be great.

Thanks

---

### Post by praseodym on 2012-05-17
Try from terminal (CTRL+ALT+T)

> nm-applet

---

### Post by JTech 452 on 2012-05-17
Thanks! 

turns out I somehow uninstalled the gnome network manager tool.

When I went to run the command, it told me where the package could be found. I connected to ethernet, ran 

> sudo apt-get install network-manager-gnome 

It automatically put the applet back into the startup list, and all was well.

Thanks again, you're a lifesaver!

---

