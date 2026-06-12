---
title: "Need libgcrypt.so.11 for spotify"
date: 2015-11-27
forum: Multimedia Software
---

### Post by mollie4168 on 2015-11-27
Hello,

Spotify won't open.  I've been using [this post]("http://ubuntuforums.org/showthread.php?t=2291529&p=13389376#post13389376") for guidance.  It doesn't seem that I have any version of libgcrypt on my computer.  How do I get it?

[HTML]tracy@tracy:~$ spotify
spotify: error while loading shared libraries: libgcrypt.so.11: cannot open shared object file: No such file or directory
tracy@tracy:~$ ^C
tracy@tracy:~$ wget http://security.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb
--2015-11-27 10:10:18--  http://security.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb
Resolving security.ubuntu.com (security.ubuntu.com)... 2001:67c:1562::17, 2001:67c:1360:8c01::19, 2001:67c:1562::14, ...
Connecting to security.ubuntu.com (security.ubuntu.com)|2001:67c:1562::17|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2015-11-27 10:10:18 ERROR 404: Not Found.

[/HTML]

Thanks!

---

### Post by tridentlead on 2015-11-29
Try the following:
```

wget https://launchpad.net/ubuntu/+archive/primary/+files/libgcrypt11_1.5.3-2ubuntu4.2_i386.deb && wget https://launchpad.net/ubuntu/+archive/primary/+files/libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb && sudo apt-get install -y libgcrypt*

```

---

### Post by blm-ubunet on 2015-11-29
wget downloads a couple of .deb files into your home folder and then they are not used ?
What am I missing.. How does that do anything other than the following:-
```
sudo apt-get install libgcrypt11
```

The .debs are **only** needed if you are running ubuntu 15.04 & later (& the above apt-get fails).
You have to install them with:-
```
sudo dpkg -i blah.deb
```

---

### Post by mollie4168 on 2015-11-29
I may have misunderstood, but here's what happened when I tried both ideas:

[HTML]tracy@tracy:~$ sudo dpkg -i libgcrypt11.deb
[sudo] password for tracy: 
dpkg: error processing archive libgcrypt11.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libgcrypt11.deb
tracy@tracy:~$ wget https://launchpad.net/ubuntu/+archive/primary/+files/libgcrypt11_1.5.3-2ubuntu4.2_i386.deb && wget https://launchpad.net/ubuntu/+archive/primary/+files/libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb && sudo apt-get install -y libgcrypt*
--2015-11-29 09:29:08--  https://launchpad.net/ubuntu/+archive/primary/+files/libgcrypt11_1.5.3-2ubuntu4.2_i386.deb
Resolving launchpad.net (launchpad.net)... 91.189.89.223, 91.189.89.222
Connecting to launchpad.net (launchpad.net)|91.189.89.223|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://launchpadlibrarian.net/201289903/libgcrypt11_1.5.3-2ubuntu4.2_i386.deb [following]
--2015-11-29 09:29:09--  https://launchpadlibrarian.net/201289903/libgcrypt11_1.5.3-2ubuntu4.2_i386.deb
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.229|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 237534 (232K) [application/x-debian-package]
Saving to: &#8216;libgcrypt11_1.5.3-2ubuntu4.2_i386.deb&#8217;

libgcrypt11_1.5.3-2 100%[=====================>] 231.97K   141KB/s   in 1.6s   

2015-11-29 09:29:12 (141 KB/s) - &#8216;libgcrypt11_1.5.3-2ubuntu4.2_i386.deb&#8217; saved [237534/237534]

--2015-11-29 09:29:12--  https://launchpad.net/ubuntu/+archive/primary/+files/libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb
Resolving launchpad.net (launchpad.net)... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net (launchpad.net)|91.189.89.222|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://launchpadlibrarian.net/201289896/libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb [following]
--2015-11-29 09:29:12--  https://launchpadlibrarian.net/201289896/libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.229|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 238842 (233K) [application/x-debian-package]
Saving to: &#8216;libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb&#8217;

libgcrypt11_1.5.3-2 100%[=====================>] 233.24K   253KB/s   in 0.9s   

2015-11-29 09:29:14 (253 KB/s) - &#8216;libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb&#8217; saved [238842/238842]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb
E: Couldn't find any package by regex 'libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb'
E: Unable to locate package libgcrypt11_1.5.3-2ubuntu4.2_i386.deb
E: Couldn't find any package by regex 'libgcrypt11_1.5.3-2ubuntu4.2_i386.deb'
tracy@tracy:~$ sudo apt-get install libgcrypt11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgcrypt11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgcrypt11:i386

E: Package 'libgcrypt11' has no installation candidate
tracy@tracy:~$ sudo apt-get install libgcrypt11:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgcrypt11:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgcrypt11

E: Package 'libgcrypt11:i386' has no installation candidate



[/HTML]

---

### Post by oldos2er on 2015-11-29
What version of Ubuntu are you running? 

As blm-ubunet said, *sudo apt-get install -y libgcrypt** doesn't install the files you downloaded, it only looks to the repositories. To install the files you downloaded, use ```
sudo dpkg -i libgcrypt11_1.5.3-2ubuntu4.2_i386.deb
``` or ```
sudo dpkg -i libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb
``` according to which architecture you're running.

---

### Post by mollie4168 on 2015-11-29
Success!  Many thanks.

---

### Post by oldos2er on 2015-11-29
Welcome.

---

