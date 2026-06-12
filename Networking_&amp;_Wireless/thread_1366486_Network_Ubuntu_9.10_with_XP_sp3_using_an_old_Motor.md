---
title: "Network Ubuntu 9.10 with XP sp3 using an old Motorola VT2442"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by tuckeroil on 2009-12-28
Hey,

I am trying to network my XP laptop to my Linux desktop so they can share file, printers, etc. I am trying to network them across the VT2442 (the one that vonage gave us a while ago).  I disabled the DHCP. Not sure where to go from there.

Also, both computers are plugged into the LAN ports (not the internet port) but I can not access the web interface.  I guess I got lucky one time and was able to but now its not doing it. Any suggestions?

Thanks

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
hi to do that you will have to configure an app called samba so goto

applications -> accessories -> terminal and make sure you are root (admin)
if you are not type 

sudo su

then you account password if you cant do that then contact the sytem admin.if you are root then type

sudo apt-get install samba smbclient smbfs

now i need to know waht type of filesharing your gonna setup is it a workgroup (simple but hard to find shares) or a domain (like in schools like i use coz im 13)
plz tell me.
then i will guide you through what 2 do nxt

---

### Post by tuckeroil on 2009-12-29
> **headvampyre@hotmail.co.uk said:**
> hi to do that you will have to configure an app called samba so goto

applications -> accessories -> terminal and make sure you are root (admin)
if you are not type 

sudo su

then you account password if you cant do that then contact the sytem admin.if you are root then type

sudo apt-get install samba smbclient smbfs

now i need to know waht type of filesharing your gonna setup is it a workgroup (simple but hard to find shares) or a domain (like in schools like i use coz im 13)
plz tell me.
then i will guide you through what 2 do nxt
Thanks for the reply

Ok, I have Samba loaded and created the workgroup on the XP computer called "TRAVISHOME". The computers are connected to the VT2442

I think I forgot to mention that the computers are part of a wireless network but I want them to share files across the ethernet connection.

---

