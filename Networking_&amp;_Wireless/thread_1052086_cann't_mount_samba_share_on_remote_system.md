---
title: "cann't mount samba share on remote system"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by 999alfred on 2009-01-27
I am having a problem mounting a smb share that is located on one ubuntu system on another ubuntu system, but it can mounted from a windows xp laptop.

layout:
system A, ubuntu host system with the share, cal it user1 home directory.
system B, ubuntu system that wishes to access user1 directory on A.
laptop, XP system

On laptop, workgroup DOGPOUND, right clck on network and then mount network drive. Type in A's ip,etc and select "login in as different user". Enter "user1" and user1's samba password, quit and then finish. Bingo, the user1's directory pops up on the laptop perfectly.

Now from B, the ubuntu system. Click on Places->Network and "Windows Network" appears. Click on it and dogpound appears, click on it and system A appears and click on that and the user1 share appears. Clack on it and I am asked for name, which I enter user1, just as on XP, domain I change MSHOME to DOGPOUND and the same password as I used on the XP system.
But, it pops up asking again, a couple of tries and it says you do not have access rights. I try domain dogpound, lower case, and no go,

System A smb.conf has 

   workgroup = DOGPOUND
   server string = Samba Server

   security = share
   encrypt passwords = true

   hosts allow = 192.168.1. 192.168.2. 127.
   browseable = yes

[user1]
   path = /home/user1
   comment = user1 home
   browseable = yes
   writable = yes

So, why can the XP system mount it and not the ubuntu system?

tj

---

### Post by Iowan on 2009-01-27
[Here]("http://ubuntuforums.org/showpost.php?p=6611650&postcount=4") is a post describing how to change workgroup on Ubuntu.  I doubt that's the problem, but worth a try.
When you say "the same password as I used on the XP system" I presume you mean the password for user1 on Samba... Security=share *should* make it a moot point.

You didn't mention the IP addresses of the two systems. My Samba Unleashed book shows the "hosts allow" entries separated with a comma: ```
hosts allow = 192.168.1., 192.168.2., 127.
```

---

### Post by 999alfred on 2009-01-27
Yes, system B is 192.168.1.xxx, so that is in range and thesmb.conf is pretty much he same I have used for a while on other systems, Slackware, etc.

tj

---

