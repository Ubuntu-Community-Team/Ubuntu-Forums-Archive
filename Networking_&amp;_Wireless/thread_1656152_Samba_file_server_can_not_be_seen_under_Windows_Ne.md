---
title: "Samba file server can not be seen under Windows Network and Mac Shared"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by BreadPaPa on 2010-12-30
Hi, there,

I am trying to setup my file server on a desktop under ubuntu 10.10. I have installed samba and modified smb.conf. But other windows and mac machines in local network can not see the ubuntu server in Network or Shared section. The ubuntu machine can see other computers in Network. I tried to ping ip of the ubuntu computer from other machines and could get response.

Something weird was that I did same thing and same configuration of smb.conf on my laptop ubnder ubuntu 10.10 and the file sharing worked smoothly. The only difference is that that the laptop has been running ubuntu for a while and has some applications installed like apache, mysql, etc.. The desktop was just fresh installed ubuntu but IMO just samba is enough to realize the file sharing function. Btw I did not edit firewall of my laptop so I think the firewall setting should be same between the laptop and the desktop.

Any thoughts? Thanks a lot in advance.. please help, I really need to get it done asap.

---

### Post by PatchesTheCaveman on 2010-12-30
If you have a firewall installed on the desktop, you'll need to open the ports for SMB (137-139 and 445).

---

### Post by Morbius1 on 2010-12-30
In addition to the firewall advice you got above it almost sounds like nmbd isn't running. Find out if it's running:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```

---

### Post by don_xvi on 2011-01-04
Not a bad tip, I had the same problem; nmbd was running, but I decided to restart it anyways and all of a sudden I can see the share.

---

