---
title: "Broadcom 43xx in 11.04??"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by justincredibal on 2011-04-28
Well I am trying to install the b43 drivers since the default drivers are broken but with the new unity desktop I cannot figure out how.

Is there a guide for this yet? The sticky at the top of the forums seems to be for 10.10.

Thanks

---

### Post by naja on 2011-04-28
Hi
I have the same problem since Beta and i could not solve it yet.
i have bcm4311 which worked just fine in maverick but not in natty.
any help?
thank you

---

### Post by justincredibal on 2011-04-28
I was trying to follow the guide at: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

But I cannot do step 2: 
**Step 2.** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use.

No clue how to do this since the interface is different from 10.10 and there is no longer the normal menu at the top with system ect.

---

### Post by justincredibal on 2011-04-28
nothing??

---

### Post by naja on 2011-04-28
solved it!

download  bcmwl-kernel-source for maverick, install it after removing the natty version, after that click on your installed package in synaptic then package menu then lock version, so it doesnt updates it till it is solved.
[http://packages.ubuntu.com/maverick/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/maverick/i386/bcmwl-kernel-source/download)

got it from a bug report
goodluck

---

### Post by alt256 on 2011-04-28
Thanks! That worked for me too, after reboot (bcm4311).

---

### Post by drauger on 2011-04-28
Solved it in such way:

sudo apt-get -y install b43-fwcutter firmware-b43-installer

sudo mcedit /etc/modules 
(if you don't have mcedit in your system - replace it with nano, or another editor) add string "b43". Don't forget about carriage return at the end of file.

sudo depmod

Reboot. Working.

---

### Post by drauger on 2011-04-28
> **justincredibal said:**
> I was trying to follow the guide at: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

But I cannot do step 2: 
**Step 2.** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use.

No clue how to do this since the interface is different from 10.10 and there is no longer the normal menu at the top with system ect.

a panel at left - sign with magnifing glass that has a plus inside (it would be named "Applications" in english version, i guess), then in dropdown menu at right upper corner choose "System" (i guess in english version :) ) - here search for **Hardware/Additional Drivers**

---

### Post by Lucky8Media on 2011-04-28
Simplest way we have found:

[http://ubuntuforums.org/showthread.php?t=1742147](http://ubuntuforums.org/showthread.php?t=1742147)

---

