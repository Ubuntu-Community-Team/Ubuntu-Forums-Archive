---
title: "Envy"
date: 2008-07-01
forum: Multimedia Software
---

### Post by daitheflu08 on 2008-07-01
Okay somehow my envy installation has become completely fouled up.

When I run envy this is the message I get:

envyng-gtk
/usr/bin/envyng: line 11: cd: /usr/share/envy: No such file or directory
Traceback (most recent call last):
  File "/usr/share/envyng-gtk/envynggtk.py", line 7, in <module>
    from Envy import objects
ImportError: No module named Envy

After receiving this message I proceeded with the instructions on envy's website to remove it.  Hence I deleted the main folder but my computer still thinks it's fully installed.  And therefore, I can't reinstall it or remove it.

How can I uninstall envy completely so that I can reinstall it.

:(

---

### Post by daitheflu08 on 2008-07-02
I'm sorry that was the wrong copy and paste try this one:
root@daniel-desktop:/home/daniel# envyng
ERROR: you need to provide a parameter:
   "-t" for the textual interface
   "-g" for the GTK frontend
   "-k" for the QT4 frontend
   "--uninstall-all" to completely remove what EnvyNG has done

root@daniel-desktop:/home/daniel# sudo envyng -t
/usr/bin/envyng: line 6: cd: /usr/share/envy: No such file or directory
python: can't open file 'interface.py': [Errno 2] No such file or directory
root@daniel-desktop:/home/daniel# 

root@daniel-desktop:/home/daniel# envyng -g
/usr/bin/envyng: line 11: cd: /usr/share/envy: No such file or directory
Traceback (most recent call last):
  File "/usr/share/envyng-gtk/envynggtk.py", line 7, in <module>
    from Envy import objects
ImportError: No module named Envy

root@daniel-desktop:/home/daniel# envyng --uninstall-all
/usr/bin/envyng: line 26: cd: /usr/share/envy: No such file or directory
python: can't open file 'pulse.py': [Errno 2] No such file or directory

---

### Post by xc3RnbFO8P on 2008-07-02
Did try to reinstall it and then uninstall.

---

