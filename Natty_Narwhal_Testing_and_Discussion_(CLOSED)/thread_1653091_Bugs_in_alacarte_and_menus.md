---
title: "Bugs in alacarte and menus"
date: 2010-12-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2010-12-26
The "New Separator" button in alacarte does nothing.

The "System=>Administration=>Users and Groups" entry is missing from the menu.

Is there a way to get the menus working in Unity?

Clicking on the Ubuntu logo in the upper left corner opens a window with  links to installed programs.  Is this a work in progress?

---

### Post by mc4man on 2010-12-26
> Is this a work in progress?
Of course
> "System=>Administration=>Users and Groups"
You may find, for the moment, that adding 'control center' to your launcher will prove useful, the above is available there.
(a few things that aren't visible in control center can be added thru main menu, ie. - software sources, file management, ect.

---

### Post by efflandt on 2010-12-26
I am not familiar with alacarte.  I don't see "Users and Groups" in Control Center.

**sudo adduser *username*** can be used to add users.  I simply use **sudo nano /etc/group** to add a user to groups (comma with no spaces between usernames works).  Technically on a multi-admin system you should probably use **sudo vigr -g** instead to lock the group file during editing:

```
adm:x:4:efflandt,deffland
```There are other things to sort out with Compiz and Unity before they work on menus.  Classic Desktop has menus (except all applets crash there for me), or if Failsafe works for you (I end up with no panels or hot keys).  In Unity I have to right click on desktop and close the popup before applets or menus in applications work.

So for now, the Ubuntu logo brings up /usr/share/**applications**.  I bookmarked that in file manager, so if I am doing something else with files, I can quickly get back to applications

---

### Post by mc4man on 2010-12-26
> I don't see "Users and Groups" in Control Center.
It's right there at bottom, one could open the main menu from control center to see if it's enabled.

---

### Post by JRV on 2010-12-26
> **efflandt said:**
> I am not familiar with alacarte.  I don't see "Users and Groups" in Control Center.


"System=>Preferences=>Main Menu" is a link to alacarte.

"Users and Groups" does not show up in Control Center for me either.

---

### Post by mc4man on 2010-12-26
It would seem that recent iso's no longer include gnome-system-tools

if you wish users and groups then
```
sudo apt-get install gnome-system-tools
```

---

