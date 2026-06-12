---
title: "Installed xubuntu, and now I can't VNC into machine?"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by CptanPanic on 2011-05-21
I have 11.04, and installed xubuntu desktop, but now I can't vnc into this machine, I get connection denied.  I was able to before with the default desktop.  What do I need to do?
Thanks,
CP

---

### Post by Toz on 2011-05-21
> **CptanPanic said:**
> I have 11.04, and installed xubuntu desktop, but now I can't vnc into this machine, I get connection denied.  I was able to before with the default desktop.  What do I need to do?
Thanks,
CP

Is vncserver running on the machine?```
ps -ef | grep -i vncserver
```
Is there a firewall blocking the connection?```
sudo ufw status
```

---

### Post by gradinaruvasile on 2011-05-21
> **CptanPanic said:**
> I have 11.04, and installed xubuntu desktop, but now I can't vnc into this machine, I get connection denied.  I was able to before with the default desktop.  What do I need to do?
Thanks,
CP

Default desktop = Gnome Desktop. Gnome has a built-in vnc server (vino-server) that can be activated with a single click. Xubuntu, that is based on Xcfe Desktop Environment does not have it.

So, you should install a vnc server and put it in the autostart. x11vnc is a very good one.

---

### Post by CptanPanic on 2011-05-21
> **gradinaruvasile said:**
> Default desktop = Gnome Desktop. Gnome has a built-in vnc server (vino-server) that can be activated with a single click. Xubuntu, that is based on Xcfe Desktop Environment does not have it.

So, you should install a vnc server and put it in the autostart. x11vnc is a very good one.

Thanks, I didn't realize this.

---

