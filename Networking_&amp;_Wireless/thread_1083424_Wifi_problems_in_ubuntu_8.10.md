---
title: "Wifi problems in ubuntu 8.10"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by krishh123 on 2009-02-28
I have installed my ehome wireless adapter thru NDISWRAPPER 1.54.Everything works out fine but after restarting my pc i need to install the driver again by typing the following commands

depmod -a
modeprobe ndiswrapper

Can anyone suggest me how to make tis driver persistent.Is there any shell script that could run these two commands everytime i logon to ubuntu at the startup itself.

---

### Post by RedSingularity on 2009-02-28
Why not add it yourself through System>Preferences>Sessions?

---

### Post by krishh123 on 2009-02-28
Im very much new to ubuntu.Can u just give me a detailed explanation on adding sessions..

---

### Post by RedSingularity on 2009-02-28
When you go to System>Preferences>Sessions just click the ADD option.  Then type in the command you have above.  "depmod -a"  You will have to give it a name as well.

---

### Post by RedSingularity on 2009-02-28
Here do the above mentioned to get to Sessions.  Then in sessions click add. Give it a name then type this in the command box:  depmod -a && modeprobe ndiswrapper

---

### Post by krishh123 on 2009-03-01
Actually these are the steps i would type into the terminal

su
(password)
depmod -a
modprobe ndiswrapper

so for me to login into the root at the startup i have typed the command as u have said

su && (password) && depmod -a && modprobe ndiswrapper

but it did not work out.. for performing successive commands at the startup should we concatenate them with &&

---

### Post by RedSingularity on 2009-03-01
Yea, for performing commands in line with each other you put an && in between.  If you put one & in between it will activate the commands simultaneously.

What happened when you did this?

PS:  You dont put your password in the sequence.....that wont work.

---

