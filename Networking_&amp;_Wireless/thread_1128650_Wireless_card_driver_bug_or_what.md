---
title: "Wireless card driver bug or what?"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by luiznetto on 2009-04-17
My laptop is Acer Aspire 5315, with wireless antenna Atheros AR5007EG. I run Ubuntu 8.04 (Hardy Heron). To make my wireless internet work, I had to install a driver for my wireless antenna, which is madwifi-ng-r2756+ar5007.tar.gz. It works as it's supposed to when I go to an internet café; they give me a password and I connect, and next time I return to the café it connects automatically, without any need to input the password again. I live in a house with several roommates, and recently our landlord acquired Comcast wireless internet. He gave me a 26 digit (letters + numbers) hexa key to connect. It works, but the problem is, each time I reboot, I have to enter the whole 26 digits again to reconnect to the wireless network! This is most awkward and inconvenient. Is there a bug with my wireless driver? Should I uninstall it and install another version of the same driver that doesn't have the same bug? If this is the case, where to find it? Or is there another way to fix it? Any help will be greatly appreciated.
Regards, Luiz

---

### Post by luiznetto on 2009-05-19
I found out that the problem has nothing to do with my wireless card driver, but with my Gnome Network Manager. NetworkManager stores passwords in the Gnome Keyring. Gnome Keyring always assumes your keyring password is the same as your Ubuntu login password. If you happen to change that password, though, Gnome Keyring does not automatically update your keyring password. I had recently changed my Ubuntu password, that's why I kept getting the message "Enter password for default keyring to unlock - The application 'NetworkManager Applet' wants access to the default keyring but it is locked." To solve the problem, I deleted the file

/home/luiz/.gnome2/keyrings/login.keyring

(this file used to be called default.keyring in previous versions of Ubuntu)

After I logged out and rebooted, the file was created again by Gnome Network Manager with correct permissions next time I connected.

The name of the package is gnome-keyring; to check if you have it installed on your system, enter

$ aptitude show gnome-keyring

that's where your network passwords are stored.

Some useful links:

[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

[http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html](http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html)

http://forum.paldo.org/index.php?action=topic&topicnr=509&hilikeywords=a:0:{}

[http://techxplorer.com/2007/10/28/changing-the-gnome-keyring-master-password/](http://techxplorer.com/2007/10/28/changing-the-gnome-keyring-master-password/)

---

