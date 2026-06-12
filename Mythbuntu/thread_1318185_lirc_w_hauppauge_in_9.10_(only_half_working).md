---
title: "lirc w/ hauppauge in 9.10 (only half working)"
date: 2009-11-07
forum: Mythbuntu
---

### Post by bkn on 2009-11-07
After reading through dozens of posts regarding lirc and hauppage remotes (w/ hvr-1600) I was able to get the remove half functional. In particular, the buttons in the middle of the remote below the Volume+/- and Channel+/- and Mute buttons; so Pause, replay, skip, forward, backward, back/exit do not work. 

This is the remote that i have. 
[http://lirc.sourceforge.net/remotes/hauppauge/PVR-350.jpg](http://lirc.sourceforge.net/remotes/hauppauge/PVR-350.jpg)

has any one been able to get this style remote fully working on 9.10?

Thank you.

---

### Post by whistlerxj on 2009-11-08
I knew I should have kept the original lirc file during the upgrade from 9.04 to 9.10 tonight.

I cannot get any buttons my remote (just like yours) to work.

I see the remote, model 350, in the lircd.conf.hauppauge file, but it doesn't work

---

### Post by bkn on 2009-11-08
I was able to get it half working using these instructions. Perhaps it'll help you, 

[http://www.uluga.ubuntuforums.org/showpost.php?p=8257616&postcount=27](http://www.uluga.ubuntuforums.org/showpost.php?p=8257616&postcount=27)


However, like i said above, many buttons still didn't work. You can't navigate through mythtv without the back/exit button working. Also irw doesn't seem to work at all either. If i run irw i can get no output even when pressing buttons that i know work on mythtv.

---

### Post by SiHa on 2009-11-08
I think you'll find the problem is that the remote is being recognised by the kernel as a HAL device. In this case you will get some of the buttons (arrows, OK, numbers) recognised by the kernel, but irw won't respond. If you open a terminal window, and press the buttons - do they show up?

In this case, the buttons that do work, will work in Myth, as the kernel sees them as keypresses on the keyboard.

I can't tell you how to fix it, but there's quite a bit of stuff on this forum about it.

---

### Post by whistlerxj on 2009-11-08
how can i tell if its recognized as a HAL device?

in cat /proc/bus/input/devices
my lirc is not listed as an input

it was just fine on 9.04 until last night's upgrade to 9.10

---

### Post by SiHa on 2009-11-09
> how can i tell if its recognized as a HAL device?
Easiest way is to open up a terminal, and press the number buttons. If you get numbers echoed to the terminal then it's being seen as a HAL device. If not, then it's just a case of sorting out your lirc config.

---

### Post by utar on 2009-11-09
I have that remote working on my Nova T-500.  Although I actually give up but then it started working after a reboot!

Using mythbuntu control centre to select your remote and then make sure you are using the right event number.  You can do this by "sudo cat /dev/input/event0" then press buttons on the remote and see if anything appear.  Increase 0 to 1 then 2 etc until it works.

Your config file will then need to be edited to use the correct event number.

If not all the buttons are working in myth you will need to edit the myth lirc file, look in /home/your user name/.lirc/

You will need to restart Myth if you make any changes to this file.



Utar

---

