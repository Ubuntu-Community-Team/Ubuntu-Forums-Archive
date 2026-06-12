---
title: "Admin rights in File Browser"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by zoon_unit on 2006-06-22
Okay, I've managed to get my LAMP server and Ubuntu desktop up and running.  (woohoo!  Not bad for a total newbie)  :-)

I'd like to add subfolders to my apache folder (var/www) in order to install several evaluation packages.  But since I logged in as a user, I don't have root privileges.

How does one "turn on" root privileges in the file browser?  I know I could activate the root user account and login to gdm as root, but that seems like a dangerous proposition.  Isn't there someway to obtain temporary root access in the file browser?

note: I've already tried sudo -s -H in terminal, hoping that would persist, but when I go into the file browser, I still can't create folders

---

### Post by codejunkie on 2006-06-22
[quote=zoon_unit]Okay, I've managed to get my LAMP server and Ubuntu desktop up and running.  (woohoo!  Not bad for a total newbie)  :-)

I'd like to add subfolders to my apache folder (var/www) in order to install several evaluation packages.  But since I logged in as a user, I don't have root privileges.

How does one "turn on" root privileges in the file browser?  I know I could activate the root user account and login to gdm as root, but that seems like a dangerous proposition.  Isn't there someway to obtain temporary root access in the file browser?

note: I've already tried sudo -s -H in terminal, hoping that would persist, but when I go into the file browser, I still can't create folders[/quote] if you have sudo privliges with that user account, you can run either ```
sudo nautilus
```or ```
gksudo nautilus
```in a terminal to open a file browser with root privliges.

---

### Post by bikeboy on 2006-06-22
I gather you're in the grapical Ubuntu desktop when you try this. If so, open up a terminal as you tried, but type in "gksudo nautilus".
gksudo is used for opening graphical apps from a terminal, all you have to do is put in your user password when prompted.

When you're working in a terminal and want to do something as root, just put sudo before the command you want to execute.

---

### Post by tturrisi on 2006-06-22
add menu item:
 System Tools > File Browser (as root)

sudo gedit /usr/share/applications/Nautilus-root.desktop

put this in the file & save it:

[Desktop Entry]
Name=File Browser (Root)
Comment=Browse as root user
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;

---

