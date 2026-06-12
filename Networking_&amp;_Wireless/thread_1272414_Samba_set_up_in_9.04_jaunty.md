---
title: "Samba set up in 9.04 jaunty"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by mr_shedges on 2009-09-22
Ola,

I have been trying to set up samba sharing on my dual boot. I have auto mounted all of my drives and have installed a number of additions like wine, launchy, chm viewer, torrent apps, prism apps, firestarter (but do not have autostart on it, virtual box, vmserver, avidemux, project tools and adobe flash player. I think that about covers it.

I tried the following

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")#-o
then
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")#-o

all to no avail. I then thought try a fresh en. So I installed a fresh jaunty install in vmplayer on my windows machine and followed the tutorial on 

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

Every thing worked swell. all good.:)

So back to my real machine, tried to remove samba and re-install but nothing still no go. I am also followed the following thread

[http://ubuntuforums.org/showthread.php?t=994516]("http://ubuntuforums.org/showthread.php?t=994516")#-o

no matter what I follow I get the following

> 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.#-o

I am lost. Please any help would be great.

I am totally displectic so it is possible that I missed something but

sudo apt-get install samba
sudo apt-get install smbfs
right click your folder select > share options
tick the > Share this folder
click > OK
then it should be done
goto places>network> heay presto should be there.
but no.

Cheers all,
Scott:confused:

---

### Post by emarkay on 2009-10-07
Did you get it working?

---

### Post by mr_shedges on 2009-10-07
in short no, I have some how got my d key to call the change title dialogue box in terminal so I can no longer type most commands in terminal. I am trying to fix this issue then once that is fixed I will move back to the samba issue.

---

