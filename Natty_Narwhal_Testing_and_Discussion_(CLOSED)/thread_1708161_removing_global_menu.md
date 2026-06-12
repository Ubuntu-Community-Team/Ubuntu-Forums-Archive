---
title: "removing global menu?"
date: 2011-03-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-03-16
Just a question from someone who tried natty for a full week.
 
Will it be possible without much trouble to return menu bars back to applications rather than the panel easily?

---

### Post by mc4man on 2011-03-16
see here
[http://ubuntuforums.org/showthread.php?t=1690668](http://ubuntuforums.org/showthread.php?t=1690668)

-------------------------------------------------------------

If you wished to do individually then most apps in most common uses can be switched by editing the apps .desktop (if 'global returns to qt4 apps then a diff. env is usually needed

Ex. - return menu to gedit

```
gksudo gedit /usr/share/applications/gedit.desktop
```

Make the Exec= line look like this 

```
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=env UBUNTU_MENUPROXY=0 gedit %U
```

If you had an app that was run at times from the cli you'd need to create a binary diversion instead of editing the .desktop.
Ex. given here for audacity, post 4,  though the .desktop edit is generally all that's needed for most uses.
[http://ubuntuforums.org/showthread.php?p=10553637](http://ubuntuforums.org/showthread.php?p=10553637)

---

