---
title: "Autostarting nvidia-settings on mythtv"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by Lem on 2007-06-24
I've done a combined frontend/backend install of mythtv on 7.04 - all working fine. However, i want to add nvidia-settings --load-config-only to the startup script to overscan the image onto my tv correctly.

However, I don't know the password for the mythtv user so I can edit anything in .local which is where the startup seems like it might reside.

Any ideas on how to do this?

---

### Post by Lem on 2007-06-27
Any mythtv or openbox experts out there?

---

### Post by superm1 on 2007-06-30
Hi Lem.

Two options here.

1) While in the mythtv autologin session, hit ctrl alt right.  You will be brought to a virtual desktop.  You can right click the desktop and open a terminal.  Launch nvidia-settings.  Once the settings are saved, log out and back in.  They should automatically load. (Because of a session login script that is setup already)

2) Make the setting as a regular user. They are saved in the home directory as a .nvidiasettingsrc i think.  Copy that file to /home/mythtv and chown it to mythtv:mythtv

Either way, they should autoload once made.

---

### Post by Lem on 2007-07-01
Thank you! :)

---

