---
title: "Need Help with networking. usernames &amp; passes"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by vlex on 2010-04-20
hey,

Im new to using Ubuntu and my current goal is to make a home server for my family to backup their files on so that its a bit more structured.

What i want to do is give each of my family members a folder to store their files in. what i want to know if its possible to give each of my family a username and password so when they type that into whatever OS they are using to access the files it will direct them to a folder for that specific username.

im not sure if this can be acheived but i thought id come here first. ive tried to use and configure Samba but i havent had much luck. Im using ubuntu Desktop 9.10.

I appreciate any help,

Regards,

VLEX

---

### Post by johngreth on 2010-04-20
You could make everyone a user on the server, then setup the server for ftp and let it use the local users as the ftp users. That way anyone could put things into their respective home folders from anywhere on the network. Then just put a shortcut on everyone's desktops to the ftp location.

I've tried samba, but it always has ended in a mess for me, so I gave up on it. That's why I switched to ftp. It's harder to set up, but I think it's more reliable.

---

### Post by vlex on 2010-04-20
can you provide a tutorial?

---

### Post by Iowan on 2010-04-20
[LDAP]("https://help.ubuntu.com/community/OpenLDAPServer") might be an option - but it seems a bit complicated for a simple file server. Samba should be an option, as well. There are a few How-To's on the forum (and elsewhere), but it can still be a bit tricky.

---

### Post by vlex on 2010-04-20
So try and go with samba? im jst completly lost with it. if i had a tutorial i am capable of following the instructions.

---

### Post by johngreth on 2010-04-20
More info about installing ftp here: [https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html)

If you can get samba to work, it is also a good option. I've just always had problems because my computers with windows have all kinds of crazy things making file sharing way more difficult than it should be. There is more info about samba here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
and here: [https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html)

Also, I thought LDAP was for users to log into a network from a network dependent terminal. Is it possible to log into an LDAP server after already being logged into a computer? Does it work with windows? If so this may be something I will look into for my self.

---

### Post by vlex on 2010-04-20
cool, ill give it a try and report back here. I also read somewhere about Samba gui. Anyone got any info on that? Also if anyones else has ideas. PLEASE help :D

---

### Post by Iowan on 2010-04-21
There are a few Samba How-To's around:
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://samba.netfirms.com/]("http://samba.netfirms.com/")
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")
[https://help.ubuntu.com/9.10/serverguide/C/windows-networking.html]("https://help.ubuntu.com/9.10/serverguide/C/windows-networking.html")
This should be enough to get you started... In addition, [howtoforge]("http://howtoforge.com/howtos/linux/ubuntu") usually has some "perfect server" articles for Ubuntu.

---

### Post by Iowan on 2010-04-21
There are a few Samba How-To's around - here are a few to get you started...
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://samba.netfirms.com/]("http://samba.netfirms.com/")
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")
[https://help.ubuntu.com/9.10/serverguide/C/windows-networking.html]("https://help.ubuntu.com/9.10/serverguide/C/windows-networking.html")

 In addition, [howtoforge]("http://howtoforge.com/howtos/linux/ubuntu") usually has some "perfect server" articles for Ubuntu.

---

