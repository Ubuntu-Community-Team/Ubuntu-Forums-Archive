---
title: "mount error(127): Key has expired"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by josephpmh on 2009-12-05
Until a few days ago, everything was mounting fine.  Then, when I tried mounting my Windoze share, I got the above message.  (I added T-bird 3 RC2 that day.

I've tried so many different ways of searching for the solution.  I've check the Windoze7 machine (all seems 2B set correctly there; but I cannot connect using either cifs or smbfs. 

Here's the command (in fstab): 

```
//192.168.1.101/Data ~/Data   cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

When I enter ```
sudo mount -a
```

I get ```
mount error(127): Key has expired
```

How do I permanently renew this key?  

Please help.  I use the Windoze machine for backup to Mozy, and I use rsync to backup this machine to Windoze.  But right now I can't mount a Windoze share.

UPDATE:  This is a windoze problem.  Still haven't solved it.  But will update when I do.

SOLVED UPDATE:  DOH!  Apparently, I haven't been using Windoze in a while.  I was mounting the widoze share folders from my windoze uac which is set up to have the pw expire (which it did).

---

### Post by cesarradtke on 2012-01-02
Your password may have expired or need to change it. Log on into a Windows box or RDP terminal  to change the password first, then try mount again.

---

