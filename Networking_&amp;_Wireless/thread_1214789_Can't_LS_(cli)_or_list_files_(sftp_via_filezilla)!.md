---
title: "Can't LS (cli) or list files (sftp via filezilla)!!"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by OSXniCKels on 2009-07-16
Hello all.

About a month ago, all of a sudden I am not able to list directories remotely on my ubuntu box.  I can ssh in remotely, i can pwd, i can su, i can cd around, but i CANNOT LS!!

I was hoping someone has had this issue before and can offer me advice.

I'm not sure what the hell's going on, but it sucks not having access to my files, and a big pain knowing I'll probably have to reinstall ubuntu.

Thank you in advance.

--OSXniCKels

---

### Post by wirelessmonkey on 2009-07-16
try
```

locate ls

```

It should return the path to the ls binary. i.e. /bin/ls
If something was messed up in pathing, you can use the full path to execute ls.

---

### Post by OSXniCKels on 2009-07-17
Thanks for your help.
 
I tried your suggestion and still no luck.  Do you think a package in an update is incompatable?  Do you think it could be a firewall/router/ISP thing?  I have port 22 opened in Shorewall, and forwarded through my router.  Of course I can login via SSH so it shouldn't be a networking issue.
 
This is just odd.  I will keep waiting and hoping to hear from you guys.  But if I end up needing to reinstall, it's not the end of the world!
 
Thanks again.
 
--OSXniCKels

---

### Post by jonobr on 2009-07-17
If you type

```
which ls
``` in a terminal, do you see anything
its sounding like a path issue

if not , and there is no ls in /bin then thats extremely disconcerting.

When you open a session with a system, what you type in that session should not be affected by firewalls,

it sounds more like one of two things,
either you removed ls or the Path when you log in does not have to /bin.

If the above commands does not show anything then

```
echo $PATH
```
 in your terminal window,
if it does not show /bin then thats  the issue.

if so try typing in 

```
/bin/ls ~/Desktop 
```

and see if that works, if it does, you need to modify your path.

---

### Post by OSXniCKels on 2009-07-17
Thank you all very much!

Ok so,
```
echo $PATH
```returns
```
/usr/local/sbin: /usr/local/bin: /usr/sbin: /usr/bin: /sbin: /bin: /usr/games
```So /bin is in my path, and ls is in /bin.

When I type /bin/ls it runs fine.  Not sure why it's acting that way, but it works.

Thanks again forum!

--OSXniCKels

---

### Post by jonobr on 2009-07-17
stupid question for you, 
do you run ls on its own or do you use ls and then a command or something after it?

If so , whats the full command

from what your posting, this should work

---

### Post by jonobr on 2009-07-17
Actually now that I look at your path Im not so sure.

are those spaces in your path?
Im wondering if thats the problem?

Mine doesnt contain spaces.



```
 echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by OSXniCKels on 2009-07-17
Yeah I'm sorry. My path has no spaces either, I typed it that way. My bad.

It depends what my purpose is, but I use ls by itself sometimes, but also, I use ls -al as well.

Since I now know that I can run /bin/ls that's great.  But only via terminal.  I use FileZilla and connect to my server via SFTP.  FZ automatically issues the ls cmd upon connecting, so I can't give it /bin/ls.

Could that mean there's a problem with my ssh suite? (ssh, sftp, scp, etc)

---

### Post by jonobr on 2009-07-17
Stupid question,
Using the same account on the local machine works?

However when you ssh using the same account same shell etc it doesnt?

---

