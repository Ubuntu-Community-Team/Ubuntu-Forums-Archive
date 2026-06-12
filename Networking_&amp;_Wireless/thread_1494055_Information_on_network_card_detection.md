---
title: "Information on network card detection"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by unxnut on 2010-05-26
I am writing to ask an academic question and hope that someone can help me.  I am running Ubuntu 9.10 and trying to understand how the OS recognizes the Intel network card.  I have gone through the system and understand that the module e1000e is needed to make network operational.  I tried to see where in the system does it insert e1000e by using modprobe or insmod but could not find it.
 
I also looked in initrd and noticed that e1000e is present there.  lsmod shows that this module appears early on but I cannot find where did Ubuntu determine that his module was needed and inserted it.  Can someone point me to the documentation to understand this?
 
I also noticed that e1000e does not have other dependencies and does not appear in the dependencies of any other module.  I take it that this module has been inserted by the time udev script runs in initrd.
 
Thanks a lot for your help.

---

