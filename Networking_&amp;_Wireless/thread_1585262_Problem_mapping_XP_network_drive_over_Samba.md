---
title: "Problem mapping XP network drive over Samba"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by tracyandskye on 2010-09-30
I have XP in a virtualbox.  I can access the Ubuntu server fine, but when I try to map the drive I get a prompt for a username & password.  In years of setting up & using XP over small networks, I never remember needing a username or password to map a drive to a local network.  I can only assume I have some security setting set differently but I can't figure it out.

I have another XP machine on the network that is mapped to the server shares with no problem.  Maybe it's a virtualbox issue?  Can't remember if I've had this working before through VB or not.

---

### Post by netopalis45 on 2010-09-30
you first have to make sure that you have the virtualbox guest additions installed (it should be in one of the menus) . then you have to add the share to the virtualbox server and then you should be able to map to the drive. 
if you are using a different username in virutalbox you will probably have to select the box that says "log on as a different user" or something of that nature (dont really remember what it is right now).

---

### Post by tracyandskye on 2010-09-30
Thanks for the reply.  I already have access to the shares, and the access is directly through Network Places so it doesn't seem like anything special I'm doing through VB.  It's just mapping the drive that's the issue.

---

### Post by netopalis45 on 2010-09-30
then you should be able to go to the tools menu in "my computer" and select map network drive, your ubuntu box should show up under the "microsoft windows network" and then you should be able to select which shared folder you want to select as the network drive. at least that is how mine worked

---

