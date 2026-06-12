---
title: "How can I close VLC media player?"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by jis on 2006-09-07
It got stuck while playing a CD.

---

### Post by haiku99 on 2006-09-07
try closing the desktop, ctrl-alt-backspace

---

### Post by Anonii on 2006-09-07
"ALT+F2" and execute the xkill program, then click the VLC window. That is if you can use your desktop.

For more info check this thread:
[http://ubuntuforums.org/showthread.php?t=248646](http://ubuntuforums.org/showthread.php?t=248646)

---

### Post by jis on 2006-09-07
Thanks, Anonii. I wasn't careful enough with xkill as I clicked the VLC program in the bar located on bottom of display. I lost the bar and menus :( Any idea how to get them back?

---

### Post by Anonii on 2006-09-07
Heh, that was a mistake. 
You can try restarting metacity which is GNOME's window manager, but I'm not really sure it will work.
Try: "killall metacity"
if that doesnt work use "ctrl+alt+delete" to kill X, and start your GNOME session again.

---

### Post by jis on 2006-09-07
There is no metacity installed, at least the killall command you gave didn't kill it. I can still get into the application menu by right-clicking the desktop.

---

### Post by Anonii on 2006-09-07
Which UI are you using? KDE/GNOME or what?
Try "CTRL+ALT+Delete" except if you have something important running right now.

---

### Post by jis on 2006-09-07
The UI is Xfce. I got my desktop bars back by doing the following in the given order:
1) Select "Quit" in the Application menu
2) Uncheck "Save sessions for future logins" (not sure if this is needed)
3) Select "Log out". 
4) Log in again.

---

### Post by Anonii on 2006-09-07
> **jis said:**
> The UI is Xfce. I got my desktop bars back by doing the following in the given order:
1) Select "Quit" in the Application menu
2) Uncheck "Save sessions for future logins" (not sure if this is needed)
3) Select "Log out". 
4) Log in again.
How lame , am I? I didnt see that you were using Xubuntu from your profile >:

Anyway, I'm glad you fixed it. Also, try checking the thread I gave you, it has some other methods on how to kill programs that dont behave correctly :]

---

