---
title: "nVidia 6200 problem....OOOOH Pls help!"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by Dan Kay on 2007-03-23
I installed a nVidia GeForce 6200 and booted up 6.10 and everything was fine.

Through Automix I installed "nVidia Driver" and rebooted.
Now I boot up to a BLACK SCREEN.
What do I do now??

Please help....:confused:

---

### Post by Dan Kay on 2007-03-23
Also, after the install I got a message something like this:

If the install experiences problems, go to the terminal and type:

sudo cp /etc/x11/xorg.conf_backup_200703231430 /etc/x11/org.conf

Please help.......I'm a nOOB!

Do I boot in a Safe Mode or something??

---

### Post by taurus on 2007-03-23
Sure.  Boot into recovery mode from GRUB menu and run this command at a prompt.

```
cp /etc/X11/xorg.conf_backup_200703231430  /etc/X11/org.conf
```
Remember,  it's **X11**, not x11 since Linux/Unix is case sensitive.  Then, reboot with

```
shutdown -r now
```

---

### Post by Dan Kay on 2007-03-24
still not working....help

---

### Post by Dan Kay on 2007-03-24
WOW.......I did some checking because I was paniced and typed:
**dpkg-reconfigure xserver-xorg**pressed...... enter,enter,enter,enter,enter....etc.........typed **reboot** and got my screen back....

**Man this is just too scary for me!**

I wish a nOOB could find an easy straight forward approach.

---

