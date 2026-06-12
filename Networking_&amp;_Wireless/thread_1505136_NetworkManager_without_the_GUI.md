---
title: "NetworkManager without the GUI"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by BillRebey on 2010-06-08
I'm using 9.10 on headless boxes that I need to deploy in large quantities.   Currently, I'm using the "traditional" network management tools:  /etc/network/interfaces file, "ifconfig wlan0 ...", wpa_supplicant, etc.  This allows me to load all the boxes with identical installation images with a known static IP address, and connect to them one at a time and via Ethernet and run a scripted configuration via SSH and SCP.  

However, I'm finding that the networking is very unreliable, my network card's driver doesn't Roam in WEP mode, it's difficult to auto-switch between wired and wireless networking, etc.  I've also heard that NetworkManager solves all these problems.

How, though, do I set up/configure NetworkManger from the command line or via config files so that I don't have to run a GUI on each machine and manually configure it with a mouse??  

All the information I find on NetworkManager references network-manager-gonme to configure it, which won't work for me.  I need a solution that allows me to script (or otherwise programmatically) set up networking.  The mn pages on nm-tool and NetworkManager are woefully inadequate.

Any pointers to a resource are greatly appreciated!

---

### Post by Jose Catre-Vandis on 2010-06-08
Try **WICD** first. It has an ncurses (CLI) graphical interface and a scriptable cli client, takes care of wireless and wired, and for me has been bomb-proof.
```
sudo apt-get install wicd wicd-daemon wicd-gtk python-wicd wicd-curses wicd-cli
```

> Wicd is a general-purpose network configuration server which aims
to provide a simple but flexible interface for connecting to networks.
Its features include:
wide variety of settings.
 * ability to connect to (and maintain profiles for) both wired and
   wireless networks;
 * support for many encryption schemes, including WEP, WPA, WPA2 and
   custom schemes;
 * wireless-tools compatibility;
 * tray icon showing network activity and signal strength;
 * lack of GNOME dependencies (although it does require GTK+), making it
   easy to use in Xfce, Fluxbox, Openbox, Enlightenment, etc.

---

