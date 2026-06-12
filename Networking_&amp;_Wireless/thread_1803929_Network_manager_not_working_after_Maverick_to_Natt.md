---
title: "Network manager not working after Maverick to Natty"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by violetdream on 2011-07-14
I just did a dist upgrade on two computers. One of them was fine with the network manager, but the other,  netbook, now refuses to start the service. If I do service start network-manager I'll get a message saying a process started, but it must be immediately dying since I can't find the pid or any network manager processes at all. I looked at daemon.log and noticed it was complaining about nm-system-settings.cfg not being there. One question I have is how is this not getting generated? It's not in the deb so somehow it must be generated. I put a fake file in there and even put some data from a pastebin I found online that looked promising, and the message in daemon.log went away but the pids were still dropping off.

I have many problems with nm-applet, but I don't want to go into it so much now that the service can't start. The problem I do see popping up is something like:

 ** (nm-applet:2622): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service.   Message: 'Connection ":1.24" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file'

(had to pull message from online, don't remember the exact message)

I've tried installing and reinstalling, doing a purge uninstall. Next thing I was going to try is an aptitude uninstall of all of the dependencies in case something got weird in the upgrade. Any thoughts? I am using a custom rolled distro so some of the suggestions don't apply to me, I don't have the same shell etc, but all command line stuff should be good.

---

### Post by violetdream on 2011-07-14
If I can offer any additional information please let me know. I would not be so insistent about this topic but I am going into the hospital shortly and need a working netbook.

---

