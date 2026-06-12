---
title: "MySql root accounts"
date: 2008-03-13
forum: Mythbuntu
---

### Post by BustedChicken on 2008-03-13
I found the following while trying to figure out why I can't diskless front end to work. 
Oh,  I am using a fresh install of Mythbuntu - Hardy

in syslog
```

Mar 13 17:24:34 hostname /etc/mysql/debian-start[5515]: Checking for insecure root accounts.
Mar 13 17:24:34 hostname /etc/mysql/debian-start[5519]: WARNING: mysql.user contains 3 root accounts without password!

```BTW - If you can tell me how to troubleshoot or why I am getting a file not found when I boot my diskless client, I would be grateful as well.

---

### Post by laga on 2008-03-14
Are you using the recent support for diskless clients in MCC? What 'file not found' error are you getting when you boot your client? Unless you provide the *exact* error messages, nobody will be able to help you.

---

### Post by BustedChicken on 2008-03-14
Being a network tech, I should have know to post better info, the error is PXE-T01and PXE-E38 on the client. The client and the server have the exact same hardware, less a harddrive on the client, and both are amd64s. 

I can post this in the diskless forum if I don't get it working. I have a somewhat complicated dhcp.conf and am sure it I just misspelled the file or pathname or something. 

I am more worried about the 3 'unpassworded' mysql root accounts. I am not near that machine right now so I can't see what the accounts are for, or if it is nothing to even worry about.

---

### Post by uopjohnson on 2008-03-14
It isn't a real big deal unless your backend is connected directly to the internet or your netowrk is unprotected/open.  I think the default is to create an unprotected root account.  There are three of them because mysql defines WHERE someone is coming from as well as WHO they are.  I image they are for root@hostname, root@localhost and root@% with % being the mysql wildcard.
You can set a new root password with:
```
mysqladmin -u root password NEWPASSWORD
```
which should change all three.

---

### Post by BustedChicken on 2008-03-14
Thanks for the info, it's not connected directly to the net, I was just concerned.

---

