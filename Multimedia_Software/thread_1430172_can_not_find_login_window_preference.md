---
title: "can not find login window preference"
date: 2010-03-15
forum: Multimedia Software
---

### Post by akashnayak on 2010-03-15
i can not find login window preference in ma admin. section. There is login screen option but not the later. I want 2 change my login screen but as a result i cant

---

### Post by EndorphinE on 2010-03-15
Try to go to the System -> Administration -> Login Window to change the login theme. Or you may try:
```
gksu /usr/sbin/gdmsetup
```
Under the ALT+F2 Run application menu.

---

### Post by mikemelen on 2010-03-15
for change the appearance of login screen on ubutntu 9.10, pls follow below steps

1. Logout of your current session
2. Type  Ctrl-Alt-F1
3. Login using your normal login/password
4. At the command line prompt type: [COLOR=blue]export DISPLAY=:0.0[/COLOR]
5. then type: [COLOR=blue]sudo -u gdm gnome-control-center[/COLOR]
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

---

### Post by jcoles on 2010-03-18
But where do we get to set substantive options? I don't want Ubuntu to be like a Mac, where all you can change is the colours.

For my login screen, I don't want a list of known users, just a Username field. Can I get that?

I notice there is an option to auto-login to one account, but "allow x seconds for anyone else to log in first". That might work for me, but I couldn't figure out how this other person logs in. The Login button ended the login delay. It didn't give me an option to enter a user name. What am I missing?

---

### Post by jcoles on 2010-03-19
I got the simple login screen I wanted by switching to XDM. Just install the xdm package, and as part of the install you are asked to choose between XDM and GDM (the default Gnome login screen).

---

