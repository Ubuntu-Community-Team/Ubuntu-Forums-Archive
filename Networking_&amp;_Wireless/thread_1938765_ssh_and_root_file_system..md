---
title: "ssh and root file system."
date: 2012-03-10
forum: Networking &amp; Wireless
---

### Post by ultimbro on 2012-03-10
hi all, 
here's what i'm trying to accomplish

I want to access my mp3 files and others documents from my iphone so here's what I've done so far

-installed sftp client on iphone
-installed open ssh server
-was able to connect to my PC from my iphone 

but here's the problem... My mp3s are on another drive on my pc which mount at each start up in /media/(drive #)/

When I log in with a user from my sftp client on the iphone it log into /home/user/ folder and I cannot go back in tree

I guess this is a matter of giving permission to this same user to all the file on the system but I don't know how to do this 

I looked into /etc/ssh/sshd_config but there is nothing there I could see that give access to particular files.

I'm not familiar with the chroot command... is this the way to go ?? if so ... how? never used this before as i'm a linux user for only a year now

thanks for your help

---

