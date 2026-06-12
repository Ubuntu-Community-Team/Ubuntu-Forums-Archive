---
title: "install apache with no internet access"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by gmadamide on 2013-05-28
Hi everybody
I have ubuntu lucid 10.04 installed on a robot so I have no internet access. I use ssh to connect to it, or a usb to transfer files. 
How can I install on it apache2? I searched online but the only options are with apt-get install. Is there some other way?

Thank you
George

---

### Post by zt14427 on 2013-05-28
try installing XAMPP [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html) on your robot.

---

### Post by gmadamide on 2013-05-29
OK thank you

---

### Post by Lars Noodén on 2013-05-29
You can download the packages you need and install them with [dpkg](http://manpages.ubuntu.com/manpages/raring/en/man1/dpkg.1.html).  In particular you can look at using offline package management:

[http://www.debian-administration.org/article/Offline_Package_Management_for_APT](http://www.debian-administration.org/article/Offline_Package_Management_for_APT)

You could also add **—print-uris** to your **apt-get install** command on your robot and it will return a bunch of URLs for the .deb files.  You can then take that list to a machine with networking and download everything to take back to your robot.

```

apt-get install apache2 --print-uris

```

Please, please consider staying with real packages and the package manager.

(xampp is a useful crutch for Windows users but introduces a lot of problems for Linux users, if you can solve your task without it that will be much better for you.  It install things in non-standard locations and fails to use the package manager.  It is the package manager which will automatically handle dependencies for you as well as facilitate security updates and notifications.  You have to do all that by hand with xampp.  Also it installs a redundant copy of perl which will be a little out of sync with what is already installed on your system.  Mixing in packages outside the package manager is a recipe for avoidable trouble.  Been there, done that. )

---

### Post by scbingham on 2013-05-29
I was looking into installing packages off line & found this:

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

Hopefully this will help you out.

---

