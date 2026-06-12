---
title: "Screen resolution swap"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by WoosterB on 2008-04-05
I have a problem with the login/GUI for 7.1

A while back I tried a dubious method for getting my X-Fi sound card to work, only to have my graphics drivers (8800gtx) go away (169.12).  I reinstalled my drivers and got everything to pre-sound trial conditions.  

For some reason, the login kicks in at a different resolution (1280x1100 or something).  When I log in, the screen stays the same in the GUI.  I then "change resolution" back to 1440x900, but no change.  I restart and the login window is again the wrong resolution **BUT** the GUI environment is 1440x900.

So....when I start up to Linux, I have to now reset my resolution and then restart the computer before the appropriate resolution takes over.  

What am I doing wrong/missing/should do?

Thanks!
-W

---

### Post by warp99 on 2008-04-05
If you want to login at 1440x900 open a terminal and do the following:

```
sudo gedit /etc/usplash.conf
```

replace the resolution to the following:

```
# Usplash configuration file
xres=1440
yres=900

```

save then close the file and issue the following command:

```
sudo dpkg-reconfigure usplash
```

This we create a new initrd.img which will set the resolution in usplash and your bash sessions to 1140x900. The reason that your resolution goes to 1440x900 is because you reloaded the xserver by logging out and back in again.

---

### Post by p_quarles on 2008-04-05
Moved to Multimedia & Video.

---

### Post by WoosterB on 2008-04-06
I'm familiar with the process above.  Basically we are editing the reconstructing the usplash configuration for the right resolution, however......

a restart of the computer (following those codes by the letter) still comes up at 1280

A quick recheck shows 1440x900 in the config file but there it was, 1280 and all.

Anything else that I'm not setting?

-W

---

### Post by warp99 on 2008-04-06
Did you try 'sudo dpkg-reconfigure xserver-xorg' and reset the resolution this way? When xserver  loads GDM (login manager) it sets the resolution per the settings in your xorg.conf, so set the highest resolution to 1440x900 when you reconfigure the xserver since 1280x1100 is a higher resolution then 1440x900. Remove the resolution 1280x1100 from the list presented. If that does not work we'll have to manually edit you xorg.conf file.

FYI when you login any resolution you set through the GUI desktop tools if you didn't have to enter a sudo password at some point it will be 1440x900 only for your desktop because it is only set locally, i.e only your share.

---

