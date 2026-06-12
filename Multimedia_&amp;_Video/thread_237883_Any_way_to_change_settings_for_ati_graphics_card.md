---
title: "Any way to change settings for ati graphics card?"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by WalmartSniperLX on 2006-08-16
I have a ati card on the fglrx 8.27.10 driver and im wondering if theres any way to change any settings or if theres even a way to change settings. :D (like the control panel in windows)

---

### Post by isharra on 2006-08-17
The package installation should have given you a control panel that allows you to change some of the settings (it's under the Applications, Accessories in Ubuntu - not sure of the location in Kubuntu or Xubuntu).

You can configure all of the settings in the /etc/X11/xorg.conf file. The 'aticonfig' program can edit that file for you with many options. Type 'aticonfig --help' in a terminal to see the options.

---

### Post by mordi on 2006-08-17
or you can break your xserver yourself, instead of some other application, by editing /etc/X11/xorg.conf. you can even play it safe and back up xorg.conf before editing it.

---

