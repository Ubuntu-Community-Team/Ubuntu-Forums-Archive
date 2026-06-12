---
title: "jsymphonic - can't see it on Menu"
date: 2010-01-03
forum: Multimedia Software
---

### Post by Love2MeetU on 2010-01-03
I've installed Jsymphonic with Synaptic Manager, but can't see it anywhere on the Menus. I've looked all over the place. I've also gone through Preferences>Main Menu, but it still doesn't appear.

Where do I find it, and how do I get it to run?

---

### Post by x33a on 2010-01-03
try
```
killall gnome-panel
```now see, if it appears on the menu.

if not, then create an entry in the menu yourself.

to find the executable, try
```
whereis jsymphonic
or
whereis symphonic
```

---

### Post by Love2MeetU on 2010-01-04
Didn't appear on menu, but the "whereis" found it here;

> jsymphonic: /usr/bin/jsymphonic /usr/share/man/man1/jsymphonic.1.gz


Now next what do I do? Is the .gz an executable?

---

### Post by x33a on 2010-01-04
press ctrl+f2, type:
```
alacarte
```

this opens the menu editor.

Now click sound and video, then click new item.

1. type: Application
2. name: Jsymphonic
3. command: /usr/bin/jsymphonic
4. comment: anything you want (like portable music manager etc.)
then click ok and you'll have a menu entry under sound and video.

also, the .gz file is the man page, not the application binary.

---

### Post by Love2MeetU on 2010-01-05
Thank you, It worked.

---

