---
title: "I cant connect to the wireless..~"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by RyozKidz on 2010-03-03
I have just installed my first LINUX Ubuntu version 9.04 ..~
And i might think to upgrade some software inside my OS ..~
At first , i tried to search online by using my window vista OS to surf some information on how to use digi broadband to connect . It failed
Then i just found a book in my university's library which is a guide for Ubuntu . And i tried the method which is connecting to the wireless  . It failed too .

Based on the book , it show us go to the System on the top panel and navigate to the Administration submenu . There , click the Windows Wireless Drivers menu option(command name ndisgtk) . But i cant find it . So i open the terminal and typed ndisgtk , the terminal displayed a message that ndisgtk is not installed and ask me to install by typing a command( forgot what is the command , something like sudo apt-get install ndisgtk) . After i typed , it displayed E:Can't find any source .

Appreciate to every comments that will be left by you all.

---

### Post by MR. ZUL on 2010-03-29
i got same problem. cannot connect digi broadband. all members please help us... i use ubuntu 9.04

---

### Post by chris0108 on 2010-03-29
Basically thats diswrapper for installing the windows driver for your device, the sudo command wont work because it needs to go online to get the file.

What i did was connect on an ethernet cable and get the files then go from there

---

### Post by ubunterooster on 2010-03-29
Try running update manager first while the computer is connected to the internet via wired ethernet. After the update manager is finished close it (the update manager) and go to system>administration>synaptic package manager.  Get the package by the name: ndisgtk

If you need the drivers and do not have time to tinker consider [http://linuxant.com](http://linuxant.com) .  They have a better program but costs $.

---

