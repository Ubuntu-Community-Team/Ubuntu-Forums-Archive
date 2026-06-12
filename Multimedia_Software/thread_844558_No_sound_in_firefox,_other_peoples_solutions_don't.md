---
title: "No sound in firefox, other peoples solutions don't work."
date: 2008-06-29
forum: Multimedia Software
---

### Post by MadnessRed on 2008-06-29
I have already googles this and the solutions given don't work for me

Ubuntu 8.04 - Clean Install from shipit cd
Intel P4 (32bit)
Realtek AC-97 codec
-Other sound cards, - ATI 3850, - Bluetooth Audio
Firefox 3.0

Most of the time sound doesn't work in firefox, no flash applications will play sound.

First tried > sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1


> madnessred@anthony-desktop:~$ sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
madnessred@anthony-desktop:~$

Then found this.

>  mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old



> madnessred@anthony-desktop:~$  mv ~/.asoundrc .asoundrc.old
mv: cannot stat `/home/madnessred/.asoundrc': No such file or directory
madnessred@anthony-desktop:~$ sudo  mv ~/.asoundrc .asoundrc.old
[sudo] password for madnessred: 
mv: cannot stat `/home/madnessred/.asoundrc': No such file or directory

And sound still doesn't play??? It works occasionally though which is what is annoying.

---

