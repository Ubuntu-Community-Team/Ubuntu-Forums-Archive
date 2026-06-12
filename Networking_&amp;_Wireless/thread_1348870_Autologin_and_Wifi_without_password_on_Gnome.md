---
title: "Autologin and Wifi without password on Gnome"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2009-12-07
many users of Ubuntu with Gnome have come across the issue of setting their computer to auto login only to have to type their password once their desktop loads in order to connect to their wireless network.
The solution that I've seen offered over and over again is to use KDE, as this option is available out of the box.  Well, I personally do not care for KDE at all and in my opinion, installing KDE alongside an existing Gnome install makes a disaster of your system and installs many redundant or unnecessary applications.
The problem of not being able to connect without typing in a password is caused by network-manager.  In order to fix this, all I did was install wicd and disable the network-manager at startup in the 'sessions' menu.
A few caveats that I would warn you about if you should choose to do this are:
1) I had to reset the settings on my wireless router and change my security type from WEP to WPA.  For some reason, using wicd my laptop couldn't obtain an IP address.
2) I have disabled samba for file sharing because I don't have any Windows computers on my network and NFS is ten times as fast on Linux as samba.  Despite the fact that I edited my /etc/fstab to mount my network shares and it worked fine before, after installing wicd on my laptop my shares would not mount at boot.
The workaround I came up with for that was to create a simple script containing the mount command
```
gksudo mount 192.168.X.X/home /home/user/Desktop/Network
```
which I saved as 'shares.py' and set as an executable file.  Then I added that script to my 'menu>system>preferences>sessions' and it works just fine.
*NOTE:  Without going into too much detail, the directory /home/user/Desktop/Network is actually a symbolic link to the a directory I created called /Network.  I just removed the 'Network Connections' shortcut from my desktop by editing the gconf-editor--apps>nautilus>desktop and unchecking 'network_icon_visible'

Sure, it may not be the most straight forward way to do things, but I think it works just fine.  It gets the job done, and now my wife isn't complaining about having to type in passwords all the time.

---

