---
title: "Video is stripped lines Dell 1501"
date: 2011-10-01
forum: Multimedia Software
---

### Post by paynek716 on 2011-10-01
I have a Dell Inspiron 1501 with video problems. Either before or after login I have vertical stripped lines. Pretty but not very userful. Here are some specifics:

[LIST]
[*]Ubuntu 10.04
[*]Grub 1.5
[*]ATI Radeon Express video card
[/LIST]

I know of the solution here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572521]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572521") but can't get to a usable screen where I can add "nomodeset" to the grub boot menu.

---

### Post by Toz on 2011-10-07
Hold down the shift key when you are booting and you will get to the grub screen. Press 'e' to edit the current kernel line. Cursor down to the line that contains the words **quiet splash** and add (separated by a space) the word **nomodeset**. 
```
...quiet splash nomodeset
```
Press 'Ctrl+x' to boot the kernel with the nomodeset parameter. This should get you a useable screen so that you can make the change permanent.

Reference link: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")

---

