---
title: "How to get USB WiFi to connect BEFORE login?"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by brec on 2011-12-14
Just replaced wired ethernet to my Ubuntu 10.04 system with USB WiFi.  My main access to this system is remotely via VNC.  With the former wired ethernet the system could boot and get to and remain on the (Gnome) login screen with no local interaction required, with a LAN connection enabling me to access via VNC.

With the USB WiFi, it doesn't attempt to connect until after log in, requiring a local login before VNC access is possible.  When the WiFi connection succeeds an announcement appears (for a while) "over" the desktop.

The USB WiFi driver is from RealTek (actually, so is the ethernet).

Somewhere there's a command or script being run after login that gets the wireless software to attempt connection.  I'd like to find a way for that to happen before login.

---

### Post by Iowan on 2011-12-14
Is the USB set to "Connect automatically", and Available to all users"?

---

### Post by lswb on 2011-12-14
What Iowan means is login in on the system, then right-click on the wireless icon. Select "Edit Connections..." then the "Wireless" tab, and select your wifi name from the list presented. Click the "Edit button", enter password if prompted, then check the "Enable All Users" box at the bottom of the dialog box. Close all the dialogs. The next time your system is started, the wifi connection will be established even before any graphic logins.

---

### Post by brec on 2011-12-15
The "all users" setting solves the problem!  Thanks, Iowan and lswb.

(Since I got the WiFi hardware just today, I hadn't yet discovered there was a menu available under the signal-strength icon in the Panel...)

---

