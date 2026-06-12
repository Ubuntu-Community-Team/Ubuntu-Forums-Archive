---
title: "MythtvRemoteTrouble"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by Earlofnecromium on 2007-03-28
This entry refers to this wiki [URL="http://www.mythtv.org/wiki/index.php/MCE_Remote"]
Ubuntu 6.10

HI, I'm using a MCE usb remote (oldversion). I have managed to install the drivers for the remote/ir receiver but i can't get it to work with mythtv. I have Made a lircrc file(just modified a few buttons on the lirc_mceusb2 lircrc file) and put it in both /etc/lirc/lircrc and /home/mythtv/.mythtv/lircrc. I have configured Mythtv keys as the lircrc file said to do. I have not however been able to get the modules/lircd to load on boot or get any buttons to work with Mythtv. 

To get IRW to work i have to  

[INDENT]sudo modprobe lirc_mceusb

sudo lircd -d /dev/lirc/0

irw
[/INDENT]

Any help would be greatly appreciated.

---

### Post by majoridiot on 2007-03-30
instead of trying to fix a non-ubuntu specific installation, you are likely better off starting fresh with
an ubuntu-specific install.

follow this guide: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy) and you should be up
and running in no time.

i can confirm that the guide works perfectly for both the old-stlye (card-connected) remotes as
well as the USB style.

---

### Post by Earlofnecromium on 2007-04-01
Lircd now works with mythtv, everything except the back button and i think that's something i did. Thanks alot man. Still don't know how to get all the modules and stuff to load on boot but i probably just missed something. Thanks alot.

---

### Post by majoridiot on 2007-04-02
> **Earlofnecromium said:**
> Lircd now works with mythtv, everything except the back button and i think that's something i did. 

make sure the name of the back button in your lircrc matches the name in they mythtv section 
of /etc/lirc/lircd.conf (case sensitive)

> **Earlofnecromium said:**
> Still don't know how to get all the modules and stuff to load on boot but i probably just missed something.

do:

```
$ ls -l /etc/init.d/lirc
```

is it there? if so, post it, as well as a copy of your /etc/lirc/hardware.conf

---

