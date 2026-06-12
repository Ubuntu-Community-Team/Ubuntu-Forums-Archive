---
title: "Getting MythTV and LIRC to work."
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by DAXP on 2007-01-21
I have a Hauppage PVR-500 card. IVTV sees it, but when I try the test command it only gets static. Not sure if it should. <_< I used a USB-UIRT for changing channels on me cable box when I used Windows, and used a Snapstream Firefly remote..as a remote. Not quite sure what to do in LIRC. =/

As for MythTV...well, I know I followed all of the directions in the UbuntuWiki howto ([https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop) going to other links when needed), but I'm still stuck on something. It says it can't connect to the database when I do the mythtv-setup command. There were commands listed in the howto to fix this (```
mysql -u root mysql

mysqlcheck -r -u mythtv -pmythtv mythconverg

UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';

FLUSH PRIVILEGES;

quit
```)
..but they didn't work. I noticed it said something about setting a password for the user mythtv, so I tried changing the password for it (in the mythtv-setup command) to PASSWORD.  Didn't work. What am I missing? <_<

---

