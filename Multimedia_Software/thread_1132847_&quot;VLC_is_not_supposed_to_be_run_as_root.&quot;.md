---
title: "&quot;VLC is not supposed to be run as root.&quot;But Why?"
date: 2009-04-22
forum: Multimedia Software
---

### Post by lovelyvik293 on 2009-04-22
I am using ubuntu 8.10 and when i tried to run vlc as the root user i got 
this error
```

VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root first and
cannot be run by non-trusted users first).

```
Now my first query is what is the problem running the Vlc as a root?

and second what is this vlc-wrapper?

I searched in the ubuntuforum and goolge also about this issue and i don't get any good answer.If you the link of the answer of my query please post it.
Thanks
Cheers.

---

### Post by SuperSonic4 on 2009-04-22
You're exposing system files to the internet which can screw up the system

---

### Post by aysiu on 2009-04-22
Only applications that need access to system files should be run as root.

A better question is "Why are you trying to run VLC as root?"

---

### Post by JK3mp on 2009-04-22
I second the above posts.No real reason to run vlc in root. A security risk anytime you idle around in root. Thus why root is a seperate account from primary user.

---

### Post by psyke83 on 2009-04-23
> **lovelyvik293 said:**
> I am using ubuntu 8.10 and when i tried to run vlc as the root user i got 
this error
```

VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root first and
cannot be run by non-trusted users first).

```
Now my first query is what is the problem running the Vlc as a root?

and second what is this vlc-wrapper?

I searched in the ubuntuforum and goolge also about this issue and i don't get any good answer.If you the link of the answer of my query please post it.
Thanks
Cheers.

I highly recommend you learn about administrative privileges, and the security impact of user vs superuser. An example: a buffer overflow exploit in a media file could let hackers gain root access to your machine.

Another reason why it's not recommended: when you run VLC as root, it will save the preferences to your user directory with root privileges. When you next try to launch VLC as a regular user, it will not be able to save any preferences, as the current files will be marked as owned by root. Very messy.

---

### Post by mysoogal on 2011-08-08
its 2011, having the same problem, can not use vlc while I'm using the root account.

mencoder, ffmpeg, handbrake etc all could be used with root ? is vlc special needs case? or i need to be mentally ill to understand what vlc-wrapper is ? where could i learn more about this vlc-wrapper I'm mentally sick and I'm Afraid I'll lose it all 

:confused::guitar:

---

### Post by aysiu on 2011-08-08
I'm still confused as to why people are logged in the root account, let alone running VLC as root.

---

### Post by andrew.46 on 2011-08-09
> **aysiu said:**
> I'm still confused as to why people are logged in the root account, let alone running VLC as root.

Indeed! It is in fact *possible* to compile vlc to run as root:

```

andrew@skamandros~/source/vlc/vlc-1.1.11$ ./configure --help | grep -i 'run-as-root'
  --enable-run-as-root    allow running VLC as root (default disabled)

```

but I believe that this is intended for those who wish to run vlc on an embedded, single user device that requires applications to function as root. See [this commit message]("http://mailman.videolan.org/pipermail/vlc-devel/2008-September/050560.html") from the developer who put this option in. Definitely not for the other 99.999% of users...

---

