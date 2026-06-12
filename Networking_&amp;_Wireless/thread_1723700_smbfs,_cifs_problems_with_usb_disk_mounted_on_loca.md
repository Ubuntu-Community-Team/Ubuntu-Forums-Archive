---
title: "smbfs, cifs: problems with usb disk mounted on local network"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by mer0090 on 2011-04-07
Hello everyone,

I have mounted a 2 tera usb disk on my local network and sometimes happens that I dont see several files that actually exist on the usb disk. 

The strange thing is that if I access directly the disk with nautilus ("connect to server" command) everything is fine.

Here is my fstab configuration:

**********
//192.168.178.93/cargoalpha /media/wd-usb smbfs iocharset=utf8,credentials=/home/seba/.smbcredentials,gid=1234 0 0

//192.168.178.93/cargoalpha /media/wd-usb smbfs iocharset=utf8,credentials=/home/seba/.smbcredentials,dir_mode=0775,gid=1234 0 0

//192.168.178.93/cargoalpha /media/wd-usb smbfs iocharset=utf8,credentials=/home/seba/.smbcredentials,uid=1000 0 0

//192.168.178.93/cargoalpha /media/wd-usb cifs iocharset=utf8,credentials=/home/seba/.smbcredentials,gid=1234 0 0

//192.168.178.93/cargoalpha /media/wd-usb cifs iocharset=utf8,credentials=/home/seba/.smbcredentials,dir_mode=0775,gid=1234 0 0

//192.168.178.93/cargoalpha /media/wd-usb cifs iocharset=utf8,credentials=/home/seba/.smbcredentials,uid=1000 0 0

#//192.168.178.93/cargoalpha /media/wd-usb cifs users,noauto,credentials=~/.credentials,iocharset=utf8,uid=1000,gid=1000 0 0
**************

Can anyone help me?

Thanks,
Sebastiano

---

