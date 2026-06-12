---
title: "Corrupted Xorg"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by DanMan_7 on 2007-03-17
Greetings All,
    I'm running a Geforce 7600Gt card.  I was running a working version of the nvidia driver and beryl quite successfully until i let my machine perform an update.  Now, when i reboot it tells me Xorg cannot initialize.  It seems whatever new nvidia driver came out won't work on my machine.  

Anyway, I reformated, reinstalled ubuntu, installed the nvidia driver, and boom i get the same failed Xorg thingie.  Can someone tell me how i use the terminal to re-establish my backuped Xorg file?  I know when you install the nvidia drivers it makes one, I just a newbie and don't know how to swap it back into action so i can boot again...
         Thank you kindly,  Danman_7

---

### Post by Efwis on 2007-03-17
boot into recovery mode, this will give you a prompt, at the prompt put in the same username you use to log into Ubuntu. give Password when prompted. After that, do the following to get the name of your backup file. It might not use a convential backup system Hit enter after each entry:

[code]cd /etc/X11 
dir
sudo cp /etc/X11/xorg.conf_backupfile  /etc/X11/xorg.conf
[code]
This will replace the xorg.conf with the working backup file. The dir command will allow you to find the backup file name so you can use the correct name. Also,  have you tried to update before installing beryl? it might be a beryl update that is crashing your system.

---

