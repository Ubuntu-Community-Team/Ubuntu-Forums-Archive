---
title: "Resolution problem - on Samsung 226BW"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by Sockie on 2007-04-10
I have a nice new Samsung 226BW and my second PC is an Ubuntu Box (connected to VGA not DVI) but Ubuntu 6.1 seems not to know about my monitor and the max resolution I can do is 1280x1024 :confused: 

Can I please have some help in configuring my monitor properly for Ubuntu? I'm really not a command line commando at all, just thought I'd mention it that's all. :-|

---

### Post by williammanda on 2007-04-10
Paste your xorg.conf file here and I will give you a couple of commands to use.
Thanks

---

### Post by Sockie on 2007-04-10
:KS  Thankyou, but how do I find this config file. I a complete noob.

---

### Post by Malac on 2007-04-10
Is the monitor working at all?
If so,  in a maximised terminal, type : ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
``` This will first backup xorg.conf that you have now and then bring up several options for configuring X.
If you don't know what the answers are to any of the prompts just press the [Enter] key and continue until you get to stuff related to the monitor.
When done, reboot and see if all is well.
If you can't  get into Ubuntu or anything else has gone wrong. then reboot.
If you have GRUB menu hidden press Esc, choose Recovery Mode,
login and type :```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` (Write this down before you do anything then you know what to type :) )
Reboot and you should be back where you were.

Hope this helps.

---

### Post by Sockie on 2007-04-10
> **Malac said:**
> Is the monitor working at all?
If so,  in a maximised terminal, type : ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
``` This will first backup xorg.conf that you have now and then bring up several options for configuring X.
If you don't know what the answers are to any of the prompts just press the [Enter] key and continue until you get to stuff related to the monitor.
When done, reboot and see if all is well.
If you can't  get into Ubuntu or anything else has gone wrong. then reboot.
If you have GRUB menu hidden press Esc, choose Recovery Mode,
login and type :```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` (Write this down before you do anything then you know what to type :) )
Reboot and you should be back where you were.

Hope this helps.

The Video Card is an intel onboard 845g wasn't sure what to choose though... So I chose VESA :(

---

### Post by Sockie on 2007-04-10
Ok went through the whole configuration, lets see what happens next. :popcorn:

---

