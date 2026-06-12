---
title: "lirc problems with hauppauge hvr-1600"
date: 2009-08-29
forum: Multimedia Software
---

### Post by jt_04 on 2009-08-29
I'm trying to get my remote control to work under ubuntu 9.04.  When i run the command "cat /proc/bus/input/devices", I can't see anything resembling an IR device, only my keyboard, mice, USB receivers, power buttons, etc.

When I run "sudo lircd -n" and start irw in a separate terminal, i get the output: 

> lircd-0.8.4a[27179]: accepted new client on /dev/lircd
lircd-0.8.4a[27179]: could not get file information for /dev/lirc
lircd-0.8.4a[27179]: default_init(): No such file or directory
lircd-0.8.4a[27179]: Failed to initialize hardware
lircd-0.8.4a[27179]: removed client

also, when i run "sudo /etc/init.d/lirc start", i get the output:

> * Starting remote control daemon(s) : LIRC       [fail]

oh, and "lsmod|grep lirc" returns nothing.  I followed the [instructions located here]("http://www.mythtv.org/wiki/Ir-kbd-i2c") to use the "ir-kbd-i2c" kernel module, but I have no idea what that did to my system or if it is interfering with lirc.  "lsmod|grep ir-kbd-i2c" returns:

> 
ir_kbd_i2c             17552  0 
ir_common              56068  1 ir_kbd_i2c

does anyone have any suggestions?  even an explanation of what "lsmod" is doing or what the "modprobe" command does would be great.  i looks like lirc doesn't even know there is an IR receiver plugged into my card.  When I installed lirc, i chose "Hauppauge TV card", according to some guides I read.  

any pointers would be awesome.

thanks,
jt

---

