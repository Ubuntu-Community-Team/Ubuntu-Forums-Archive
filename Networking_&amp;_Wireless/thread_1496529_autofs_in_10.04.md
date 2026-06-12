---
title: "autofs in 10.04"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by gfxguy on 2010-05-29
So I finished upgrading to 10.04 yesterday, and proceeded to vpn to my work computers and work from home for about 5 or six hours with no problem.

Now this morning I'm having a really weird autofs problem... I can switch to the root level of the server I'm connecting to, but that's it.  So let's say the work server is just called "work", here's what happens (this is a cut and paste, but names have been changed to protect the not so innocent):

```

me@desktop:~$ cd /net/work
me@desktop:/net/work$ ls -l
total 0
drwxr-xr-x 2 root root 0 2010-05-29 11:32 home
drwxr-xr-x 2 root root 0 2010-05-29 11:32 public
drwxr-xr-x 2 root root 0 2010-05-29 11:32 sys
drwxr-xr-x 2 root root 0 2010-05-29 11:32 tutorial
me@desktop:/net/work$ cd home
bash: cd: home: No such file or directory
me@desktop:/net/work$

```

I swear to you I was just doing this last night, multiple servers, for hours and hours and everything was working just fine.

So what's wrong?  It's certainly possible someone changed something at work, but I can connect... and there are the directories right there...

Any help greatly appreciated.

---

### Post by gfxguy on 2010-05-29
Note: manually mounting the work/home directory works, this is clearly an autofs issue.

(I know, I know... then why did it work last night... no idea, maybe because, while I rebooted after the upgrade, I hadn't rebooted after some of the finishing touches).

---

### Post by microbert on 2010-07-24
gfxguy, did you figure out the problem? I ran into the same issue last night, and what I noticed is, autofs mounted the remote folder one level to high. So in your case, if you try connecting to /net/work/home, home would be empty, but you'll likely find all files located on your server home folder in /net/work.
This way you can only access the first share you'll connect to. Umounting only works with
 sudo service autofs reload

---

### Post by gfxguy on 2010-07-24
I honestly forget what it was... I just did a complete reinstall to consolidate disks and everything seems to work.

I don't know what the problem may have been.

What I discovered then was that I could manually mount remote drives... it wasn't a matter of being at the wrong level, in my case, though.

---

