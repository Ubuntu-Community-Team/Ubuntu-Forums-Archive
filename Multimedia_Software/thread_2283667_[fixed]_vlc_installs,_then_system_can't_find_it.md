---
title: "[fixed] vlc installs, then system can't find it?"
date: 2015-06-23
forum: Multimedia Software
---

### Post by jnajna on 2015-06-23
Dear Ubuntu community,

This is very strange to me.  I added the nightly build ppa for vlc, installed vlc, removed vlc, then removed ppa.  Now I am stuck:


----------

$ sudo apt-get update

$ sudo apt-get  install vlc

Reading package lists... Done

Building dependency tree  
     
Reading state information... Done

vlc is already the newest version.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ which vlc

$ /usr/bin/vlc

bash: /usr/bin/vlc: No such file or directory

$ vlc

The program 'vlc' is currently not installed. You can install it by typing:

sudo apt-get install vlc-nox

$ uname -a

Linux HOST 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:31:11 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

$ lsb_release -a

No LSB modules are available.

Distributor ID:    Ubuntu

Description:    Ubuntu 15.04

Release:    15.04

Codename:    vivid

----------


***Please help me.  Thank you!***

---

### Post by papibe on 2015-06-23
Hi jnajna. Welcome to the forum ):P

Could you run these commands, and post back the results?
```
apt-cache policy vlc

dpkg -L vlc | xargs -I arg -n1 bash -c 'if [ ! -e "$1" ]; then echo "missing file: $1"; fi' _ arg
```
Regards.

---

### Post by jnajna on 2015-06-23
```
$ sudo apt-cache policy vlc
vlc:
  Installed: 2.2.0-1
  Candidate: 2.2.0-1
  Version table:
 *** 2.2.0-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages
        100 /var/lib/dpkg/status


```

no output for this one:

```
$ dpkg -L vlc | xargs -I arg -n1 bash -c 'if [ ! -e "$1" ]; then echo "missing file: $1"; fi' _ arg
```

Thank you!

I also purged and reinstalled.  It is like my path is wrong or something.

```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games


```

---

### Post by papibe on 2015-06-23
Try this:
```
sudo apt-get purge vlc
sudo apt-get autoremove
sudo apt-get install -f

sudo apt-get update
sudo apt-get install --reinstall vlc
```
Let us know how that goes.

---

### Post by jnajna on 2015-06-23
All the commands ran OK.  But still no vlc:

```
$ vlc
The program 'vlc' is currently not installed. You can install it by typing:
sudo apt-get install vlc-nox

$ sudo apt-get install vlc-nox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc-nox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```


```

$ apt-cache policy vlc vlc-nox
vlc:
  Installed: 2.2.0-1
  Candidate: 2.2.0-1
  Version table:
 *** 2.2.0-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages
        100 /var/lib/dpkg/status
vlc-nox:
  Installed: 2.2.0-1
  Candidate: 2.2.0-1
  Version table:
 *** 2.2.0-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by jnajna on 2015-06-23
Can I purge all my sources somehow?

How is this possible?

```
# apt-get remove --purge vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vlc*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,898 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
# vlc
The program 'vlc' is currently not installed. You can install it by typing:
apt-get install vlc-nox


```

---

### Post by ajgreeny on 2015-06-23
What do commands ```
which vlc
whereis vlc
``` show as output?

---

### Post by jnajna on 2015-06-23
Sure:

```
# which vlc
```

```
# whereis vlc
vlc: /usr/lib/vlc /usr/share/vlc /usr/share/man/man1/vlc.1.gz

```

```
/usr/share/vlc# ll
total 100
drwxr-xr-x   5 root root  4096 Jun 19 16:40 ./
drwxr-xr-x 301 root root 12288 Jun 22 11:03 ../
drwxr-xr-x   3 root root  4096 Jun 17 10:23 lua/
drwxr-xr-x   3 root root  4096 Jun 19 16:40 skins2/
drwxr-xr-x   2 root root  4096 Jun 19 16:40 utils/
-rw-r--r--   1 root root 73164 Mar 19 14:43 vlc.ico


```

---

### Post by mc4man on 2015-06-23
could you try - 
sudo apt-get purge vlc-data
sudo apt-get update
sudo apt-get install vlc

---

### Post by jnajna on 2015-06-23
:guitar:   


sudo apt-get purge vlc-data  did the trick!  Thanbk you all for your effort!

---

### Post by mc4man on 2015-06-23
Just for reference - 
a vlc install  comes with  a min of 5 packages, just removing vlc leaves all the rest behind. Removing vlc-data will assure removing all the packages from an install of vlc

Also to note - that vlc master ppa is dead, hasn't gotten new builds in months which when providing the dev version (3.0 currently), makes it worthless..

---

