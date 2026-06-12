---
title: "able to see samba share from vista, not ubuntu"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by badperson on 2009-01-31
hi,
I have two machines, one dual booted with vista and ubuntu, the other is running upbuntu server (lamp). I created a samba share on the server, which I can see from the vista machine, but not ubuntu. 

In ubuntu, I go Network\Windows Network, and I am able to see the group I created in the smb.conf file, but I can't see any computers or folders under it. 

```
workgroup = JASONGROUP
```

should I just comment out that line? 

this is the relevant part of the smb.conf file...

```
[share]
comment = Ubuntu Server Samba Share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755
```

thanks for any help!!
bp

---

### Post by johnjohn2 on 2009-01-31
An easier way to set is open a terminal and type > shares-admin
This will then allow you to change and administer what workgroup you want
As well as what you want to share!

You could also give webmin a shot just google!

Regards john

---

### Post by badperson on 2009-01-31
hi,
this is from the client machine, not the server, right? 
bp

---

### Post by FishRCynic on 2009-01-31
you are just trying to browse the network with nautilus?

clicked on network and voila nothing there but windows network

---

### Post by badperson on 2009-02-01
was able to get to the folder by entering 
smb://<ip address> to view the shared foler...may not be the best way, but it works.
bp

---

