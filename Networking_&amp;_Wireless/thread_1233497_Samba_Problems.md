---
title: "Samba Problems"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by Captain Fwiffo on 2009-08-06
Hey Everyone,

I have an ubuntu 8.10 desktop set up and I am trying to get samba working with several other OS X and windows machines.  I can see my share from all the remote machines, however I am unable to write to the share, I get a permission error.  The account that I am using to log in is in the group for the folder, and the permissions are 770.  Here is the relevant smb.conf file info

[share]
     comment = Private Share
     path = /share
     read only = No
     writeable = Yes

I can't quite figure out what I am doing wrong.  Any ideas.  It seems to be related to the fact that the directory is in the / directory as opposed to the /home/ directory since I tried sharing a folder from /home/ and it worked just fine.

This is the first time I have set up samba on an Ubuntu machine.

Thanks for the help,
Captain Fwifo

---

### Post by swerdna on 2009-08-07
> **Captain Fwiffo said:**
> Hey Everyone,

I have an ubuntu 8.10 desktop set up and I am trying to get samba working with several other OS X and windows machines.  I can see my share from all the remote machines, however I am unable to write to the share, I get a permission error.  The account that I am using to log in is in the group for the folder, and the permissions are 770.  Here is the relevant smb.conf file info

[share]
     comment = Private Share
     path = /share
     read only = No
     writeable = Yes

I can't quite figure out what I am doing wrong.  Any ideas.  It seems to be related to the fact that the directory is in the / directory as opposed to the /home/ directory since I tried sharing a folder from /home/ and it worked just fine.

This is the first time I have set up samba on an Ubuntu machine.

Thanks for the help,
Captain Fwifo
OK, it's probbaly like you said. Let's have a look at the permissions & ownership on the share. Run this command and post the results back here:```
ls -l / | grep share
```

---

### Post by Captain Fwiffo on 2009-08-11
Here are the results.
```

drwxr-xr-x   6 root root  4096 2009-06-23 13:34 share
```I tried changing the group to a group that included my login and the permissions to 775, but it still didn't work.

Captain Fwiffo

---

### Post by Captain Fwiffo on 2009-08-11
Just to test, I even set the owner and group to my login, and set the permissions to 777 and it still didn't work.

---

### Post by Iowan on 2009-08-11
**read only=** and **writeable=** are redundant - you should use either/or. Try inserting a **write list=username** or **valid users=username** line (substituting your username...) in the share definition.

Afterthought... dunno if capital letters for Yes/No makes a difference. Sample/default file uses lower case.

---

### Post by swerdna on 2009-08-11
This share:
> [share]
comment = Private Share
path = /share
read only = No
writeable = Yes
Allows access only to users who are entered in the Samba user database. So to enter the share users must login. When they do login they ar not the root user and they are not members of the group root. So writing is not possible. 

On the other hand, if they can enter without logging in, you have enabled the "usershare" functionality through the sharing facility in Nautilus (R-click --> Sharing options). If you have this running as well as the [share] stanza in smb.conf, then you'll be confused. If you have the Nautilus sharing going on the shared directory, go back to Nautilus and turn it off (just work with smb.conf).

Then in smb.conf, set the share like this:
```
[share]
comment = Private Share
path = /share
read only = No
```
Make the share to be owned by a normal Linux user; e.g. ```
sudo chown anthony:anthony /share
```and chmod it to 777 e.g. ```
sudo chmod -777 /test
```
And enroll all users into the Samba user database.

You might consider the administrative artifice of the "force user" property useful.

For the share above, plus the share with "force user" and for other forms, see this tutorial:
Samba Server and Ubuntu / Kubuntu: HowTo Configure a Professional File Server on a SOHO LAN: [Part II: Defining and Using File Shares (Services)]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

---

### Post by Captain Fwiffo on 2009-08-13
I tried changing the owner and group to include my login.  I also tried setting permissions to 777 and the write list and valid users options.  I changed the cases on the "writeable= yes" to make sure that a capital 'Y' wasn't causing my troubles.

The login user is in the Samba user database.

---

### Post by Iowan on 2009-08-13
You restarted Samba after these changes?

---

### Post by Captain Fwiffo on 2009-08-21
yes

---

### Post by Iowan on 2009-08-21
What's the current result of ```
ls -l / | grep share
``` (if it's changed since changing permissions.)
 Did you try the **write list=** in the share definition?

---

