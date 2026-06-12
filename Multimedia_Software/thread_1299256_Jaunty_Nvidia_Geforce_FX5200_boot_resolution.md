---
title: "Jaunty Nvidia Geforce FX5200 boot resolution"
date: 2009-10-23
forum: Multimedia Software
---

### Post by momist on 2009-10-23
Hi there,

I can't seem to find a way around this one, and none of the threads I've looked at here show me the way.

My system uses the Nvidia drivers 173.14.16 from the restricted repository, and I can set the resolution to 1280 x 1024 at 60Hz to suit my shiny new flat panel monitor.  However, everytime I reboot, it goes back to 1024 x 768.  I've tried deleting the xorg.conf file and running "sudo dpkg-reconfigure xserver-xorg", and running "sudo nvidia-xconfig" and saving the resulting xorg.conf file, without it changing the situation.  In fact, the old xorg.conf file showed the monitor as 1280 x 1024 already, but it always comes up in 1024 x 768 when I reboot.  

Can anyone point me in the right direction please?

Thanks,

---

### Post by momist on 2009-10-23
Solved:

This thread [http://ubuntuforums.org/newreply.php?do=newreply&p=7439622](http://ubuntuforums.org/newreply.php?do=newreply&p=7439622) showed me the way.  

In Jaunty there is now a hidden file ~/.config/monitors.xml which can be edited by the user with a text editor, and this cured my problem.

---

