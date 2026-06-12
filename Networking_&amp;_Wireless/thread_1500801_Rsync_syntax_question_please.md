---
title: "Rsync syntax question please"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by Mongao on 2010-06-03
Hi all,

I`m trying to use rsync to synchronize my Torrents folder, in my local client PC, to a QNAP NAS server.

Please note that what I`m trying to achieve is something rather simple, I am at my home in a private network, no Internet transfer through complicated protocols. 

OK, I`ve seen on the Web many many rsync guides, but I have to admit  that all of them are very complicated and I don`t have all the knowledge to understand them.

I need a simple solution, to learn how to write rsync`s proper syntax to synchronize a folder in my computer (client) with a folder in the QNAP server.

I have tried this line:

sudo rsync --delete -azvv -e ssh /media/Dados/Torrents admin@192.168.1.100:/Public/

but I receive back the message: "permission denied", and just this, the terminal does not return a password request.

I believe I have to add the password information in the command line, but what should be the correct syntax please ?

Also, would there be any difference if trying on a wired or wireless networks ? Should I set up something in the router ?

Thank you so much,

Mongao

---

### Post by b0b138 on 2010-06-03
Well first you're trying to do 2 seperate things, rsync and ssh. First you need to setup ssh server correctly on you NAS server. Start here [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH). If you have ssh server setup already, do key authentication. It'll make things easier.

You could probably also use samba shares instead of ssh, and set it up to be a persistant mount (like assigning drive letters to network shares in windows)

---

### Post by Mongao on 2010-06-03
> **b0b138 said:**
> 
You could probably also use samba shares instead of ssh, and set it up to be a persistant mount (like assigning drive letters to network shares in windows)

OK, thanks, could you please give me a basic instruction on how to set it through samba ? I really don`t need SSH, as I`m wired at my own home.

Please, how would my command line look like ? Could you please give me a suggestion ?

Thanks,
Mongao

---

### Post by Iowan on 2010-06-03
A couple of threads you can check:
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")
[http://ubuntuforums.org/showthread.php?t=1186877]("http://ubuntuforums.org/showthread.php?t=1186877")

---

### Post by Mongao on 2010-06-03
> **Iowan said:**
> A couple of threads you can check:
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")
[http://ubuntuforums.org/showthread.php?t=1186877]("http://ubuntuforums.org/showthread.php?t=1186877")

Thank you, but I am a regular user of Windows that occasionally decided to give Ubuntu a try, I`m not really interested in all this information, I`ve passed through lots of threads, all of them are written for programmers, not for regular users - I only know that SSH is an encrypting method, it`s enough info for me.

I am basically looking for a correct suggestion to the rsync command line as I posted above - of course I`d do everything else needed to make the line work.

I am also checking the CNET Forum, will return to Windows, I need a back-up, not a full Unix programming course.

Thanks,
Mongao

---

