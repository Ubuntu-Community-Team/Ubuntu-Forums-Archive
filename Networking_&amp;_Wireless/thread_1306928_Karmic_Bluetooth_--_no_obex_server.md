---
title: "Karmic Bluetooth -- no obex server"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by fragos on 2009-10-30
In the past we could send files via Bluetooth with the default install but had to install gnome-obex-server, recently called Bluetooth File sharing, to send file to Ubuntu via Bluetooth. I've been Bluetooth file transferring with my Nokia N810 tablet for some time over a number of releases. I did an upgrade from 9.04 to 9.10 and gnome-obex-server is no where to be found and I can no longer send from my N810 to Ubuntu. The other direction works fine. Is it perhaps now called gnome-file-share?

---

### Post by AlanR8 on 2009-10-30
Install "blueman" and all will be resolved. You'll even be able to connect to the web via your phone with bluetooth with a couple of clicks...

---

### Post by fragos on 2009-10-30
> **AlanR8 said:**
> Install "blueman" and all will be resolved. You'll even be able to connect to the web via your phone with bluetooth with a couple of clicks...

Installed Blueman but couldn't run it so I reinstalled the Bluetooth Manager that comes with Karmic.

---

### Post by walmis on 2009-10-31
> **fragos said:**
> Installed Blueman but couldn't run it so I reinstalled the Bluetooth Manager that comes with Karmic.

What do you mean you couldn't run it? It is in System -> preferences -> Bluetooth Manager
or did you get an error while attempting to run it?

PS. In karmic archives it is a bit outdated (1.10), you should add the official ppa for the latest version (1.21) - [https://edge.launchpad.net/~blueman/+archive/ppa]("https://edge.launchpad.net/%7Eblueman/+archive/ppa")

---

### Post by Larppaxyz on 2009-10-31
After installing new packages from mentioned PPA, OBEX file server with kbluetooth now works.

Repositories for Karmic : 

deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) karmic main

---

### Post by fragos on 2009-10-31
> **walmis said:**
> What do you mean you couldn't run it? It is in System -> preferences -> Bluetooth Manager
or did you get an error while attempting to run it?

PS. In karmic archives it is a bit outdated (1.10), you should add the official ppa for the latest version (1.21) - [https://edge.launchpad.net/~blueman/+archive/ppa]("https://edge.launchpad.net/%7Eblueman/+archive/ppa")

Blueman un-installed the Gnome Bluetooth Manager that was accessed from the applet bar and didn't appear in the Application or System menu. I went to the command line and tried "which blueman" and again it wasn't found. The blueman repository was configured with Ubuntu Tweak and Blueman installed when it came up as an available update.

---

### Post by walmis on 2009-10-31
the command you're looking for is blueman-applet

---

### Post by fragos on 2009-10-31
> **walmis said:**
> the command you're looking for is blueman-applet

This time it worked when installed. I did have to add blueman-applet to my startup applications and remove the bluetooth-applet.

---

