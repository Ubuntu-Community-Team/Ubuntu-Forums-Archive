---
title: "Network-manager"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by bizkyt on 2010-11-01
Hello,

I have a problem with my network manager. I had the 0.8.1 version (the normal, that comes with the updates), but yesterday I have installed the 0.8.2 (beta), from projects.gnome.org/NetworkManager (untar the file, ./configure, make and make install on it).
But after this, I lost my connections to internet from wireless and ethernet cable too. So I went to Synaptic and removed completely all network-manager packages, make restart and reinstalled it from the synaptic again (with the help from wicd to connect to internet) . But it don't work, is always showing the 0.8.199 (0.8.2), in the network manager aplet on tray icon and the internet don't work with networkmanager.
Anyone knows how to completely remove network manager, or any manner to get network-manager to work again?


Best Regards

---

### Post by bizkyt on 2010-11-01
bump

---

### Post by anwmalos on 2010-11-01
hello,

Go to the source tree of the network manager that you downloaded and type "make uninstall". If that doesn't work you will have to manually remove the compiled version of network manager from your system that usually resides in /usr/local/

---

### Post by bizkyt on 2010-11-01
I tried the "make uninstall" and didn't work. So went to /usr/local and removed all with name "network-manager" and files with "nm-*". 
After that, installed network-manager from synaptic along with network-manager-gnome (applet). I do a reboot, but the network-manager applet don't appear in the tray. Now that I'm thiking I remember that I deleted files and folders that say nm-applet.

But isn't suppose that all the files that network-manager needs, are installed when from synaptic?

---

### Post by bizkyt on 2010-11-01
Anyone? I really need network-manager :s

---

### Post by bizkyt on 2010-11-02
I made a fresh installation of ubuntu to resolve this.

---

### Post by sml on 2011-01-15
Other solutions other than a fresh install?

Must be better ways to close out this thread.

---

