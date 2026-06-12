---
title: "Samba"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by gabe17 on 2009-11-16
Hi, I am beginner in Ubuntu. I tried to install and configure Samba to be able to tranfer data between Ubuntu on my PC and Vista on my notebook (notebook is connected wireless to rooter and PC is connected wired to the same rooter, of course). I was doing it as it was written in a tutorial (I think it was also on ubuntuforums), but it couldn't go. I think it could be because the tutorial wasn't written for Samba4, Ubuntu 9.10 and Vista. Can somebody give me a link to a verified tutorial, or write a short step-by-step tutorial? Sorry for noob question and thanks for your patience. Gabe17.

---

### Post by Iowan on 2009-11-16
Which tutorial? The basics *should* remain pretty much the same. [This]("http://ubuntuforums.org/showthread.php?t=202605") seems to be the standard, but [this]("http://ubuntuforums.org/showthread.php?t=1169149") one covers some Vista stuff.

---

### Post by indiandruid on 2009-11-19
Hi gabe17 - Give this a try. Go to Synaptic, seach for samba-common-bin, 'Mark for Upgrade' and hit apply. You can use the Terminal also and type: 

sudo apt-get upgrade samba-common-bin

Upgrade other **installed** samba components if the option is available. Reboot if you wish.

---

### Post by gabe17 on 2009-11-23
I've done it as it is written in the first tutorial in Iowan post, but it can't work.  My PC with Vista can't connect to the Ubuntu PC.

---

