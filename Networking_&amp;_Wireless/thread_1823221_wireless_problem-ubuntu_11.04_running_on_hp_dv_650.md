---
title: "wireless problem-ubuntu 11.04 running on hp dv 6500 amd 64 bit"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by BobiZOZO on 2011-08-11
i tried to do all the things i found online in aim installing the driver of my Broadcom 802.11 card, so i will have wireless in my UBUNTU 11.04 .
but i always get those messages(which appear in the end).
what am i missing??? thanks.



from the shell:
ME@ubuntu:~$ cd Desktop/
ME@ubuntu:~/Desktop$ ls
broadcom-sta-common_5.60.48.36-3_all.deb  gnome-terminal.desktop
broadcom-sta-source_5.60.48.36-3_all.deb
ME@ubuntu:~/Desktop$ sudo dpkg -i *.deb >> tt.txt
[sudo] password for ME: 
dpkg: dependency problems prevent configuration of broadcom-sta-source:
 broadcom-sta-source depends on debhelper (>= 7); however:
  Package debhelper is not installed.
 broadcom-sta-source depends on quilt; however:
  Package quilt is not installed.
dpkg: error processing broadcom-sta-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 broadcom-sta-source
ME@ubuntu:~/Desktop$

---

### Post by ~!geek!~ on 2011-08-11
It seems a Dependency problem with broadcom package,
You may try this:
Open synaptic manager-> search for broadcom -> select the required broadcom package and mark it for installation. Synaptic will select all the dependencies and mark them too-> Select generate package download script from file menu in synaptic manager. Now follow this link, to download files required using some download manager and install them:
[http://xperiencegnulinux.blogspot.com/2011/07/manage-ubuntu-without-active-internet.html](http://xperiencegnulinux.blogspot.com/2011/07/manage-ubuntu-without-active-internet.html)

---

### Post by militantduck on 2011-08-11
have you tried...

sudo apt-get install broadcom-sta-common

that should install all dependencies as well.

good luck

---

### Post by militantduck on 2011-08-11
In case you cant get on the internet using a wire or something with that machine, here is my output from the above command, it lists the packages it needs as dependencies. (Ubuntu 11.04)


```

daffyduck@ubuntu:~$ sudo apt-get install broadcom-sta-common
[sudo] password for daffyduck: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  broadcom-sta-source debhelper html2text libmail-sendmail-perl
  libsys-hostname-long-perl module-assistant po-debconf quilt
Suggested packages:
  dh-make libmail-box-perl procmail graphviz
The following NEW packages will be installed
  broadcom-sta-common broadcom-sta-source debhelper html2text
  libmail-sendmail-perl libsys-hostname-long-perl module-assistant po-debconf
  quilt
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,870 kB of archives.
After this operation, 5,878 kB of additional disk space will be used.

```

---

### Post by theozzlives on 2011-08-11
I had this problem also and went back to 10.04. I may try these ideas. Let me know if it works.

---

### Post by BobiZOZO on 2011-08-11
thanks for the reply, it sounds good, but i would never finish though, cause those dependencies have another dependencies etc...
M I RIGHT?

THANKS AGAIN


> **militantduck said:**
> In case you cant get on the internet using a wire or something with that machine, here is my output from the above command, it lists the packages it needs as dependencies. (Ubuntu 11.04)


```

daffyduck@ubuntu:~$ sudo apt-get install broadcom-sta-common
[sudo] password for daffyduck: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  broadcom-sta-source debhelper html2text libmail-sendmail-perl
  libsys-hostname-long-perl module-assistant po-debconf quilt
Suggested packages:
  dh-make libmail-box-perl procmail graphviz
The following NEW packages will be installed
  broadcom-sta-common broadcom-sta-source debhelper html2text
  libmail-sendmail-perl libsys-hostname-long-perl module-assistant po-debconf
  quilt
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,870 kB of archives.
After this operation, 5,878 kB of additional disk space will be used.

```

---

