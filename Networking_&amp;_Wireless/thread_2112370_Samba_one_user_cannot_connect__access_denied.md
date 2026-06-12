---
title: "Samba: one user cannot connect / access denied"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by beengone on 2013-02-04
This is not related to my other Samba thread. I'm working with a client to get a new user to access their Samba share on a 10.4 server. I'm using Webmin to manage this as well as SSH. 

I created the Linux account and synced the Ubuntu password to Samba. The user can SSH into their home folder file. That works fine. The user can list the folders but cannot access their home folder or the shared folder at /home/shared. I assigned the same Linux/Samba password as the user's Windows password. 

/shared is set to allow the 'users' group and I made the user's primary group 'users'. Everything I see in webmin shows me that this user is the same as the others except that the other users have 'pre-encrypted passwords' assigned and I just used 'standard password' for this user.

A related question that I just don't understand but think I've tried every possible way: when I connect to this share from a Win7 machine and am prompted for the user/pass I should leave the local machine's name as the domain, right? I've tried:

user
user@servername
user@serveripaddress
user@localmachinename
user@winworkgroup

All give permissions errors.

the output of 'cat /etc/passwd' shows the various user accounts are identical minus the account identifier. 

What am I missing?

Thanks.

---

### Post by beengone on 2013-02-04
I tested mapping the user to shared, but that didn't do anything useful. But, when I took that back off and restarted Windows (heh) I can now list folder contents but have no write access.  A step closer, but still need help.

EDIT: The user can write to their home directory, just not the main shared directory.

---

### Post by beengone on 2013-02-04
Big update. SSHed in as the user and found I don't have write permissions on the shared directory. 

Uses in the users group which has write access. What am I missing?

---

