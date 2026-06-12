---
title: "Could not launch 'Desktop recorder'"
date: 2013-06-23
forum: Multimedia Software
---

### Post by VanillaMozilla on 2013-06-23
I can't start RecordMyDesktop.  The error message is:

"Could not launch 'Desktop recorder'
Failed to execute child process "gtk-recordMyDesktop" (No such file or directory)"

The Applications menu entry (in Gnome fallback mode, Precise) has an entry with the command gtk-recordMyDesktop, which gives that error message.  A terminal command '/usr/bin/gtk-recordMyDesktop' gives the message "No such file or directory".  There is a Python script /usr/bin/gtk-recordMyDesktop on the computer.  I just uninstalled and reinstalled this program with the Ubuntu Software Center.

What's wrong?  Why can't I get this program to work?  It has worked in the past.

---

### Post by mc4man on 2013-06-23
> **VanillaMozilla said:**
> I can't start RecordMyDesktop.  The error message is:

"Could not launch 'Desktop recorder'
Failed to execute child process "gtk-recordMyDesktop" (No such file or directory)"

The Applications menu entry (in Gnome fallback mode, Precise) has an entry with the command gtk-recordMyDesktop, which gives that error message.  A terminal command '/usr/bin/gtk-recordMyDesktop' gives the message "No such file or directory".  There is a Python script /usr/bin/gtk-recordMyDesktop on the computer.  I just uninstalled and reinstalled this program with the Ubuntu Software Center.

What's wrong?  Why can't I get this program to work?  It has worked in the past.
here the name is gtk-recordmydesktop

```
$ ls /usr/bin |grep recordmy
gtk-recordmydesktop
recordmydesktop

$ file /usr/bin/gtk-recordmydesktop
/usr/bin/gtk-recordmydesktop: a /usr/bin/python script, ASCII text executable

```

---

### Post by VanillaMozilla on 2013-06-23
That was ridiculously simple.  Thanks.  The computer is littered with both spellings, and I didn't notice the misspelled command.

---

