---
title: "Jacked Up Video"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by Neondog82 on 2007-12-28
Hello everyone, I have done it again. Some how I have screwed up my install of Ubuntu. The problem now is that the login screen is like four monitors on one screen. Everything is screwed up and I can't see anything to fix stuff. Is there a way to put my xorg.conf file back to the way it when I installed it? I messed it up while trying to install my ATI card. Also is there suppose to a xorg.conf.1, xorg.conf.2, xorg.conf.3 and a xorg.conf.fglrx files? there are a couple other also but I can't think of what they are right now. Any help would be much appreciated. Thanks in advance.

---

### Post by Neondog82 on 2007-12-28
For anyone that reads this, I got it fixed. I was able to get a command prompt where I used the code:

```
Sudo dpkg-reconfigure xserver-xorg
```

After that just type in:

```
Sudo /etc/init.d/gdm start
```

---

