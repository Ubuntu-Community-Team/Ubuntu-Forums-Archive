---
title: "Network Authentication"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by leostrom on 2006-05-08
Guess what!  I am just starting to use and setup ubuntu.  I have it on a computer connected to a router with an ethernet card.  The router is connected to the internet through a dsl modem.  I am able to connect to the internet without a problem.  I can also see the other three windows 2K computers I have on my network.  I can see the ubuntu computer from the window computers.  My problem is that when ever I try to access the linux computer from the windows computer it asks who I want to connect as and for a password.  When I try to access the windows computers from Linux it comes up with a dialog box that says authentication required and asks for a username and a password.  I cannot get either one to take anything I enter and don't want to have to use a password anyway.  I have read several things about editing the config file but when I try to edit it it is read only.  I am banging my head against the wall.](*,)

---

### Post by Azrael on 2006-05-08
I assume you are referring to windows shares and Samba? To edit the samba config you need to use the sudo command (sudo gedit /etc/blah). You can also use the Gnome GUI tool though I think (System > Administration > Shared Folders).

---

### Post by Iowan on 2006-05-09
[https://wiki.ubuntu.com/SettingUpSamba?]("https://wiki.ubuntu.com/SettingUpSamba?")
You might also search for Samba or file sharing.
Also, check the Absolute Beginner forum - the topic has come up there several times.

---

### Post by leostrom on 2006-05-09
Thanks for the help, but I finally found what I needed to do in the online manual.  The first thing I had to do was to change user to root and then run gedit and then I was able to change the authentication lines in the samba config file.  I changed user = share and then I had to change the quest settings in windows 2K

---

