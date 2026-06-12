---
title: "Plain black screen, help?"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by Davasaurous on 2007-06-18
Hey guys, I've just enabled my graphics card drivers after playing around in Ubuntu for a few days, now when I start up I'm just getting a blank screen. I've read around a bit, but I don't know how to disable the drivers before booting the OS. I've got an Nvidia card, I think I just need to get "Envy" and update my drivers, but I can't get in.

HALP :(

---

### Post by Davasaurous on 2007-06-19
Bump, still having the problem.

Can I upgrade my drivers over the net through the terminal on startup before entering the GUI?

---

### Post by Verminoz on 2007-06-19
You can restore your desktop by entering in recovery mode. When you login in the console check this directory for backups of xorg.conf
/var/backups/xorg

If there's not one there check in the /etc/X11 directory for something like this "xorg.conf.backup"
I think envy backs up your xorg.conf before doing anything to it. If you find a backup just copy it over the existing one (/etc/X11/xorg.conf) by giving
sudo cp /directory/of/the/found/file/the.file /etc/X11/xorg.conf

If you don't find a backup of xorg.conf you will have to open xorg.conf with this:
sudo pico /etc/X11/xorg.conf

Find the driver section and change this line
driver      "nvidia"
to
driver     "nv"
Save and exit!

Then by giving
exit 
or by rebooting you should be able to re-enter your graphical environment.


I can't get my nvidia GeForce 7300 GS to work either and I get the same problem as you, with all the methods available........

---

