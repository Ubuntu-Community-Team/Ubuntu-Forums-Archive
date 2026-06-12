---
title: "Poor video quality while in XGL"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by oranges2 on 2007-01-16
I've only been using linux for a few days now, so I'm not all that adept in the subject.

While playing Xvid encoded AVIs, the video quality is deteriorated and there is a translucent green bar near the top of the video. This only happens while in an XGL session (Regardless of whether Beryl is being used as the window manager). VLC Player and MPlayer both give me the same results.

I have an ATI Xpress 200m card and followed these instructions to install the drivers and beryl:

[http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)

Video quality is fine while I'm in a Gnome session.

Finally got sound working though :D If I can get this and wireless working I'll be pretty happy.

And if theres any way I can disable the Shift + Backspace to logout hotkey, that would be great. :D

EDIT: On Ubuntu Edgy i386

---

### Post by fjellREV1 on 2007-01-16
In order to disable shift + backspace = log out, run this command but remember to add it to a start up script. If you use thefuture script for xgl add it to the end. **** + backspace is a XGL only so  NO need to use the command if in Gnome/KDE

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server" 


The poor video quality I dont know about. I allways turn off beryl/emerald if I watch movies.

---

### Post by oranges2 on 2007-01-16
It works

How would I go about adding it to startup?

(Maybe I should have posted in absolute beginner talk >_>)

---

### Post by oranges2 on 2007-01-17
Bump

---

### Post by nphx on 2007-06-25
VLC > Settings > Preferences > click Advanced options > Video > Output modules > Select alternative from Default, try out some other modules and see which one works best. Remember to click on Save after making changes.

---

