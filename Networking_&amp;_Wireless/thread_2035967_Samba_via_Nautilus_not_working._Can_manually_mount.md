---
title: "Samba via Nautilus not working. Can manually mount as cifs."
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by vancouverite on 2012-07-31
Hello,
I just did a fresh install of 12.04, 64 bit and have a problem with Nautilus. A samba share that I used to connect to regularly on my LAN now does not work within Nautilus. When I click on the bookmark (or do it from scratch via File->Connect to Server) I get asked for username, workgroup and password. When I enter the credentials and press connect, the credentials window closes and then opens again, asking for the information again. This happens endlessly.

I can mount the share using 
```
sudo mount -t cifs -o username=user,password=pass //XXX.XXX.XXX.XXX/data_user/data /media/samba

```
and then go from there, but I'd like the GUI way to work too.

Any idea of what could be going on?

Thanks!

---

### Post by vancouverite on 2012-08-01
No one?

---

### Post by odinb on 2013-01-21
Know this is old, but in case someone finds this and do not have the answer.

Answer can be found here: [http://askubuntu.com/questions/134249/connecting-to-windows-7-shares-from-12-04](http://askubuntu.com/questions/134249/connecting-to-windows-7-shares-from-12-04)

---

