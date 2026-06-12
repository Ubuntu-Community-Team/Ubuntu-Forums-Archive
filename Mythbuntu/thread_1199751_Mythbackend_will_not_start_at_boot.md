---
title: "Mythbackend will not start at boot"
date: 2009-06-29
forum: Mythbuntu
---

### Post by rswing on 2009-06-29
I am new to mythtv and ubuntu/linux in general. I have searched, but have been unable to find my exact issue and have tried solutions to similar issues without any luck.

I have a fresh install of Jaunty Mythbuntu 64 bit running. When I boot up, everything works, except for live tv. The screen just blinks when I select it. The only way that I am able to get it to start is if I run the backend configuration application, and then exit it. Somehow that initializes the live tv at the front end.

I did not have this issue with 8.04, only Jaunty. I am running the backend and front end on the same machine and I am using the HD homerun network tuner. Thanks in advance for the help!

---

### Post by crez79 on 2009-06-29
The problem is the HDhomerun isn't found when the backend starts. Search around for ways to make the backend start later in the boot process.

---

### Post by ian dobson on 2009-06-30
Hi,

Are you using DHCP for your IP configuation? If yes then that could cause your problems. If possible go over to using a static IP address and as crez79 try starting mythbackend abit later in the boot process.

The mythbackend process is started by a symbolic link in /etc/rc2.d. The link is named something like S24mythtv-backend where the number (24) is the order in which the program should be started.

Try changing the link to something like S90mythtv-backend (just change to the directory with cd then do a mv (move).For example:-

cd /etc/rc2.d
mv S24mythtv-backend S90mythtv-backend 

Regards
Ian Dobson

---

