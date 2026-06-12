---
title: "File sharing between 2 Ubuntu Laptops?"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by johnmollaghan on 2010-02-19
How can I share files between two laptops, both running Ubuntu 9.04, home wifi network situation?

There seem to be lots of Samba type programs etc, but I just want to know the simplest most straight forward way.

What needs to be in installed on each machine etc...

Thanks.

---

### Post by trueno_ray on 2010-02-19
another option may be ftp server, e.g vsftp
[http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux](http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux)

---

### Post by johnmollaghan on 2010-02-19
Thanks for your reply but I am wondering if there is a simpler solution?

Is there any network neighborhood area in Ubuntu? Shared folders etc? Can folders be mapped permanently like in Windows?

How can I see the other Ubuntu machines on the network etc?

---

### Post by bikeboy on 2010-02-19
Open the file browser (nautilus), right click the directory you wish to share (eg. Public) and go to properties. You will see a tab called 'Share'. When you choose to share the folder by ticking the box, it should prompt to automatically install the necessary components (internet connection or Ubuntu CD required). Repeat for the relevant folder on the other laptop and they should be able to see each other.

There are a couple of ways to browse. You can click 'Places' > 'Network' and go from there, or what I sometimes find a little more reliable is 'Places' > 'Connect to Server'. Then select 'Windows Share' as the service type, and put the IP address of the other laptop in the 'Server' field. The other fields aren't strictly necessary. Once you get it working, you can bookmark the location with Ctrl + D, and the file browser will always have a shortcut there - much like mapping a network drive.

I'd advise against trying server (especially FTP) until you're a little more comfortable.

---

### Post by trueno_ray on 2010-02-19
but actually samba is pretty good once you setup and mount it on

If you think it's difficult with command mode, you can try [http://www.webmin.com/](http://www.webmin.com/)
that provide web interface to setup your pc.

on client site, just type one command to mount the folder
for detail, see [http://ubuntuforums.org/showthread.php?t=255872](http://ubuntuforums.org/showthread.php?t=255872)

ps: for share or store file globally, try [https://one.ubuntu.com/](https://one.ubuntu.com/)

---

### Post by johnmollaghan on 2010-02-19
> **bikeboy said:**
> Open the file browser (nautilus), right click the directory you wish to share (eg. Public) and go to properties. You will see a tab called 'Share'.

Thanks bikeboy, exactly what I was looking for. A little embarrassed that I didn't spot the "SHARE" on the context menu. I was expecting a much more complicated setup.

---

### Post by Whoopie on 2010-02-19
Hi,

[Giver]("http://packages.ubuntu.com/karmic/giver") is a quick and simple application to share files in your local network.

Best regards,
Whoopie

---

