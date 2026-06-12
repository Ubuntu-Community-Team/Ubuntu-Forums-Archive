---
title: "OK I give up: Samba file/directory sharing HOW TO?"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by OM NOM NOM on 2010-08-01
OK folks I'm apparently completely stupid. I've been trying for what seems like forever to share a single directory with only two authorized users and I just can't get the permissions right. 

Running Ubuntu 10.04 desktop as home file/print server. 
Two users: chris and gretchen
Directory to share: Music
Music resides in chris' home folder. 

I'd like to have full access for these two users and no access for anyone else. The challenge is that the best I can get for gretchen is read-only. 

What i've done so far:
Created user accounts for each
Created Samba accounts with passwords for each
Created a group called "family" and added chris and gretchen to it
Assigned the family group to the Music folder.
Shared the folder giving read and write access to family group. 

chris seems to work ok but when gretchen access it from her snow leopard laptop she can't create a new folder. It should be noted that chris is also the admin account. 

Any idea as to what step I'm missing? Thanks in advance for any insight!

---

### Post by Iowan on 2010-08-01
One of the Samba guru's may have better information, but having the share folder under the home folder *might* be a potential issue.

---

### Post by vangli on 2010-08-01
> **OM NOM NOM said:**
> OK folks I'm apparently completely stupid. I've been trying for what seems like forever to share a single directory with only two authorized users and I just can't get the permissions right. 

Running Ubuntu 10.04 desktop as home file/print server. 
Two users: chris and gretchen
Directory to share: Music
Music resides in chris' home folder. 

I'd like to have full access for these two users and no access for anyone else. The challenge is that the best I can get for gretchen is read-only. 

What i've done so far:
Created user accounts for each
Created Samba accounts with passwords for each
Created a group called "family" and added chris and gretchen to it
Assigned the family group to the Music folder.
Shared the folder giving read and write access to family group. 

chris seems to work ok but when gretchen access it from her snow leopard laptop she can't create a new folder. It should be noted that chris is also the admin account. 

Any idea as to what step I'm missing? Thanks in advance for any insight!

Hey.

Try adding two more options to the share:

force user = uuuuu
force group = ggggg

where uuuuu and ggggg are username and user group.

you may also add something like

user list =  chris, gretchen

With best regards

Bent, Oslo, Norway

---

### Post by OM NOM NOM on 2010-08-02
Iowan - good thought, I'm starting to think that might have something to do with it as well. 

vanglii - thanks for the tip. I'll give it a shot and see if that clears it up.

---

