---
title: "K3b - Unable to fixate disc"
date: 2012-02-16
forum: Multimedia Software
---

### Post by Rtedmonston on 2012-02-16
Seems this is an old problem that k3b has had for a long time. Been burning discs fine up until yesterday after update, started getting "error: Unable to fixate disc. The disc may still be readable though." At first it was complaining about cdrecord didn't have permission to write, but that portion of the error message is gone now after I changed permissions under k3bsetup. 

I tried running as root user and this is what I get in terminal: 

[quote=acer@aspire]russell@russell-Aspire-7740:~$ sudo k3b 
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
Error: "/var/tmp/kdecache-russell" is owned by uid 1000 instead of uid 0.
russell@russell-Aspire-7740:~$ Error: "/tmp/kde-russell" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-russell" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-russell" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-russell" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-russell" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-russell" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-russell" is owned by uid 1000 instead of uid 0.
kbuildsycoca4(3688) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(3688) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(3688) kdemain: Emitting notifyDatabaseChanged ()
Error: "/var/tmp/kdecache-russell" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-russell" is owned by uid 1000 instead of uid 0.
k3b(3657)/kdeui (kdelibs): Attempt to use QAction "view_projects" with KXMLGUIFactory! 
k3b(3657)/kdeui (kdelibs): Attempt to use QAction "view_dir_tree" with KXMLGUIFactory! 
k3b(3657)/kdeui (kdelibs): Attempt to use QAction "view_contents" with KXMLGUIFactory! 
k3b(3657)/kdeui (kdelibs): Attempt to use QAction "location_bar" with KXMLGUIFactory! 
Error: "/tmp/ksocket-russell" is owned by uid 1000 instead of uid 0.
QLayout: Attempting to add QLayout "" to QFrame "", which already has a layout
K3bQProcess::QProcess(0x0)
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/russell/.gvfs
      Output information may be incomplete.
Error: "/var/tmp/kdecache-russell" is owned by uid 1000 instead of uid 0.[/quote]

I've googled this to death and can't find any solution. What's going on? Under Ubuntu 11.10, using Philips DVD-R 4.7GB discs, haven't had any problems until now.

---

### Post by Rtedmonston on 2012-02-16
Any ideas?

---

### Post by Rtedmonston on 2012-02-18
bump for other people having this same issue:

[http://ubuntuforums.org/showthread.php?t=1926359](http://ubuntuforums.org/showthread.php?t=1926359)

---

### Post by Rtedmonston on 2012-02-19
bump

---

### Post by Ghostnik11 on 2012-06-21
did u ever figure out a way to solve this because i am having the same problems

---

