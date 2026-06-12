---
title: "Idiot Needs Help"
date: 2013-07-13
forum: Multimedia Software
---

### Post by AnotherKevin on 2013-07-13
I did something to trash my flashplayer and it no longer works.  Could some one PLEASE give me the commands to remove and reinstall?  I'm running 13.04.


Thanks....

---

### Post by ajgreeny on 2013-07-13
Use synaptic package manager to search for flash.  You can then remove it if necessary (use remove completely), and finally re-install.  If you look in firefox with about:plugins in addressbar, what flash plugin is now installed?

---

### Post by Mr.Dunham on 2013-07-13
As **ajgreeny** said above, best and easiest option is to "Mark for complete removal" on Synaptic, and reinstalling later.

---

### Post by Yellow Pasque on 2013-07-14
Don't forget to clear the user cache before reinstalling by removing the ~/.adobe directory.
```
sudo apt-get purge flashplugin-installer
rm -r ~/.adobe
sudo apt-get install flashplugin-installer
```

---

