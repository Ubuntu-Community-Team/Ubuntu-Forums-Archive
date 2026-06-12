---
title: "join ubuntu on a windows workgroup"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by Taheer Amad Mitha on 2011-10-27
I need to join an ubunto 10.04 to a windows network workgroup and create a shared folder on ubunto with samba visible on windows pc .The Ubunto pc must conect with to netorks wirless and wired network( the wirless network with workgroup: workgroup,IP: 192.168.1.x and the wired network with workgroup: delta, IP: 199.199.0.x, both with subnet:255.255.255.0).I installed samba on ubunto and follow all the steps to create a shared folder.
 
Problems faced:
 
1-when wired card and wirles card are on i cante acess internet trough my wirless network only if wired is off.
 
2-I Cant see this ubuntu shared folder or pc  on a windows pc  but from ubuntu pc I can see windows PC´s from both workgroup(from wired and wirless windos network) and i can´t access none of them.
 
objectives:
 
1- computer from both network can share data trough the ubuntu shared folder;
2-The ubuntu user must have acess to the wired network and be able to surf internet trough the wirless network.
 
PLEASE A I NEED HELP.

---

### Post by ratcheer on 2011-10-27
To fix the workgroup name, edit /etc/samba/smb.conf. It is in section [global].

For a great reference on getting Ubuntu and Windows networking together, see thread:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Tim

---

### Post by Taheer Amad Mitha on 2011-10-28
From Ubunto i can yhe see windows pc's on the network but from windows pc's (w7 or xp) i cant see ubuntu. im stuck any light please.

---

### Post by satanselbow on 2011-10-28
As stated above you need to ensure your linux box is in the same WORKGROUP as the windows machines.

---

### Post by ratcheer on 2011-10-28
The problem is probably the firewall on Ubuntu blocking connections from the Windows machines. To me, this is the most difficult part of filesharing. I finally gave up.

Tim

---

### Post by Taheer Amad Mitha on 2011-10-28
The Ubuntu is on the same workgroup with others win pc´s.Today was possible to copy some files on a win7 pc from my ubunto but still cant see the ubunto from win7.
tanks for the replies.

---

