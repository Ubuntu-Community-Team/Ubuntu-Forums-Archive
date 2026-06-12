---
title: "Videos - Open with &quot;VLC Media Player&quot; or &quot;vlc&quot;"
date: 2008-10-16
forum: Multimedia Software
---

### Post by fermulator on 2008-10-16
Good day!

I have a problem with, I suppose nautilus(?)'s way of playing videos using VLC doesn't work (sometimes).

_Scenario 1 - Right click, open with "VLC Media Player"_
 - Not all videos play.  Sometimes we receive the following error:
> **Errors**
The following errors occured.  More details might be available in the Messages window.
Unable to open 'file://thefile'

_Scenario 2 - Right click, open with "vlc"_
 - All video play, always.  No problems.


What is the difference between playing with the raw "vlc" command, and Ubuntu's built in "VLC Media Player" file association?  ... and, ultimately, how can we fix the "VLC Media Player" default Ubuntu configuration to work properly?

---

### Post by Mattie03 on 2008-10-16
Maybe the file isn't compatible with VLC or the video file is corrupted. Have you tried opening it with other players?

---

### Post by mc4man on 2008-10-16
open with "VLC Media Player" opens vlc from the default vlc.desktop. "open with vlc" opens vlc from a created userapp-vlc-XXXXXX.desktop which unless specified will use a launch command of vlc %f (EXEC=)

The user app .desktop was created by going at some point r. click -> open with -> open with other application.

You can find this (and other ) .desktops in home folder -> .local/share/applications. (ones with blue diamonds are userapp .desktops, ones with icons are either the default or custom created .desktops. The listings showing names and if applicable the default (first listed) would be in mimeapps.list (in above folder

Note: the only way to read whats inside a .desktop is to open with a text editor. Doing this from the terminal can be a little tricky with the userapp .desktops due to needing the exact name (including XXXXXX

What's easier is to install nautilus actions and create a right click 'open with text editor" action.

In any event try going right click on Applications -> edit menus. Highlight sound & video and right click on vlc -> properties. If the command is vlc %U then change it to vlc %f  (%U is a terrible launch command for vlc, you'll find %f much better.

screen - ex. of how that folder can grow

---

