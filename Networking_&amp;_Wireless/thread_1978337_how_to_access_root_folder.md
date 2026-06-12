---
title: "how to access /root/ folder?"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by wa1d0rf on 2012-05-11
I was reading in another (3 year old) thread that suggested putting a credentials file in the /root/ folder.  I tried to do this, including using sudo command but my Ubuntu 12.04 system reports that I don't have permissions.  I log in as a user named "john".  This folder has the following permissions:
```
drwx------   8 root root  4096 May  8 19:04 root
```This is what I get when I try to access this folder:
```
john@john-ubuntu:/$ cd /root
bash: cd: /root: Permission denied
john@john-ubuntu:/$ sudo cd /root
sudo: cd: command not found
john@john-ubuntu:/$ 
```
What is the issue I'm having here?  Why would the person have suggested putting my credentials file here anyway?

---

### Post by MG&amp;TL on 2012-05-11
I'm not sure...can you post the thread?

Read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") first, it's a good source of information about permissions.

The reason *sudo* didn't find *cd* is that cd is a shell builtin, not an actual program. So when sudo looks for an executable file for cd, it can't find it. To actually look in /root (not very interesting):

```
sudo -i
cd /root
```

Hope this helps a bit.

---

### Post by Enigmapond on 2012-05-11
If you need to browse the root folders, just do it with nautilus.

```
gksu nautilus
```

---

### Post by wa1d0rf on 2012-05-11
> **MG&TL said:**
> I'm not sure...can you post the thread?

Read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) first, it's a good source of information about permissions.

The reason *sudo* didn't find *cd* is that cd is a shell builtin, not an actual program. So when sudo looks for an executable file for cd, it can't find it. To actually look in /root (not very interesting):

```
sudo -i
cd /root
```Hope this helps a bit.


Here is the thread I was speaking about:
[http://ubuntuforums.org/showthread.php?p=11926686#post11926686](http://ubuntuforums.org/showthread.php?p=11926686#post11926686)

---

### Post by MG&amp;TL on 2012-05-11
Well, as the guy said in the thread, "what's your problem, post it elsewhere"-the thread's 3 years out of date. 

Post your problem here, or make another thread-I'm not a networking expert, but there are people here who are.

---

