---
title: "Myth Front End Hangs"
date: 2010-07-30
forum: Multimedia Software
---

### Post by MarkBM on 2010-07-30
Hi all,
I have MythTv installed & had it working wholly on the one machine. I also use this machine as a general desktop computer with Gnome. I recently tried using Mythmote from my Android 2.1 HTC Desire. I now have the frontend hanging with no menu with the gray background. Initially I could connect mythmote while it  was in this hang state then the front end just quit after about 15 seconds. I tried "mythfrontend --reset" in a terminal. Now the frontend hangs with a blank screen. Here is the the log output 

mark@mark-desktop:~$ /var/log/mythtv 
bash: /var/log/mythtv: is a directory 
mark@mark-desktop:~$ cd /var/log/mythtv 
mark@mark-desktop:/var/log/mythtv$ tail mythfrontend.log 
2010-07-30 22:57:29.039 MediaMonitorUnix::AddDevice() - empty device path. 
2010-07-30 22:57:29.040 MediaMonitorUnix::AddDevice() - empty device path. 
2010-07-30 22:57:29.045 NetworkControl: Listening for remote connections on port 6546 
2010-07-30 22:57:29.048 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Terra/menu-ui.xml 
2010-07-30 22:57:29.366 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml 
2010-07-30 22:57:29.372 Found mainmenu.xml for theme 'Terra' 
2010-07-30 22:57:29.413 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1) 
2010-07-30 22:57:29.414 Using protocol version 56 
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0. 
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab 
mark@mark-desktop:/var/log/mythtv$ 

Can anyone help with this fatal IO error if this would be the cause?
I have tried completely removing the frontend with synaptic, rebooting & re-installing. The problem persists with no change.
Thanks.
.

---

### Post by MarkBM on 2010-10-22
> **MarkBM said:**
> Hi all,
I have MythTv installed & had it working wholly on the one machine. I also use this machine as a general desktop computer with Gnome. I recently tried using Mythmote from my Android 2.1 HTC Desire. I now have the frontend hanging with no menu with the gray background. Initially I could connect mythmote while it  was in this hang state then the front end just quit after about 15 seconds. I tried "mythfrontend --reset" in a terminal. Now the frontend hangs with a blank screen. Here is the the log output 

mark@mark-desktop:~$ /var/log/mythtv 
bash: /var/log/mythtv: is a directory 
mark@mark-desktop:~$ cd /var/log/mythtv 
mark@mark-desktop:/var/log/mythtv$ tail mythfrontend.log 
2010-07-30 22:57:29.039 MediaMonitorUnix::AddDevice() - empty device path. 
2010-07-30 22:57:29.040 MediaMonitorUnix::AddDevice() - empty device path. 
2010-07-30 22:57:29.045 NetworkControl: Listening for remote connections on port 6546 
2010-07-30 22:57:29.048 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Terra/menu-ui.xml 
2010-07-30 22:57:29.366 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml 
2010-07-30 22:57:29.372 Found mainmenu.xml for theme 'Terra' 
2010-07-30 22:57:29.413 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1) 
2010-07-30 22:57:29.414 Using protocol version 56 
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0. 
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab 
mark@mark-desktop:/var/log/mythtv$ 

Can anyone help with this fatal IO error if this would be the cause?
I have tried completely removing the frontend with synaptic, rebooting & re-installing. The problem persists with no change.
Thanks.
.

By going into the disk utility under the system menu I was able to unmount "SDC" . This allowed the menu in the front end to be visible again. From the setup I was able to uncheck the box that asks to "scan all media"

---

