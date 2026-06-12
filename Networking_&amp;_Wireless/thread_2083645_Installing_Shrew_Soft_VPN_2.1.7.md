---
title: "Installing Shrew Soft VPN 2.1.7"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by TobyBv on 2012-11-13
I am new to Ubuntu (12.4) and trying to figure out how things are installed and done. 
I am trying to install  Shrew Soft VPN 2.1.7 and coming accross an error message: 
Unable to locate required package : QT


[INDENT]$ cmake -DETCDIR=/etc -DNATT=YES -DQTGUI=yes
-- Using install prefix /usr/local ...
-- Using etc path /etc ...
-- Using lib path /usr/local/lib ...
-- Using man path /usr/local/man ...
-- Using binary /usr/bin/flex ...
-- Using binary /usr/bin/bison ...
-- Enabled NAT Traversal support ...
-- Could NOT find Qt3 (missing:  QT_QT_LIBRARY QT_INCLUDE_DIR) 
CMake Error at CMakeLists.txt:423 (message):
  Unable to locate required package : QT
[/INDENT]What I have tried so far is    apt-get install libqt4-dev which is installed.
I also tried apt-get install libqt3-mt libqt3-mt-dev as I saw suggested, [http://ubuntuforums.org/showthread.php?t=1665584](http://ubuntuforums.org/showthread.php?t=1665584) 
but these packages could not be found.


I assume I need Qt3 (as opposed to 4 which seems to be the current version)but I cannot figure out how to install it.

Would appreciate any insight!

---

### Post by TobyBv on 2012-11-13
Sorry, I just realized I am actually running 12.10 and Shrew has been removed from the 
application launcher because it requires qt3libs. [http://comments.gmane.org/gmane.network.vpn.shrew.user/2773](http://comments.gmane.org/gmane.network.vpn.shrew.user/2773)

Is there a way around this? Or an alternative way to connect? (I have a file with a .vpn extension to import. Is there an alternative vpn?
Thanks!

---

### Post by ahallubuntu on 2012-11-13
I am not familiar with Shrew Soft VPN.  I have been using OpenVPN for years and recommend it.  I have not installed it in Ubuntu 12.04 or 12.10 however so can't speak to how well it works there.

---

### Post by TobyBv on 2012-11-14
I have a .vpn file with the configurations for shrew. Would I be albe to use openvpn with it?

---

### Post by sracz on 2013-01-09
Try to install the latest development release (currently 2.2.0-rc-2).

It will work with qt4.

---

