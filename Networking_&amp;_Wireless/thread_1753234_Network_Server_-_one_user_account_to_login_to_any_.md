---
title: "Network Server - one user account to login to any PC"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by geidorei on 2011-05-08
Hi - hope someone can point me in the right direction, as Im getting confused.

This is what I want to do:
Network server to administer accounts for all users, one login 
ie at login select or type in user name and password  to login - so that I don't have to setup users separately on all PC's so that they can login from any computer.

Many thanks, Karl

---

### Post by geidorei on 2011-05-20
bump - anybody???

---

### Post by drdos2006 on 2011-05-20
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood





```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by geidorei on 2011-05-22
Brilliant - many thanks for the info.

---

