---
title: "Password/keyring problem preventing wireless connection??"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by tad_pole on 2008-12-06
I'm having trouble getting my wireless network up on 8.10.Although my Dlink network card detects and automatically adds my WPA protected connection in Network Connections, there seems to be problems with the password. It tries to connect and another dialogue box comes up saying "Wireless Network Authentication Required" even though I've already typed in the password. What's more, the password is different to the one I typed in?!?

If I try to edit the connection, a dialogue box pops up saying "The application 'nm-connection-editor' (/usr/bin/nm-connection-editor) wants to access the password for 'Network secret for Auto *mySSID*/802-11-wireless-security/psk' in the default keyring." I am forced to select "Always allow" if I want to continue. I have looked in System>Preferences>Encryption and Keyrings and found there is no default key, if that has anything to do with it.

However, disabling WPA does not solve the problem. Network Connections still demands a password. Aaarrrgh! I have scoured the web and found many people with similar problems but few answers. Here a few links that seem relevant, but don't solve my problem.
 [confused but resolved - waiting for network key]("http://ph.ubuntuforums.com/showthread.php?t=914582")
[never made a default password for keyring and root password not working.]("http://ubuntuforums.org/showthread.php?t=966119")
[wireless password is not being saved (intrepid)]("https://bugs.launchpad.net/ubuntu/+bug/271097")

Any help much appreciated.

---

### Post by karlox on 2009-06-14
This... I like....
[http://www.ubuntued.com/?p=15](http://www.ubuntued.com/?p=15)

But there are plenty!!
[http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/)

[http://ajlcom.instantspot.com/blog/2007/05/24/Unlock-keyring-immediately-on-login](http://ajlcom.instantspot.com/blog/2007/05/24/Unlock-keyring-immediately-on-login)

[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)

---

