---
title: "BCM4311 wifi driver install but cannot connect"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by LanceRooke on 2011-09-30
This is on my old Dell Inspiron 1501.  The drivers are installed but I can not get the wifi to work.  Please help.  I'd greatly appreciate it.

---

### Post by pdc on 2011-09-30
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

if you subscribe to a thread you create, you will told if there are replies

---

### Post by garvinrick4 on 2011-09-30
With your wired connection install the marked packages below in screenshots.
Anything else remove the package. Then take wired out and reboot.
Notice I used synaptic and what is typed in search window. If still does not work
type this in a terminal and post, lots of good network card users around here: 
```
rfkill list
```

---

### Post by LanceRooke on 2011-10-19
I'm sorry, but I am brand new to Ubuntu.  A total Noob.  I have no idea what to do with those jpegs.  Could you perhaps be more detailed?  I need anything that's not in plain English to be explained as if I were mentally handicapped.  I hope that you can forgive my ignorance enough to help me out here.

---

### Post by garvinrick4 on 2011-10-19
> I'm sorry, but  I am brand new to Ubuntu.  A total Noob.  I have no idea what to do  with those jpegs.  Could you perhaps be more detailed?click on them, the screenshots and they will enlarge.
Open up synaptics and type bcm in search window.
Now install the two I have highlighted and remove any others that are installed then reboot and take
wired ethernet cable out should start up your wireless.
Or:
[http://ubuntuforums.org/showthread.php?t=1861669%20post%20#4](http://ubuntuforums.org/showthread.php?t=1861669%20post%20#4)

---

### Post by LanceRooke on 2011-10-20
gabe@gabe-Inspiron-1501:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


This is what comes after I enter the rfkill list.  Now what?  What does it mean and what do I have to do?

---

### Post by LanceRooke on 2011-10-20
Ok! We figured it out!  Your solution helped but was not entirely complete.  We installed the correct drivers, uninstalled the default drivers and then blocked the blacklisted BCM43xx (thereby unblocking the device). Then it was just a matter of using the function keys to turn on the wifi.  Now it works perfectly, but brings me to a new question:  How do I get Ubuntu to scan for available wifi?  So far it seems the wifi connections can only be set up manually.

---

### Post by Nate89 on 2012-01-22
> **garvinrick4 said:**
> With your wired connection install the marked packages below in screenshots.
Anything else remove the package. Then take wired out and reboot.
Notice I used synaptic and what is typed in search window. If still does not work
type this in a terminal and post, lots of good network card users around here: 
```
rfkill list
```

This worked like A CHARM FOR MY DELL INSPIRON 1501 THANK YOU.:D

---

### Post by LanceRooke on 2012-01-23
Actually, the solution in the jpegs works like a charm on My 1501 also.  I don't know why I had so much trouble the first time.  Now it's something I can set up in probably less than a minute.

---

