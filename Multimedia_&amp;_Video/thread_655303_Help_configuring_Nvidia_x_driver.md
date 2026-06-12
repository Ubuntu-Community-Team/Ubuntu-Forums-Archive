---
title: "Help configuring Nvidia x driver"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by ray17374 on 2008-01-01
I finally got my Nvidia 6200 graphics card to be recognized by gutsy gibbon. However it seems when i click on nvidia x server settings I get an error stating" you do not appear to be using the nvidia x driver. Please edit your x configuration file(just run "nvidia-xconfig' as root and restart the x server).

Can any one give me instructions on how to do this?

Thank you.

---

### Post by taurus on 2008-01-01
Have you installed nvidia driver from System -> Administration -> Restricted Drivers Manager?  After you click to install it, you have to reboot and it should now using nvidia driver for your graphic card.

Look in /etc/X11/xorg.conf to see which Driver you are currently using.

```
cat /etc/X11/xorg.conf
```

---

### Post by ray17374 on 2008-01-01
Thank you, that worked and now the card is working properly.

---

