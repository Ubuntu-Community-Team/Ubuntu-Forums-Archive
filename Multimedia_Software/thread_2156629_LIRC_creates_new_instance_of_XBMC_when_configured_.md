---
title: "LIRC creates new instance of XBMC when configured to run from MCE remote"
date: 2013-06-22
forum: Multimedia Software
---

### Post by andyking on 2013-06-22
I am trying to setup a MCE remote to launch xbmc with the green button.

I've done this successfully by setting irexec to run as a daemon on start up and configured the .lirc file to launch the xbmc executable when pressed.

However, if I'm in XBMC and press the green button again then it opens another instance xbmc. Is there anyway to set lirc to check if there's an existing instance already running and switch to that? Or failing that is there anyway to disable irexec when xbmc is launched and then renable on closing?

---

