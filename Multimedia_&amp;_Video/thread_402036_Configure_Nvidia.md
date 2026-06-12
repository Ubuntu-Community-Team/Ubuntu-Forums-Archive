---
title: "Configure Nvidia"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by Du_rodrigues on 2007-04-05
Good Morning, I have an equipment HP D325 that has a Nvidia plate and installed in this equipment Ubuntu 6,06, I executed the following way to install driver:
# apt-get install nvidia-glx nvidia-kernel-common
# nvidia-xconfig

Make Backup of file:
# cp -p /etc/X11/xorg.con /xorg.con

edit file and replace "nv" for "nvidia"
# vi /etc/X11/xorg.conf

Restart  X, and a machine it accuses error:
There was an error starting the GNOME Settings Daemon.
Some Things, such as themes, sounds, or background settings
may not work correcty.
The last erro message was:
The name org.gnome.SettingsDaemon was not provied by
any .service files
GNOME will still try restart the Settings Daemon next time
you log in.

somebody can help me to take off this error?
Tanks

---

