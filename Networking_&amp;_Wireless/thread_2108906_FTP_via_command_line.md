---
title: "FTP via command line?"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by pspencil on 2013-01-25
I am new to Ubuntu and in windows I use filezilla to log in to my ftp server. In Ubuntu, i know there is also a filezilla, but i am just curious is there any way to connect to the server via command line?

Thanks

---

### Post by ahallubuntu on 2013-01-25
Actually, people have been using FTP on the command line since the beginning.  All these Gui tools were built later to make it easier for you.

From the command line, simply type

```
ftp ADDRESS
```

where ADDRESS is the ftp site you are trying to get to.  You can use "cd" and "ls" to navigate.  Use the commands "get" to download a file and "put" to upload.

Personally, even though I am quite comfortable in a terminal, I prefer using the Gui environment for FTP when I can.  I do it in Nautilus (the built-in file manager) in Ubuntu.  Just connect to an FTP server which will open a folder, then drag and drop to other windows to copy files.

---

### Post by pspencil on 2013-01-26
> **ahallubuntu said:**
> Actually, people have been using FTP on the command line since the beginning.  All these Gui tools were built later to make it easier for you.

From the command line, simply type

```
ftp ADDRESS
```

where ADDRESS is the ftp site you are trying to get to.  You can use "cd" and "ls" to navigate.  Use the commands "get" to download a file and "put" to upload.

Personally, even though I am quite comfortable in a terminal, I prefer using the Gui environment for FTP when I can.  I do it in Nautilus (the built-in file manager) in Ubuntu.  Just connect to an FTP server which will open a folder, then drag and drop to other windows to copy files.
I tried ftp command .. and find it not working.. is it because the server require username and password?

---

### Post by ahallubuntu on 2013-01-26
If you're trying to connect to an anonymous FTP server, try the username "anonymous" .

---

### Post by pspencil on 2013-01-26
actually, my question is I have a username and password, but when I try to connect using 'ftp ADDRESS', it doesn't give me the chance to enter my username and password. 

I might have been unclear in my previous post.

---

