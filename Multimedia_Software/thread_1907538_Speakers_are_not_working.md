---
title: "Speakers are not working"
date: 2012-01-11
forum: Multimedia Software
---

### Post by ManGAGA on 2012-01-11
Hi,
Im new to linux, installed 2 days ago & everything is working fine, except sound.
I can hear sound in headphones but not speakers..googled & checked many posts,solutions that made me confused,cuz i cant find out whats the problem.
The last thing i tried was Alsamixer & still nothing.
So can anyone help? Its really annoying to think that i have to put on headset foreveeeeer:shock:??
& Thank you in advance.

Edit: 

Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
Installed Ubuntu 11.10 32-bit on desktop(a bit old)..
Attached a file (alsa info) that i saw in other post, if it helps.

---

### Post by ManGAGA on 2012-01-12
No one can help?

---

### Post by gordintoronto on 2012-01-12
Installed Ubuntu 11.10 64-bit? On what brand and model of laptop/desktop? If you open a terminal window and enter the command:
lspci
one of the output lines describes your sound device. Please copy/paste it into your message.

It's a lot easier to help you when you provide facts.

---

### Post by ManGAGA on 2012-01-13
Bump

---

### Post by MoreOrLess on 2012-01-13
Usually, this is a matter of playing with a program called hda-analyzer and enabling some amp. [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

---

