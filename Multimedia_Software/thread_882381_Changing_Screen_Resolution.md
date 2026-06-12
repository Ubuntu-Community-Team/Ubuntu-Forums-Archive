---
title: "Changing Screen Resolution"
date: 2008-08-06
forum: Multimedia Software
---

### Post by mewilh0 on 2008-08-06
Can anyone help me?  I have tried all of the ways to change the screen resolution on this site.

My latest is gksu displayconfig-gtk but I can't find a combination of video and monitor driver that works.  I keep getting this error:
on_button_test_config_clicked()
xauth:  creating new authority file /tmp/dcg-GNwdhH5510/xauthority
Got pid 7460
(0, 0)
checkpoint 1
None
False
Sorry, this configuration video card driver
and monitor doesn't appear to work:

Messages from the X server:
(EE) open /dev/fb0: No such file or directory
(EE) No devices detected.
Fatal server error:

When I run sudo dpkg-reconfigure xserver-xorg it says xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080806224653
and I never get to the video screens.

Any clue what I have done?  I have a hercules 3D prophet 4500 video card with a viewsonic g773 monitor if that helps.

Thanks

---

### Post by wolfen69 on 2008-08-06
try
```
sudo dpkg-reconfigure -*phigh* xserver-xorg.
```
then you need to restart x or reboot.

---

### Post by mewilh0 on 2008-08-07
I still get the same warning:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080807181954

I restarted X and rebooted.  

Thanks for your help.

---

