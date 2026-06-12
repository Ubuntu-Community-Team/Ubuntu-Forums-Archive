---
title: "Zen X-Fi on Ubuntu Jaunty"
date: 2009-05-19
forum: Multimedia Software
---

### Post by iball8888 on 2009-05-19
I have been reading a ton of threads and tutorials but nothing is working for me. I have a Creative Zen X-FI 32GB.

I have the following installed.

Gnomad2 2.9.1 
libmtp 8 
Kzenexplorer
mtptools

Nothing works.  I even opened up libmtp8 and edited those things i was told to edit.  When i do sudo gnomad2 i can get the player into docked mode but then gnomad2 kind of crashes or freezes.  When do mtp-detect it make the player go into docked but then that also freezes.


PLEASE i really need help.

---

### Post by iball8888 on 2009-05-20
please help

---

### Post by iball8888 on 2009-05-21
please help

---

### Post by Crazy Skinny on 2009-05-27
Hi ibal8888. I'm also having problems conecting my Zen X-fi 16 GB with Jaunty. I have managed to avoid it for crashing. But it continues with some bugs, I can't copy files to it with any program like amarok or such.

I've copy this files to /etc/udev/rules.d :

45-libmtp8.rules
> LABEL="libmtp_usb_rules"

# Creative ZEN X-Fi
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

And:

LABEL="libmtp_usb_device_rules"
# Creative ZEN X-Fi
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
45-libnjb5.rules
> SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libnjb_rules_end"

# Creative Zen X-fi
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4162", MODE="660", GROUP="audio"

Now, if I try to mount it as root, the zen doesn't freezes and I can see all the files and reproduce them. But I can't transfer files to it with a program like amarok or gnomad2 and it doesn't recognice the covers of the files I transfer.

If anyone knows anything more....please Help!!!!

---

### Post by Crazy Skinny on 2009-06-04
Help !!!!!

---

### Post by m0ar on 2009-10-21
[http://www.centriment.com/2009/06/05/creative-zen-x-fi-on-ubuntu-904-jaunty-jackpole/](http://www.centriment.com/2009/06/05/creative-zen-x-fi-on-ubuntu-904-jaunty-jackpole/)


Fixed for me :3

---

