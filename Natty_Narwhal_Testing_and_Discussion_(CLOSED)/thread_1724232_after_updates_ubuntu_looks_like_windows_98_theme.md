---
title: "after updates ubuntu looks like windows 98 theme"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jardo on 2011-04-08
hello!
today i made updates on my ubuntu 11.04 and after reboot...now i have windows looking like windows98 ...i tried to change themes but it didn't help...
is it a known bug?
greetings!

---

### Post by dino99 on 2011-04-08
i've not seen any change except the new weird games style

---

### Post by jardo on 2011-04-08
thanks for replying!
i didn't made any update since two or three days...in the update list i saw something about kernel update infact the total update was about 120Mb

---

### Post by Harry33 on 2011-04-08
> **jardo said:**
> hello!
today i made updates on my ubuntu 11.04 and after reboot...now i have windows looking like windows98 ...i tried to change themes but it didn't help...
is it a known bug?
greetings!

This behaviour is still seen on certain setups.
The reason is that after login process the gnome-settings-daemon is closed and the system cannot start a new gnome-settings-daemon session when desktop starts.
There was an update to the package gnome-settings-daemon a while ago, but it did not fix all the cases.

Did you just upgrade the package gdm (2.32.1-0ubuntu1)?

Here is bug report (649809):
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

---

### Post by jardo on 2011-04-08
> **Harry33 said:**
> This behaviour is still seen on certain setups.
The reason is that after login process the gnome-settings-daemon is closed and the system cannot start a new gnome-settings-daemon session when desktop starts.
There was an update to the package gnome-settings-daemon a while ago, but it did not fix all the cases.

Did you just upgrade the package gdm (2.32.1-0ubuntu1)?

Here is bug report (649809):
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

thanks for helping! 
unluckly i'm not so expert in ubuntu, by the way i checked in synaptic package manager what version of gdm is installed,
and there is just  2.32.0-0ubuntu15

by the way, yes i see the same desktop theme as in the bug on lunchpad

---

