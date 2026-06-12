---
title: "mythbuntu control center (deamon crashed)"
date: 2009-11-05
forum: Mythbuntu
---

### Post by revival67 on 2009-11-05
Maybe somebody can help 

I can't manage to change something in the mythbuntu control centre using Kubuntu 9.10

After hitting the Apply button i get the next message > Task cannot be monitored or controlled

The connection to the daemon was lost. Most likely the background daemon crashed.

The terminal gives me
> 2009-11-05 10:13:22,679 DEBUG: debconf socket: /tmp/aptdaemon-7_TiSN/debconf.socket
2009-11-05 10:13:22,679 DEBUG: debconf.start()
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 218, in summaryApply
    self.commit(self.install, self.remove, self.request_unauth_install)
  File "/usr/bin/mythbuntu-control-centre", line 276, in commit
    apt_dialog.set_icon(icon = theme.load_icon("update-manager", 16, 0))
glib.GError: Icon 'update-manager' not present in theme
2009-11-05 10:13:55,045 DEBUG: debconf.stop()
/usr/lib/python2.6/dist-packages/aptdaemon/gtkwidgets.py:586: DeprecationWarning: use set_markup() instead
  box = self.label.get_parent()


Greets Revival67

---

### Post by superm1 on 2009-11-05
Well the tool wasn't tested on Kubuntu, so there is definitely room for breakage.

What exactly are you trying to change?  Do you actually have update manager installed right now?  Is it not use on Kubuntu?

---

### Post by revival67 on 2009-11-05
Thank you very much Superm1.

The problem was that update-manager and libgnome2-perl wasn't installed.

Revival67

---

