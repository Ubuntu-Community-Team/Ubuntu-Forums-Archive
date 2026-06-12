---
title: "lost login (drums)sound"
date: 2012-02-22
forum: Multimedia Software
---

### Post by sardhwk on 2012-02-22
I installed Edubuntu 11.10 on an Acer Aspire 1 D255. After recommended upgrades and PAV control I lost the login sound (drums). Audacity and VLC no problem with audio!
I checked Gnome Login sound in startup appl. Edit shows a file in usr/share/gnome/autostart/libcanberra-login-sound.desktop
At that location I found a desktop configuration file. Opening it gives the drum sound. Thus the file is there.
A post of Fractalman Oct 2011advised this command  "gksudo gedit  /usr/share/gnome/autostart/libcanberra-login-sound.desktop" to check on  "No display=false".
I did so but it returns with a prompt and it looks like the command is not executed.
I also tried to look into to file using "gksu nautilus" but  no file  that I can edit just the sound file. What is wrong and wt should I do to  get the login sound back.
A post from Forever1 suggested to use sudo instead of gksu but same that did not work.
It seems many people lost login sound after installing (ed)ubuntu 11.10. Initially it worked and then not.

---

### Post by sardhwk on 2012-02-22
I tried the guest account to check the login sound: that worked. I then changed the command in startuP application from " usr/share/gnome/autostart/libcanberra-login-sound.desktop " to what was in the guest account namely "/usr/bin/canberra-gtk-play--id="desktop-login"--description="GNOME login"  . 
But it did not work.Why, what could be wrong?

---

