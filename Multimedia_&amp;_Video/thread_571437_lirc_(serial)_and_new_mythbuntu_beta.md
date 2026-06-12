---
title: "lirc (serial) and new mythbuntu beta"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by mr_bungalow on 2007-10-09
Hi.  I'm a computer literate, yet linux newbie.  I have installed mythbuntu beta after I lost support for my old fedora core 4 installation (using Jarod Wilson's guide).  I really enjoyed the install process and went from installing the motherboard to a 95% functional system in less than 2 hours.  Great work on the installer!!

Anyways.. I have a serial receiver that I bought from Zapway (recommended by the Wilson guide).  When I did the mythbuntu setup there wasn't an option for any kind of a serial receiver.   I also use a harmony remote.  I can probably get that set up once I get the receiver working.  What options should I use to get this set up in mythbuntu setup?  When I shut down I see this error message:
```
 #####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
##################################################### 
```

I tried to do a apt-get install --reinstall lirc and it gives me the same error.  I don't see anything in dmesg and when I do a  ls -l /dev/l*I get ```
srw-rw-rw- 1 root root    0 2007-10-09 09:48 /dev/lircd
```.  
I tried following another guide and do a setserial but that command is not found.  

Do I need to do a recompilation of the kernel or something with the kernel sources?  I have no clue how to do this.  If anyone could push me in the right direction I would be extremely grateful.

Thanks in advance!

---

### Post by jimbodude21 on 2007-10-09
Try this:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

you will be using either lirc_serial or lirc_sir module, not the lirc_mceusb.

---

