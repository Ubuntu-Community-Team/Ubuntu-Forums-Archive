---
title: "Error, error &amp; error"
date: 2009-12-05
forum: Multimedia Software
---

### Post by GregFuess on 2009-12-05
subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone know what the above means?  I was trying to install flashplayer after the computer janitor seduced me into removing it as a rarely used (?!) program.  But when I attempt to reinstall, the message above is the result.

Any help appreciated.

Greg

---

### Post by HappyFeet on 2009-12-05
Try:
```
sudo apt-get install -f
```

---

### Post by GregFuess on 2009-12-06
I appreciate your help, and am feeling a bit overwhelmed.  I inadvertently deleted flashplayer when prompted to do so by the computer janitor, and when attempting to reinstall it, get this error code  Using the recommended code does not seem to correct the problem, but maybe I am doing something wrong so am copying and pasting the whole command prompt her, hoping for some more help:


greg@dell-desktop:~$ sudo apt-get install -f
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnss3-dev libnspr4-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  pdvdlinux
0 upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
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
greg@dell-desktop:~$ 


Any thoughts or recommendations appreciated.  I am new to this Ubuntu thing, and not sure what to  do.

Regards

Greg

---

