---
title: "Network connection"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by fred12345 on 2006-04-25
Hi

I am new to Linux and have a problem with networking between XP and Ubuntu.

I have access to the internet and have access from Ubuntu to XP, that is all fine. What I can`t do is log on to the Ubuntu computer from XP. I can see the Ubuntu computer, but no matter what username and password I use, I still can`t get in. I have configured the root account and another, I am able to log in to these ok, but not over a network. 

I have attempted to share the folders, but still I can`t get in. I don`t know what username and password it is looking for, what I have found is that if I look for computers on the network, it finds the pair of them. If I try to access the Ubuntu drive from the Ubuntu computer, I can gain access by not typing anything in the username and password boxes, but XP will not allow me to do that from that computer.

I have tried webmin, but could not get past the login screen. I have set the address as a static address, named the network, named the computers etc. But can`t gain access to the Ubuntu drive over my network.

Any advice please.

Thank you
Fred

---

### Post by mjm115 on 2006-04-25
I take it that you do have samba installed, right?  You may have your security level set a little high.  Try changing it from share to user and see if that helps.  Also, have you tried the username and password that you use for Ubuntu?

---

### Post by fred12345 on 2006-04-25
[QUOTE=mjm115]I take it that you do have samba installed, right?  You may have your security level set a little high.  Try changing it from share to user and see if that helps.  Also, have you tried the username and password that you use for Ubuntu?[/QUOTE]

Yes I have installed Samba, I have tried my root login and other user login details, but it doesn`t work for me. 

I have tried the following:

sudo gedit /etc/samba/smb.conf 
then changed security = user

That did not work for me.

What is confusing me, is that I know my login details and have tried those and they don`t work. I can just login to the various accounts, look at the internet and see, (and login) to my XP computer from Ubuntu, but not login to Ubuntu from XP.

---

### Post by mjm115 on 2006-04-25
try <username>@<name of ubuntu box> as your user name.  It may sound strange, but I have had that work on a couple of diffrent occasions.  If that doesn't work, then I want you to paste the contents of your smb.conf file please.

---

### Post by Iowan on 2006-04-25
You've set up a Samba user and password (via smbpasswd)?

---

### Post by fred12345 on 2006-04-25
[QUOTE=Iowan]You've set up a Samba user and password (via smbpasswd)?[/QUOTE]

Thanks for your replies (mjm115 & Iowan).

I have got it to work with a combination of:

smbpasswd, setting security back to user and also removing root from invalid username list!

I had ran the sudo passwd command, but was unaware of smbpasswd command.

Thanks for your help.
Fred

---

