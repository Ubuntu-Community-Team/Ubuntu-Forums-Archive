---
title: "shared and network printing"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by duckleet on 2010-03-02
I have 3 laptops and a imac the laptops are running ubuntu 9.10 and the imac is running 10.5.x. What I want to know is there a way to get them to share files and printing and the printer is hooked up to the imac. Kinda a noobie to this any help would help.:o

---

### Post by johnson.d on 2010-03-08
You can share the printer that is connected to you imac using the following link:

[http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh1770.html](http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh1770.html)

Now you can configure your Ubuntu Machine to install the printer that is shared form your imac using the following steps.

1) Go to Gnome menu-> System-> Administration-> Printing.
2) A window will open, Click new.
3) Another Window will open. At devices, drop down Network printer, Click Windows Printer via Samba.
4) At the right hand side, There will be a box with 'smb://'. Here enter the ip-address and the printer name as follows:
smb://<ip-address>/<shared-name of the printer>
5) Choose the driver and finish the installation.
6) Now try printing from the Ubuntu System.

---

