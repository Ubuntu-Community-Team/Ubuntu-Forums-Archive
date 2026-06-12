---
title: "How do I stop wicd from starting at boot time?"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by wonko on 2011-01-05
I've tried sudo update-rc.d -f wicd remove and there are no entries for wicd in /etc/init/. I'm running Kubuntu 10.10. I can not find wicd in the KDE service manager or Autostart either.

---

### Post by chrisx on 2011-01-05
Can you find a menu entry related to sessions or startup applications?
I think the window manager is starting it, but I don't have KDE to reference exactly where the session or start-up settings are given.

---

### Post by PatchesTheCaveman on 2011-01-05
There should be an initscript for *wicd-daemon*.

However, to stop the client/icon portion from starting, delete the related .desktop file from your */usr/share/autostart* directory.

That's where autostart scripts shared by GNOME and KDE are stored.  There are also specific ones for each desktop environment and per-user ones.

---

### Post by wonko on 2011-01-14
@chrisx: All I can find in the K-menu is the control center with the services and autostart settings which I've already searched in vain.

@patches: The contents of my /usr/share/autostart dir is kaddressbookmigrator.desktop, kmix_autostart.desktop, krunner.desktop, plasma-desktop.desktop, restore_kmix_volumes.desktop, klipper.desktop, korgac.desktop, nepomukserver.desktop and printer-applet.desktop - I don't think any of these start wicd. My ~/.kde/Autostart folder is empty. I also found some folders named /etc/network/if-up.d/ and /etc/network/if-pre-up.d/ but none of these contained anything named wicd...

Is there anywhere else I can search for startup scripts?

---

### Post by PatchesTheCaveman on 2011-01-14
They moved it since the last time I used it.  (I haven't used wicd since Jaunty.)  It is now in /etc/xdg/autostart

---

### Post by wonko on 2011-01-18
Thank you Patches! I finally found it :)

---

