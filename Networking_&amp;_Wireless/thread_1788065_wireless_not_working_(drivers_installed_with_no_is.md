---
title: "wireless not working (drivers installed with no issue)"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by litspliff on 2011-06-22
i have a friend's dell inspiron e1505 that he wanted to have xubuntu installed on to replace windows.

the install went great (restricted sources enabled, b43 drivers installed automatically).

after install, i noticed that my wireless network wasn't showing up in the network manager widget. i also noticed that the wifi light on the cluster was dark. i decided to uninstall the b43 driver, run updates, reboot, re-install b43, reboot, and check again. 

no networks. no wifi indicator light on the cluster. 
network manager didn't even have a wireless section on the list.

i know my router was on and working, because i had another device conneced and working properly.

the F3 key has a wireless symbol, so i thought maybe i just needed to use the function+F3 to turn on the hardware, but no luck.

has anyone else had this issue? 
if so, how did you solve it? 

i sent him home with it so he could use it on the wired network at his home to get his work done, but i'd like to be able to get his wireless working.

any help would be greatly appreciated by both of us.

---

### Post by chili555 on 2011-06-22
Dell's often, not always, have a problem with the module that translates key presses, Fn+F3 in this case, to useful information that the kernel can act on, in this case, "Please turn on the wireless, Mr. Kernel."

Please ask your friend to open a terminal and do:```
lsmod
```Does he see the module dell-laptop? If so, let's remove it and see if the wireless works:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Does the wireless work now? If so, we can amend one file to make it persistent.

If it doesn't work, let's see:```
dmesg | grep b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

