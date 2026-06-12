---
title: "Newbie install of MythTV questions"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by gerick on 2007-01-24
OK.  Following [MythTV Edgy Backend Frontend Desktop]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop") instructions as best as I could, I got MythTV running mostly but with some issues. And I still have many questions.

The first one:
Nowhere in the instructions does it mention to relogon as the MythTV user.  Is the frontend process supposed to be ran as the main user?

---

### Post by fenian on 2007-01-24
There are two parts of this guide that I personally don't agree with.The first is running mythtv-setup as root,I believe it should be run as the mythtv user.The other issue  have has to do with MySQL this guide seems to advocate not setting a password for the root MySQL account
> 
You will be asked for the password to the root account of mysql. By default, there is no password.
Not setting the root password to MySQL is a huge security risk.

[http://dev.mysql.com/doc/refman/5.0/en/security-guidelines.html](http://dev.mysql.com/doc/refman/5.0/en/security-guidelines.html)

Adding these steps would make setting up mythtv a little more difficult but not exceptionally so.

---

### Post by ralyon on 2007-01-26
Personally, the first time I ran mythtv-setup was from the mythtv login. However, I now run both mythtv-setup and the frontend under my (or my wife's if she is logged on) user account and do not have any problems using it that way.

---

### Post by gerick on 2007-01-26
The writer of the "MythTV Edgy Backend Frontend Desktop" instructions has informed me that his intensions is that mythtv-setup be ran as the normal user (not sudo or root) and mythfrontend is also meant to be ran as the normal user.

---

### Post by SyvanX on 2007-01-26
If I remember correctly, if everything is setup per the instructions, the mythbackend process should be handed off to the mythtv user.  mythtv-setup should be run as your mythtv user.  You can then run mythfrontend from your normal user account and enter the required settings to connect to the backend.

---

