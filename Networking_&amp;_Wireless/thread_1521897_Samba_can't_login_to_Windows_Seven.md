---
title: "Samba can't login to Windows Seven"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by kyne on 2010-07-01
Hi,

I'm not new to Ubuntu, but I've never been able to solve this problem since the last two ubuntu releases. I thought 10.04 might solve it... but I was wrong.

I've got two computer :
- My laptop, with Ubuntu 10.04 
- My PC, with Windows Seven

When I try to access my shared files ON my PC FROM my laptop, Samba ask for a password. I typed my Windows Seven login/password, pressed OK... and again, Samba asked for the password. I thought the problem came from Windows Seven, not allowing remote access from a local user account... 
I tried to allow anonymous access on my PC, but it didn't help...

But then, I learned I could also mount my shared files by adding a line in /etc/fstab :
```
//192.168.1.2/Users /media/KynePC smbfs credentials=/etc/samba/cred-file,rw 0 0
```
In the cred-file, I put the exact same login and password then before... and bingo, it works. 

But the problem is not fully resolved, as I can only browse files from the "mounted shortcut". I can't use my remote printer anymore, or access any external HD that I share on my PC :(
So I really need to get samba working... :/

---

### Post by kyne on 2010-07-02
Anyone ? :/

---

### Post by wookieshaver on 2010-07-02
Well the problem may still, indeed, be windows 7. Is password protected sharing turned on for your windows 7 box? I had to disable it for my ubuntu boxes to get to my windows 7 box with all my music. Here's a guide:
[http://maximumpcguides.com/windows-7/disable-password-protected-sharing/](http://maximumpcguides.com/windows-7/disable-password-protected-sharing/)

---

### Post by kyne on 2010-07-02
I'll try your link and see what comes up.

But I think Samba actually wants a password, even when it's not required :/

---

### Post by Morbius1 on 2010-07-02
You by any chance using "Windows Live Sign-In Assistant" on Win7: [http://social.technet.microsoft.com/For  ... 79a5597527]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527")

That may be the problem.

---

### Post by kyne on 2010-07-02
I'm not using it, but it's installed. I've removed it now, and I'll check tomorrow if the problem seems fixed.

Thanks for your help, anyway :)

---

### Post by kyne on 2010-07-03
Ok so the password protection was disabled on my PC, so i re-enabled it. And now... it still asks for a login/password, BUT, if I input my windows account, I can access my shared files from my laptop ! 

(I've also uninstalled the login assistant)

So thanx, again.

Fixed :)

---

