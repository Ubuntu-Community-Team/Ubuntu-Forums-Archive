---
title: "&quot;Cannot login to database&quot; error"
date: 2009-04-18
forum: Mythbuntu
---

### Post by felinoel on 2009-04-18
It also mentions something about no UPnP backends found, any thoughts on how to fix this? I am a newbie and am not sure what other info to give, like logs or something?

---

### Post by brianeh on 2009-04-19
Front or backend? Post the log from /var/log/mythtv directory. Can you login using mysql directly from that box - remote access might be disabled.

---

### Post by felinoel on 2009-04-19
> **brianeh said:**
> Front or backend? Post the log from /var/log/mythtv directory. Can you login using mysql directly from that box - remote access might be disabled.

I am a really big newb, how do I get the logs from there? Does it have something to do with terminal? How do I log in using mysql directly? Does it have something to do with the programming folder in applications?


-_-'

---

### Post by brianeh on 2009-04-19
Yes, you'll have to start using the terminal. For mysql the command is

> mysql -h <hostname> -u <user> -p 
- this will then prompt for the password.

For the logs, guess you can use nautilus to browse to the /var/log/mythtv directory then view the files there.

My experience with this myth stuff is you have to be, or get familiar with the underlying system...as it never works smoothly...

---

### Post by felinoel on 2009-04-20
*Post removed*

I'm just going to go back to Ubuntu and try MythTV itself

---

