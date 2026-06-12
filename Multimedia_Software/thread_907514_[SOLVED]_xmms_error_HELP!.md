---
title: "[SOLVED] xmms error HELP!"
date: 2008-09-01
forum: Multimedia Software
---

### Post by Eremis on 2008-09-01
Hi everyone

I just installed xmms (using alien to convert rpm) , but first of all it did not make an icon in applications --> Sound & Video, and when I lunch it using terminal, this is what i get:

andriy@andriy-desktop:~$ xmms

Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory
unable to open port `/dev/ttyS1' (Input/output error)
unable to open port `/dev/ttyS1' (Input/output error)


By the way it still loads the player, and i can use it, but when i close the terminal it turns off. 

Please reply! :confused:

---

### Post by nicedude on 2008-09-01
You should have used the deb package which is available several places instead of using alien to convert a rpm. I would uninstall the one you installed and then go to the link I give below and download the .deb package ( not the source but the deb ) as that will check dependencies etc for you during install and it works just fine for me here on Hardy Ubuntu.

I love xmms, as it follows the KISS principle "Keep It Simple Stupid" while still doing everything I want and with low resource usage :-)


HERES THE DEB YOU NEED
[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

---

