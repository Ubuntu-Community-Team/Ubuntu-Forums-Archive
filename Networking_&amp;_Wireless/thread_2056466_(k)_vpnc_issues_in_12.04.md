---
title: "(k) vpnc issues in 12.04"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by DBSLLC on 2012-09-11
Hey guys and gals, I used to run Ubuntu 11.10 with kvpnc but I recently bought a new SSD and for various reasons was advised to install 12.04 on it clean, reinstall all programs, and lastly restore client data.

For the most part everything works ok but I'm having a heck of a time getting (k)vpnc to work.  I installed kvpnc with Synaptic but whenever I try to start the program it just hangs and eventually dies.  Is there any way to gather some debug information to see what's going on?

Additionally, I can't even get vpnc to work on the new 12.04 install.  I copied the .conf file for one of my clients from my old Ubuntu instance to new and I'm getting a failed login.  Is it possible the Xauth UserID and Password in the .conf file (which I can obviously read) are wrong?  Is there a way to pull the password out of KDE Wallet Manager?

==========================

UPDATE:  I used the command below to "Unhide" KDE WM on my old machine and was able to verify that the password I've been trying to use via CLI in 12.04 is correct.  Maybe there's some global setting in kvpnc that is saved on my old box but not configured for vpnc on the new box?  This is a Cisco VPN I'm attaching to.

qdbus org.kde.kwalletmanager /kwalletmanager/MainWindow_1 com.trolltech.Qt.QWidget.show

TIA!
Phil

---

