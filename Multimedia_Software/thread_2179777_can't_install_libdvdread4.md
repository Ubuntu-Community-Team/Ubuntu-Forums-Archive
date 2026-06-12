---
title: "can't install libdvdread4"
date: 2013-10-09
forum: Multimedia Software
---

### Post by jeffrey2 on 2013-10-09
I get the following error when trying to install libdvdread4 in the termainal. Any suggestions

sugar@sugar-Inspiron-1545:~$ sudo /usr/doc/libdvdread4/install-css.sh
[sudo] password for sugar: 
sudo: /usr/doc/libdvdread4/install-css.sh: command not found
sugar@sugar-Inspiron-1545:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2013-10-09 19:18:44--  [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-10-09 19:18:44 ERROR 404: Not Found.

Dynamic fetch failed; Falling back to static fetch
--2013-10-09 19:18:44--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-10-09 19:18:44 ERROR 404: Not Found.

---

### Post by QIII on 2013-10-09
Medibuntu is no longer maintained.

libdvdread4 is in the repo.  Install the package ubuntu-restricted-extras to get it.

---

### Post by Bashing-om on 2013-10-09
jeffrey2; Hi !

".medibuntu.org (packages.medibuntu.org)" is no longer maintained. The package :
 libdvdread4
is available in the ubuntu software repository:
> 
sysop@1304mini:~$ apt-cache search libdvdread4
libdvdread4 - library for reading DVDs
sysop@1304mini:~$


Try terminal command:
```

sudo apt-get install libdvdread4

```

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

### Post by mc4man on 2013-10-09
To continue to use "/usr/share/doc/libdvdread4/install-css.sh" to install libdvdcss2 then **atm** users of 12.04, 12.10 & 13.04 will need to install libdvdread4 from the proposed repo, the new libdvdread 4 is already in 13.10

Basically - 
Open software sources (software and updates in some releases)
Under 'updates' tab enable the proposed repo
Update your sources ( sudo apt-get update
Install or upgrade libdvdread4

After libdvdread4 is installed or updated then re-open software sources, disable the proposed repo, update your sources again
(not all packages in proposed are suitable for upgrading so best to disable after using for a specific package(s)

The new libdvdread4 has an updated install-css.sh that will install libdvdcss2 from a videolan repo

Edit:
references
[https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928](https://bugs.launchpad.net/ubuntu/+source/libdvdread/+bug/1223928)
[https://launchpad.net/ubuntu/+source/libdvdread](https://launchpad.net/ubuntu/+source/libdvdread)

---

### Post by dbates on 2013-10-15
I just upgraded from 12.04 to 13.04. and I could no longer get to the medibuntu repo either. From following others posts, here was my most direct course of action to get Libdvdread4 working on my machine.
Libdvdread4 is already part of 13.04 so no need to try and install.
Install Ubuntu Restricted Extras from your software center first.
Then run the commmand: Sudo /usr/share/doc/libdvdread4/install-css.sh and it should pull down the codecs from videolan instead of medibuntu since it is no longer maintained. Reboot your machine and you should be up and running.

---

