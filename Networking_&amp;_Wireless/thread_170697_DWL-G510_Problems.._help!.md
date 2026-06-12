---
title: "DWL-G510 Problems.. help!"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by kane_666 on 2006-05-05
hey, as the topic says, i have a d-link dwl-g510 and i cant get it working on ubuntu. i tried the instructions below:
- Get ndiswrapper-utils by typing "sudo apt-get install ndiswrapper-utils" in a terminal.
Give the root password when necessary.
- Get the Microsoft Windows drivers. Copy the .inf and .sys file. Paste these into a folder.
(eg. /home/<USERNAME>/Desktop/driver/)
- Open a terminal
- Type the following commands:
$ cd Desktop/driver/
$ sudo ndiswrapper -i <name>.inf
$ sudo modprobe ndiswrapper

Notice that you have to repeat the last step whenever you want to use your device within a session.

but it didn't work. the drivers i used were the winxp ones from the install cd. does annyone know how to get it working? if not i have to swap back to windows :-({|=

---

### Post by kiranbr on 2006-05-08
Checkout [http://www.ubuntuforums.org/showthread.php?t=171135&highlight=DWL-G510](http://www.ubuntuforums.org/showthread.php?t=171135&highlight=DWL-G510)

---

