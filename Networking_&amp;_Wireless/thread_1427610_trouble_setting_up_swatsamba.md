---
title: "trouble setting up swat\samba"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Will5757 on 2010-03-11
i've been trying for the last 2 days (on\off) to setup a simple samba share to connect to my windows 7 box

[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat) tells me to run "sudo apt-get install swat xinetd" in a terminal but it returns
"reading package lists... Done
building dependency tree
reading state information... done
E: couldn't find package swat"

i've been having similar issues no matter what distro i download and install on the linux box

---

### Post by johnson.d on 2010-03-12
1) You can setup a simple Samba setup in a Ubuntu Machine using the following steps:

Samba setup:
i) Samba can be installed using the following command:

$ sudo apt get install samba

ii) Append the following lines to the file /etc/samba/smb.conf 

[<share-name>]
path = /<share-path>
browseable = yes

iii) Now restart the samba service by using the following command:

$ sudo /etc/init.d/samba restart

---

### Post by Will5757 on 2010-03-12
thanks (didn't completely solve my problem, but i was finally able to get a share to at least show up in windows 7) i figured the rest out after i could actually see something

---

### Post by johnson.d on 2010-03-15
You can try the following steps for installing SWAT:

1) Goto Gnome menu-> System-> Administration-> Synaptic Package Manager
2) A window will open, goto System-> Repositories.Here check the Community maintained open source software box and click close.
3) Now click on the reload button of the main window.
4) After reloading search for 'swat' in the search tab.
5) Click on the box which shows swat and mark for installation.
6) Click apply.

After installation, try connecting to swat using the url 'localhost:901' in the address bar of the browser.

---

