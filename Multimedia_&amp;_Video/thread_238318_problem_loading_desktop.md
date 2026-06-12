---
title: "problem loading desktop"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by somi38 on 2006-08-17
i changed my monitor,i have ubuntu dapper on my system
when i start my ubuntu all loading is successfully completed.
but desktop or page of username and password is not open system is still running.the monitor screen is black

please tell me what i do

---

### Post by Greycloak on 2006-08-17
Try reconfiguring xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

This should allow you to reconfigure the monitor.

---

### Post by somi38 on 2006-08-17
how can i give this command in terminal or command line 
monitor screen is completely black
nothing to do

---

### Post by Ziox on 2006-08-17
> **somi38 said:**
> how can i give this command in terminal or command line 
monitor screen is completely black
nothing to do

the basic steps:

boot up with the new monitor

then after the computer stops loading, hit ctrl+alt+f1

then enter your username

hit enter

then enter your password

hit enter

then enter the command sudo dpkg-reconfigure xserver-xorg

hit enter

then enter your sudo password

hit enter

then just hit enter for about say 20 times...(if the screen doesn't come up)

then after that numerous enters, enter sudo reboot

and just wait for the pc to reboot.

since you don't see anything on the screen, that was all guess work, so make sure you don't make any mistakes

---

