---
title: "autofs"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by stephenry on 2011-05-06
Hi,

I am attempting to mount a number of shared drives using autofs. Although the process appears to be deceptively simple, it does not work and I have no idea how to proceed. My company already uses autofs extensively and to set it up on my local Ubuntu 11.04 I copied the known working auto.master and associated files (verbatim) to my /etc/ directory. I have confirmed that the servers where the nfs shares are located are reachable, and it appears that the mount points have magically appeared where they are supposed to be (although they are empty). 

The problem is simple, the directories aren't being mounted (they simply don't exist). Can anybody give me some pointers? or even some advice on how to debug this problem.

Steve

---

### Post by stephenry on 2011-05-06
I forgot to mention, the auto.* files I copied originated from an archaic version of RHEL (version 4, perhaps?), but they look correct.

---

### Post by ddd-222 on 2011-05-06
I just set up autofs on 10.10 a few days ago. 

you haven't added much detail about what you want to do with autofs, so I will assume you just want access to the data, any working method is acceptable to you. 

First, I wouldn't use the files from RHEL4. revert them back to what they were originally.

Second, I will suggest you use indirect auto-mounting ( and i am assuming you are trying to mount nfs exports ).

In auto.master there is a file something like:
#/net /etc/auto.net

remove the comment so its like:
/net /etc/auto.net

then execute:

sudo /etc/init.d/autofs restart

now assuming your server is named:

myserver.mydomain.net

execute this:

ls /net/myserver.mydomain.net

you should see a listing like:

export

if so, try :

ls /net/myserver.mydomain.net/export

now you should see all of the available shares.

if you want to actually access them from your home directory and the export directory is called "sales_forecast" just execute the following:

ln -s /net/myserver.mydomain.net/export/sales_forecast ~/sales_forecast

now you have a link to that export in your home directory.

now you should be able to type:

cd ~
ls sales_forecast

or you cal also just type (as before):
ls /net/myserver.mydomain.com/export/sales_forecast

---

### Post by ddd-222 on 2011-05-06
deleted

---

### Post by ddd-222 on 2011-05-06
deleted

---

### Post by ddd-222 on 2011-05-06
deleted

---

