---
title: "'Options' tab missing form gnome-session-properties (aka Startup Applications)"
date: 2011-02-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ubername on 2011-02-08
Hi

Previously I could go:

System > Preferences > Startup Applications, and click on the Options tab, check "Automatically remember running applications when logging out" to save currently running applications.

The 'Options' tab seems to have disappeared. Anyone know how I can achieve the same thing?

I found an option called 'auto-save-session' in gconf-editor at /schemas/apps/gnome-session/options but this has the value <schema> and when I try to change it I get

> Currently pairs and schemas can't be edited. This will be changed in a later version.


Thanks for any help.

---

### Post by mc4man on 2011-02-08
from the changelogs of gnome-session

> gnome-session (2.32.1-0ubuntu11) natty; urgency=low

  * debian/patches/02_add_ubuntu_session.patch:
    - fix some typos.
  * debian/patches/03_no_required_component_saved_in_main_session.patch
    (removed)
    debian/patches/10_session_save.patch (removed)
    debian/patches/06_nuke_session_saving.patch: (added)
    [COLOR="RoyalBlue"]- remove saved session handling: it's broken right now with multiple
      sessions and should get a proper upstream refactoring (discussions still
      ongoing)[/COLOR]
    - [COLOR="Blue"]remove the option in the gnome-session-properties as well[/COLOR]

 -- Didier Roche <didrocks@ubuntu.com>  Sun, 16 Jan 2011 12:42:48 +0100

---

### Post by SnappyU on 2011-03-28
*ouch* ... this was such a time-saver feature of gnome / ubuntu!  And I thought my system was broken!

---

