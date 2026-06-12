---
title: "Trying to mount NAS (Caddy +  HDD) getting mount error(12): Cannot allocate memory"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by oceanexplorer on 2010-03-30
Hi,

I have a Network Attached Storage device which is a hard drive + caddy. I can access it fine using smb://192.168.0.2/Storage, I can map a network drive in Windows and I can also mount through gnome. However I want to permanently mount it, I have added this to /etc/fstab

//192.168.0.2/Storage   /media/storage        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

All I get after sudo mount -a is

[COLOR="Red"]**mount error(12): Cannot allocate memory**[/COLOR]

Driving me a little nuts, is anyone able to help? Most of the past posts focus on a full windows machine being the server but mine is just a caddy + hard drive with a web interface.

Thanks in advance

Paul

---

### Post by oceanexplorer on 2010-04-10
*Bump*

---

### Post by EddieO2 on 2010-09-06
This has been annoying me for a while - I finally *really* needed to get this to work (setting up a Firefly media server).

After a bit of searching, I found that you need to add "nounix" to the options:

```
sudo mount -t smbfs //host/share /mountpoint -o nounix,iocharset=utf8

//192.168.0.2/Storage /media/storage cifs nounix,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77 0 0

```

Original here:
[http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg26923.html](http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg26923.html) 

):P

---

