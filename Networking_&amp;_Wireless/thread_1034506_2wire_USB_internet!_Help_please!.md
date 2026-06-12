---
title: "2wire USB internet! Help please!"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by shoto1699 on 2009-01-08
I am currently dual-booting Windows XP and Ubuntu 8.10 and this computer does not have an ethernet port, so I'm stuck with usb internet connection. I am wondering if there are any fixes to this problem. My router model is 2wire 1000sw. Please help me! I would really like to use Ubuntu!!!

---

### Post by shoto1699 on 2009-01-08
anyone got a  clue or a driver to fix this?

---

### Post by dmizer on 2009-01-08
Try this: [http://ubuntuforums.org/showthread.php?t=707972](http://ubuntuforums.org/showthread.php?t=707972)

Edit:
As a courtesy to the huge number of people on this forum who are also having trouble, please wait at least 24 hours before bumping a thread. If you need immediate help, you'll probably get quicker support by joining Ubuntu's IRC channel. Thanks :)

---

### Post by shoto1699 on 2009-01-08
alright thx for the help and for the suggestion

---

### Post by shoto1699 on 2009-01-08
hey also i dont have internet access and the tut didnt help xD
cuz it keeps getting an error saying file is not find when i try and sudo it

---

### Post by dmizer on 2009-01-08
Try this:
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```
Then try the howto again.

---

### Post by shoto1699 on 2009-01-08
i meant like the file im trying to sudo xD also wut is the irc for ubuntu.

---

### Post by dmizer on 2009-01-08
I understand. I think the problem is that the file you are trying to sudo doesn't exist because you don't have the ndiswrapper package installed yet. Once you install ndiswrapper as I outlined above, then you should be able to sudo the files.

IRC support information here: [http://www.ubuntu.com/support/community/chatirc](http://www.ubuntu.com/support/community/chatirc)

---

### Post by shoto1699 on 2009-01-09
yes i tried installing ndiswrapper and i tried dragging tthe files to usr/sbin but it didnt allow me

---

### Post by dmizer on 2009-01-10
> **shoto1699 said:**
> yes i tried installing ndiswrapper and i tried dragging tthe files to usr/sbin but it didnt allow me

The howto doesn't mention anything about dragging files to /usr/sbin ... that I can see?

You can't drag and drop to /usr/sbin because it is not owned by your user. You should save the files in your home directory somewhere.

---

