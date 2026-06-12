---
title: "Accesing Files Remotely"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by Mercenary(FH) on 2009-09-15
So I just installed ubuntu 9.04 (w/e the newest one is)
Im not a complete newb at linux. just the desktop part of it (I know the commands lol)

With that being said I have looked all over google but keep getting the wrong things.

I have 2 computers, a laptop and a desktop at home with ubuntu 9.04 on them. At least I think it's 9.04......I used Wubi to install them both (seemed to work fine)

ANYWAYS
Basically I want a Folder on my desktop at home. that has files that I can access from my laptop (via ssh or w/e)
Basically I'd put files in here that I may need (Programming files/stuff I may forget and need at school)

I'd be accessing them from my laptop (which i use at My university) and be able to copy  them from the desktop to the laptop

I installed SSH on my computers, i'd obviously need to know the IP address of my home computer but I have NO clue what to do? I'd assume I set up a sharing folder on my desktop computer but then what? any help would be super greatly appreciated :) thxxx

---

### Post by nandemonai on 2009-09-15
Personally I'd go for sshfs.

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Essentially, on the server you just need ssh server running and on the client you need to install sshfs:

```
sudo apt-get install sshfs
```

On the client create a mount point and give it the right permissions:

```
sudo mkdir /media/mountpoint && sudo chmod username:username /media/mountpoint
```

mountpoint being the dir you'd like to mount to and username being your username.

Finally:

sshfs xxx.xxx.xxx.xxx:/home/username/folder /media/mountpoint

xxx.xxx.xxx.xxx being the IP address or hostname of the server followed by the share path.

:)

---

