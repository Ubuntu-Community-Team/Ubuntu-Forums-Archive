---
title: "Issues with Flash 10"
date: 2009-11-05
forum: Multimedia Software
---

### Post by andyt4097 on 2009-11-05
Hi. I just upgraded to 9.10 and went to upgrade to Flash Player 10. Upon doing this I started to get all sorts of problems. I got the red circle up near my clock that says Unknown Error: type 'Exceptions:SystemError' I guess I need to completely uninstall Flash but it wont let me open the package manager. When I try to do that it says: E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report. Can anyone help me? Thanks in advance!

---

### Post by Whiteaker on 2009-11-05
Try pasting this into a terminal window

  	 	 	 	 	 	  sudo apt-get remove swfdec-mozilla
 sudo apt-get remove mozilla-plugin-gnash
 sudo apt-get remove adobe-flashplugin
 sudo apt-get remove flashplugin-nonfree
 sudo apt-get install flashplugin-nonfree


Good luck

---

### Post by mac9416 on 2009-11-05
If Whiteaker's solution does not work, try this...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

---

### Post by Stanislao on 2009-11-05
I have a similar problem. If I download Flash 10 it gives me the i386 version. Problem is, I have a T2330.

---

