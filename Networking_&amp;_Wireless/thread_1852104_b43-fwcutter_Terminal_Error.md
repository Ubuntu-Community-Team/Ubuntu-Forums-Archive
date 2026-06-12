---
title: "b43-fwcutter Terminal Error"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by FormalRS on 2011-09-29
Currently trying to get wireless working on my laptop in Ubuntu 11.04.
Following this : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)   walkthrough.
When I type the   sudo apt-get install b43-fwcutter   command into the terminal it says : 

Reading package lists ... Done
Building dependency tree
Reading state information .. done
E: Unable to locate package b43-fwcutter

The same happens when I try the   firmware-b43-installer   command.

How can I solve this problem? Any help is appreciated.
Also I do have internet access on Ubuntu whilst doing this - I have the laptop hooked up with an ethernet.

---

### Post by praseodym on 2011-09-29
Try it like this:

```
wget http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by FormalRS on 2011-09-29
Thanks for the advice, will try it as soon as possible.

---

