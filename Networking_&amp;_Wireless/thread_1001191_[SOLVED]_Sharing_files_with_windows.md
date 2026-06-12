---
title: "[SOLVED] Sharing files with windows"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by Kiradien on 2008-12-03
I have looked around and found many many confusing things referring to samba in every related post. 

What I want is to know the easiest way to share files over a windows network with ubuntu, and perhaps also allow write permissions. Thanks...

---

### Post by philetus on 2008-12-03
[http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/](http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/)

---

### Post by Kiradien on 2008-12-03
That is a great guide, although this is the same thing - the only thing - that I had already tried (Although the guide gave me alot more information, I thought I was doing it completely wrong), so it leaves me with an error. Here's to typing:

```
'net usershare' returned error 255: net usershare cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permission to create a share.
```

I got this error message. Pretty basic, I just need to know how to set the permissions, I didnt notice the little samba thing there before... Any guides on that? I am horrible at finding stuff like this, and usually just go by intuition, but that wont work this time... :( Thanks

---

### Post by philetus on 2008-12-04
Did you log out and back in?

---

### Post by superprash2003 on 2008-12-04
post output of cat /etc/samba/smbusers

---

### Post by razy60 on 2008-12-04
One way is to enable sharing on your windows PC.
go to set up a home network follow the setup guide once its done it asks if you want to write a disc to transfer settings to another PC say no(remember passwords). next go to your Ubuntu PC click on places-network-windows network, it will then show all your windows pc's click on the relevant PC enter your password and share away,
to share files:windows to Ubuntu: etc place them into into your shared folder in windows PC or make them shared, then when your in Ubuntu just open your network folder and look they should be there.
To share files: Ubuntu to windows: open network-windows network, open the folder you want to put the files into then copy and paste files should then transfer to windows pc.
This assumes that your pc's are all on and running.

Raz

---

### Post by Kiradien on 2008-12-04
I actually cant post the result of the commands, as the way that computer is set up... Thanks for all your help, I decided to just do the sharing as a super user, probably easier since I am basically just sharing my windows partitions. So my problem is solved, Thanks everyone for all your help :) Wish I had thought of that sooner :P

---

### Post by Iowan on 2008-12-05
> **Kiradien said:**
> I actually cant post the result of the commands, as the way that computer is set up... Thanks for all your help, I decided to just do the sharing as a super user, probably easier since I am basically just sharing my windows partitions. [COLOR="Red"]So my problem is solved[/COLOR], Thanks everyone for all your help :) Wish I had thought of that sooner :P

Mark it [SOLVED] (under Thread Tools) Thanks!

---

