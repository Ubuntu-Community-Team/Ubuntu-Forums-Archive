---
title: "Accessing domain's /net/"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by Deaner13 on 2013-07-31
Hey All,

I am trying to get some ubuntu computers to work with a domain. All of the Linux systems in the Domain are RHEL 4 or 5 and use LDAP as their means of authentication.

I can ping/ssh to machines from Ubuntu, but I am unable to cd /net/***computer_name***/ to access shares of the RHEL machines. I would assume its a matter of authentication, but I am not very well versed in Ubuntu and setting up networkng. Can you guys help?

Thanks!

---

### Post by zero2xiii on 2013-07-31
Ubuntu and red hat is NOT the same in file structure and system internals!

For your issue, please first make sure everything is mounted properly:
[https://help.ubuntu.com/community/AutofsLDAP](https://help.ubuntu.com/community/AutofsLDAP)
[http://forum.zentyal.org/index.php?topic=12925.0](http://forum.zentyal.org/index.php?topic=12925.0)

and if it still does not work, please provide a lot more detail. Including any errors you get.

Thanks

---

### Post by Deaner13 on 2013-07-31
I'll do some reading into these articles. But in the meantime I would like to elaborate.

When typing cd /net/***computer_name/*** I simply get a directory not found error. I'm not really where to start in fixing this, so I really appreciate the articles.

If you need any other information from me I'll be happy to give it to you in the mean time.

---

### Post by zero2xiii on 2013-08-01
Hay,

> When typing cd /net/computer_name/ I simply get a directory not found error. 
This is correct, you will receive this error because that directory, the entire /net/ tree actually, does not exist.

LDAP shares need to be mounted (well, at least in ubuntu) just like any other physical drive. Thus (for explanation's sake):
```
mkdir /net/192.168.1.2
mount ldap://192.168.1.2/some/path /net/192.168.1.2
cd /net/192.168.1.2
```
Is the basic idea.  (Please note the above will NOT work, it is simply for explanation)

The articles I linked to, explains you HOW to mount the LDAP shares. Thus, making them accessible. WHERE this happens is up to you. Most people, me included, prefer mounting things under "/mnt/device"

I have no idea how RHEL (which I assume stand for Red Hat Enterprise Linux) handles LDAP mounting, because I assume that is why you are looking for them in ubuntu under "/net/". 

Another option you might want to try is sftp. Again, I am not sure how this works with red hat, however under ubuntu you simply need to have a ssh server running on the machine you wish to access and then open up nautilus in one of these manners:
In terminal
```
nautilus sftp://192.168.1.2
#replace nautilus with your file manager if you use a different one
#this will open a dialouge box asking you for a user name and password
#this will be your SSH login username and password.
```

From GUI,
Open up any folder, home even.
Go to file > Connect to server.
Now select from the drop down box "SSH" (or LDAP if it is displayed, it is not on my system since I do not use it at all)
Fill in the details in the dialouge box and click connect.

That should do it.

You can make the sftp method permanent by adding to your fstab, however I will not go into that here since I am not sure if that is even what you want. A simple google will provide more than enough information regarding that.

Hopefully this clears up some of the issues you might have, including some alternatives and directions. If you have a more specific question you need help with, feel free to ask that question and we can help you.

Cheers and good luck!

---

