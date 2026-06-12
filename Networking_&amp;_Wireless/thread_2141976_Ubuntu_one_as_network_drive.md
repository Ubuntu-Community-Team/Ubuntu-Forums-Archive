---
title: "Ubuntu one as network drive?"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by DenHeldert on 2013-05-04
Is it possible to map Ubuntu One as a network drive?
I would like to set this up, instead of having a local folder to synchronize.
(Actually, I already set up certain folders to Synchronize, I *also* want to map the storage space to a network drive.)

My goal here is to be able to drag-drop files inside of Dolphin without having to keep them locally after they uploaded.
In addition, it would be nice to be able to explore the drive locally within Dolphin.


Regards,


[SIZE=1]Ubuntu 13.04
KDE Plasma Desktop[/SIZE]

---

### Post by DenHeldert on 2013-05-04
OK, I made some progress.
Using [this]("https://one.ubuntu.com/help/faq/how-can-access-my-files-via-ftp-on-ubuntu/") guide.

In a terminal I ran

```
[INDENT] mkdir ~/u1ftp
 cd ~/u1ftp
 wget [https://launchpad.net/u1ftp/trunk/0.1/+download/u1ftp-0.1.zip](https://launchpad.net/u1ftp/trunk/0.1/+download/u1ftp-0.1.zip)
 ln -s ~/u1ftp/u1ftp-0.1.zip u1ftp
 python u1ftp

 [/INDENT]

```

And all works.

But I'm having trouble adding it as a startup entry, how to do that in the KDE Plasma Environment?
Hope someone can help.

---

### Post by sean-fitzpatrick on 2013-08-22
You can access startup programs in KDE by opening System Settings, clicking on the Advanced tab, and then choosing the Autostart entry. I had a bit of trouble getting it to work by creating the autorun entry directly, but it's possible I just made a mistake somewhere. 
I managed to get a setup which works though; I have a computer running Scientific Linux at work (part of a network run by a sysadmin, rather than my own machine that I have full control over) with KDE as my desktop. This should work on Kubuntu as well (although I think you can just use the UbuntuOne client in that case).

What I ended up doing was creating a .desktop file in my Desktop folder named U1FTP, containing the following:
[Desktop Entry]
Type=Application
Terminal=true
Name=U1FTP
Icon=/path/to/icon/icon.svg
Exec=python /home/YOURUSERID/u1ftp/u1ftp

(You can edit the file using Gedit; you can also set the icon by right-clicking on the file once you create it and going to Properties.)
I have that, along with a link to the bookmark to the Ubuntu One folder (created as per the instructions given in the Ubuntu One FAQ page) in my desktop folder, so both icons show up in the Folder View plasma widget. If I want to connect to Ubuntu One I first click the U1FTP icon, and then the folder icon.
You could probably also go back to the Autorun section in system settings and create an entry that points to the .desktop file you created, but I didn't bother with this step: I figure I'll only want occasional access to Ubuntu One, and this way the u1ftp script is only running when I need it to.

---

