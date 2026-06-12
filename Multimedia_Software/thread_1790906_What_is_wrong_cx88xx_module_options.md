---
title: "What is wrong?? cx88xx module options"
date: 2011-06-25
forum: Multimedia Software
---

### Post by Fisher on 2011-06-25
I just don't know what is wrong!!
I just put on my pc a Prolink Pixelview MPEG 8000GT.
It's a conexant based capture card.
According to the driver's (cx88xx) manual page, I neet to pass a insmod option: card=66 to make it work
I am using Ubuntu 10.04.2 LTS all updated.
So, first I created a file named cx88xx.conf on /etc/modprobe.d/, containing the words options card=66.
No deal, I still keep receiving a message saying me to put a insmod option (seem on dmesg).
Tried to rename the file to cx88xx, no deal, tried cx8800, cx8800.conf, tried /etc/modules, the same stuff, tried to blacklist the card, no deal, get the same message in dmesg.
What I am doing wrong??
Is the driver's name wrong?? The file location?? The options??
I just don't know where to search more options!!

---

### Post by Fisher on 2011-06-25
Found a quick and dirty solution:
Added to /etc/init/module-init-tools.conf, just before the task statement, the line:
modprobe cx88xx card=66 

Worked fine, but, I'm afraid in an update this configuration may be lost.
Still searching for a better solution...

---

