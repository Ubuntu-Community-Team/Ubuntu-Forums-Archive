---
title: "Networking disabled for some reason?!"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by edanto on 2010-09-13
Hi all,

I've had a persistent problem with the network manager disappearing from the top menu bar, and had gotten into the habit of running 'nm-applet' from a terminal to get it running again.

The last time I tried to do this - the network manager just says 'networking disabled'

In the terminal it says...


nm-eoin@eoin-laptop:~$ nm-applet

(nm-applet:2950): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(nm-applet:2950): atk-bridge-WARNING **: IOR not set.

(nm-applet:2950): atk-bridge-WARNING **: Could not locate registry
** (nm-applet:2950): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2950): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2950): DEBUG: foo_client_state_changed_cb
** (nm-applet:2950): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:2950): DEBUG: going for offline with icon: notification-network-disconnected

any ideas, please?

---

### Post by edanto on 2010-09-16
bump?

---

### Post by Iowan on 2010-09-16
A couple of threads to check:
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")

---

### Post by edanto on 2010-09-17
Thanks, that linked really helped and my problem seems to be fixed now.

---

### Post by drorata on 2010-10-04
Solved issue for me!

---

