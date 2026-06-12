---
title: "vncserver kills wireless, disappears nm-applet"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by hadenough on 2010-12-22
Anyone seen this? I've just done my first Ubuntu (10.10) installation (no previous Ubuntu/Deb experience, but lots of RedHat).

I set up vncserver (Xvnc4), as I had problems with Remote Desktop and x11vnc. This works really well, apart from one show-stopper: with vncserver running, my laptop no longer shows nm-applet, and I can't connect to a wireless network (eth1). The vnc client connects over a wired cable (eth0), and the client desktop *does* show nm-applet, and it does show the wireless connection.

If I disable the vncserver service, and reboot the laptop, then the laptop does show nm-applet, and I can connect to the network via wireless. It's not an option for me to start vncserver manually only when it's required - it has to start as a service at boot-up.

This has presumably got something to do with the fact that I'm running 2 Gnome sessions (I think; I don't know anything about gnome). My vnc xstartup file is currently running xinitrc and twm. nm-applet seems to know about only one of the desktops.

Any ideas?

Thanks -

Bob

---

### Post by I-love-maverick on 2011-11-07
Did you ever manage to display nm-applet on VNC session that is not running on the main display, :0? I'm also trying to use vncserver on display :1 and nm-applet doesn't show up there, but only on display :0.

---

