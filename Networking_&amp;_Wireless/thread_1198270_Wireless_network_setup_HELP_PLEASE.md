---
title: "Wireless network setup HELP PLEASE"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by eddieishavingago on 2009-06-27
I am trying to setup a home wireless network, and starting to get frustrated. :(
I don't really know much about networking nor samba.
At the moment I have four computers, PC A with XP and PC B, C and D with ubuntu 9.04 and samba package installed. So far, I can access a shared folder on the PC A from PC B, but not from PC C or D. I get asked for a user name and password, and I have tried all possible combinations of user names I have. They all have the same passwords, and the message I get is that it can't mount the location.
When using smbpasswd -a "user" to add users to the config file, do I have to add all four PC users on all computers? 
Why can I access PC A from PC B with no problems, but I can't from the other two?
I can't access PC B C nor D from PC A, (although I'm not too bothered about that).
I would like to be able to have read and write permission on PC A from the other three, and have read and write permission between PCs B,C and D. I DON'T want PC A to have read and write permissions on PC B, C and D.
I have never set up a network before, and my knowledge on the subject is quite restricted (as it is with many other computer related stuff).
I have seen many pages on samba configuration and network setup, but so far I still don't know what I'm doing wrong.
If anybody can redirect me to tutorials or comprehensive how to's that would be great. Suggestions on how I should proceed from beginning to end would also be fantastic.
Thank you.:D

---

### Post by mhgsys on 2009-06-27
(You wanted to have complete access to pc A right, then do this on pc A,)

The easiest way I know is to setup samba allowing everyone;
To do this open up your smb.conf.

```

sudo nano /etc/samba/smb.conf

```

Scroll down to section Authentication and add
```

security = share

guest account = nobody

invalid users = root

```

---

### Post by eddieishavingago on 2009-06-29
Thank you "mhgsys" for your reply, and pardon my delay in answering.
What you suggested, what does it exactly do? Does it allow free access to any user (even people I don't want to over the internet)?

By the way, PC A is running Win XP, not Ubuntu. PCs B, C and D run with Ubuntu.

Messing around last friday night, I managed to access PC A (windows XP) from all other three ubuntu computers, as I wanted, but only two at a time. If I tried to access PC A from a third computer while two where already accessing the shared folder, I would get asked for a password and user. If only one computer was connected to PC A, when attemping to access PC A from a second computer I wouldn't get asked for a password at all. This makes me ask myself (and anybody else too, of course), is there a limitation to the maximum number of users that can simultaneously access the shared folder on PC A???

And another question. Can I restrict the access to PC A so that ONLY PCs B, C and D can access the shared folder on PC A and nobody else??

THANK YOU!

---

### Post by eddieishavingago on 2009-06-29
Could anybody suggest a network setup tutorial for dummies? 
I find loads of information on the web, but I seem to be lacking some of the most basic concepts for understanding more complicated stuff.
THANKS!

---

### Post by mhgsys on 2009-06-29
yes, it allows every user. 

So maybe that's not what you want.

Maybe this will help you on your way ;

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

