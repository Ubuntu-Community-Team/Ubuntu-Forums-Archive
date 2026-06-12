---
title: "Theme problem - simple (ugly) theme shown after boot"
date: 2011-01-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-26
I am experiencing this bug more and more frequently these days.
This is the bug #649809
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809/+index?comments=all)

After an unsuccessfull boot (ugly theme appears) you will find these warnings in the file .xsession-errors:

```
** (gnome-settings-daemon:1641): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:1641): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
```

and then selecting a theme only changes the titlebar, not icons nor window content.

Do you see this too?
It has been said this happens commonly on fast hardware and setups, like on SSD systems and powerfull processors. Also it seems to affect more systems with a fast NVidia graphics card with binary drivers (nvidia-current).
And yes, in Ubuntu.

There is a good workaround:
Change the following line in the file /etc/xdg/autostart/gnome-settings-daemon:
```
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
```
to this:
```

Exec=bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

```

---

### Post by Harry33 on 2011-02-08
There is now an explanation to this bug #649809.

Sebastian Bacher wrote:
"Thank you for commenting on this bug, there is no need to new comments to confirm or describe the issue though, what is happening is a race between the login settings manager and the session one on modern configurations, now what needs to be done is fro someone writting a fix to make sure the login settings daemon exists before the session on starts"

Waiting for the fix.

---

