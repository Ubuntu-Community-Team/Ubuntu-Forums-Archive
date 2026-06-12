---
title: "Installing Flash 10 problems"
date: 2009-12-05
forum: Multimedia Software
---

### Post by Naater on 2009-12-05
I tried to install adobe flash player on ubuntu 9.10 and it didn't work. I tried many ways. now, whenever I try to install anything a message pops up and prevents me. This is what it says:
"E: the package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it."

Okay, but I CAN'T reinstall it... what do I do?

---

### Post by Dubbayoo on 2009-12-05
Tried to install from where? Remove everything you installed then try:

sudo apt-get install adobe-flashplugin

---

### Post by dentaku65 on 2009-12-05
try my guide :-)
[http://ubuntuforums.org/showthread.php?t=1346226](http://ubuntuforums.org/showthread.php?t=1346226)

---

### Post by Naater on 2009-12-05
Nope, I'm telling you; it is weird. I try to reinstall, remove, install... it fails and I get this massage:

 "E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it."

---

### Post by wojox on 2009-12-05
Here you go:

#Remove Flash
# Deletes a troublesome config file
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
# Force-reconfigures adobe-flashplugin
sudo dpkg-reconfigure adobe-flashplugin --force
# Force-removes adobe-flashplugin
sudo dpkg --purge --force-all adobe-flashplugin
# Installs flashplayer the easy way
sudo apt-get install flashplugin-nonfree

---

### Post by Naater on 2009-12-05
> **wojox said:**
> Here you go:

#Remove Flash
# Deletes a troublesome config file
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
# Force-reconfigures adobe-flashplugin
sudo dpkg-reconfigure adobe-flashplugin --force
# Force-removes adobe-flashplugin
sudo dpkg --purge --force-all adobe-flashplugin
# Installs flashplayer the easy way
sudo apt-get install flashplugin-nonfree


WOW! awsome! You work like a DREAM! everything works now :) thanks a bunch!

---

### Post by GregFuess on 2009-12-05
Didn't work for me, and I have the exact same problem.  The computer janiltor seduced me into inadvertently deleting flashplayer.  Now when I follow the above commands, I get the following error message:

Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 244362 files and directories currently installed.)
Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help appreciated

---

