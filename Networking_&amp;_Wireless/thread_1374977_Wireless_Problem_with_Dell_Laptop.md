---
title: "Wireless Problem with Dell Laptop"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by richard.scott-ettrick on 2010-01-07
I am using a Dell Inspiron 1545 with Windows 7 doaded on to it.I am running Ubuntu Karmic from a Philips USB Hard drive with kernel 16 on it. I cannot get the wireless system to work on it. It is setup exactly the same as my HP Laptop execpt that Ubuntu is loaded alongside Windows XP on the laptop hard drive. I can access my router if I use a cable. When I check the settings I am told Auto eth1 has never been used although I was using it at the time. Anyone any Ideas how to make it work? I am using a US Robotics USR9110 Router which allows me to use both wired or wireless connection.

---

### Post by bkratz on 2010-01-07
> **richard.scott-ettrick said:**
> I am using a Dell Inspiron 1545 with Windows 7 doaded on to it.I am running Ubuntu Karmic from a Philips USB Hard drive with kernel 16 on it. I cannot get the wireless system to work on it. It is setup exactly the same as my HP Laptop execpt that Ubuntu is loaded alongside Windows XP on the laptop hard drive. I can access my router if I use a cable. When I check the settings I am told Auto eth1 has never been used although I was using it at the time. Anyone any Ideas how to make it work? I am using a US Robotics USR9110 Router which allows me to use both wired or wireless connection.

I believe the Dells use relabeled Broadcom devices, if you do a 
lspci -nn
in the terminal and it says something like BCM43xx go to this page and follow the appropriate instructions.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by richard.scott-ettrick on 2010-01-07
> **bkratz said:**
> I believe the Dells use relabeled Broadcom devices, if you do a 
lspci -nn
in the terminal and it says something like BCM43xx go to this page and follow the appropriate instructions.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
Thankyou for your help. It now works perfecly.

---

### Post by bkratz on 2010-01-07
Please go to the thread tools above and mark as [solved] just it case it helps someone else. Also is that what you found?

---

### Post by richard.scott-ettrick on 2010-01-07
> **bkratz said:**
> Please go to the thread tools above and mark as [solved] just it case it helps someone else. Also is that what you found?
Yes thankyou. It works now. It started to work without a restart but I restarted it anyway just to be sure. thankyou again for your help.:)

---

