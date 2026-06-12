---
title: "connect two Ubuntu machine through a switch"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by jbfriend on 2009-04-25
Is there a way to connect two Ubuntu machines through a switch? i have a Comcast connection thru a cable modem that runs thru a switch to one windows laptop and two dual boot Ubuntu 8.10/windows machines. i would like to be able to see the files on all 3 machines using Ubuntu 8.10.

anyone know if that is possible and how?

thank you

jack

---

### Post by Iowan on 2009-04-25
The switch isn't the problem. Filesharing between Ubuntu and Windows will need [Samba]("https://help.ubuntu.com/community/SettingUpSamba"). The client ordinarily comes with Ubuntu - although you *might* need Winbind. To share files FROM Ubuntu to Windows will require installing Samba-server (though sometimes just called Samba). Ubuntu-Ubuntu can use several methods - Samba, NFS, SSHFS...

---

### Post by inobe on 2009-04-25
hi i just gave someone advice on setting up samaba shares.


it's pretty easy, i have setup numerous machines.

[http://ubuntuforums.org/showpost.php?p=7147407&postcount=4](http://ubuntuforums.org/showpost.php?p=7147407&postcount=4)

---

