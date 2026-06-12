---
title: "Adventures with smbnetfs"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by castalla on 2010-02-03
I've discovered there's a problem accessing shares on Win 7 using smnnetfs. The routine sees the win7 box but can't access the shared folders. 

Here's the output from ls -l :

user@SmartQ:~/SHARE$ ls -l
total 0
drwxrwxrwx 2 root root 0 1970-01-01 01:00 BB1
drwxrwxrwx 2 root root 0 1970-01-01 01:00 MSHOME
drwxrwxrwx 2 root root 0 1970-01-01 01:00 WINPC

and

user@SmartQ:~$ cd SHARE/WINPC
user@SmartQ:~/SHARE/WINPC$ dir
dir: cannot open directory .: Input/output error
user@SmartQ:~/SHARE/WINPC$


The same dir command on BB1 (Vista box) lists the shared directories

As I mentioned elsewhere the Win7 shares are working okay as they are available via Vista and linux busybox

Has anybody ideas what the input/output error actually means? How to fix it?

---

