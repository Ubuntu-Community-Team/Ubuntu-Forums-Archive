---
title: "Upgrade from 14.04 to 16.04 sql php error"
date: 2016-11-05
forum: Multimedia Software
---

### Post by dvjunk on 2016-11-05
A few days ago I upgraded through the Software Updater app to the "new" 16.04 release of Ubuntu. It took several hours 
and I had to interact with the install several times. I didn't notice any erors during the install, but I have several issues now. 
The frontend and backend are running, although the backend didn't record a few shows the first day or two, it is recording now.
When I try to access the backend remotely through the mythweb interface I get a page which shows the error:
error string:  !!NoTrans: You are missing a php extension for mysql interaction. Please install php-mysqli or similar!!
    filename:  /usr/share/mythtv/mythweb/includes/php_version_check.php
If I run:
sudo apt-get install php-mysqli
or
sudo apt-get install php-mysql
I get:
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'sgml-data' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

I have tried:
sudo apt autoremove
sudo apt-get update
followed by
sudo apt-get upgrade
which returns the same error

sudo apt-get install --purge sgml-data
which returns the same error

and maybe a few others.

I was also getting a warning mentioning 50unattended-upgrades.ucf-old so I moved it to a different folder from 
/etc/apt/apt.conf.d and I don't get that warning anymore. 50unattended-upgrades was one of the interactions 
with the install process and I chose to use the developer (I think) version during the install.

I also tried re-running Software Updater and it lists 8 updates but I get an error when I try to install. The updates do include PHP bindings and Python for Mythtv.

As you can probably tell I am not an Ubuntu/Myth expert, so I hope I have provided enough info for someone to help me resolve this.

I love using my MythTV box, but times like this are frustrating.

Thanks,
Don

---

### Post by dvjunk on 2016-11-10
After trying sereval other things I did a search for
files list file for package is missing final newline
and found these two posts:
[https://ubuntuforums.org/showthread.php?t=1319791](https://ubuntuforums.org/showthread.php?t=1319791)
[http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-missing-final-newline-271118/](http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-missing-final-newline-271118/)

which both had similar problems. 
Seems like this type problem has existed for a long time. Would be nice if the error message indicated where the file lived and something more descriptive than "missing final newline", especially when it is really corrupt.

My sgml-data.list was corrupt - did not display text characters 
so I did:
cd /var/lib/dpkg/info
sudo mv sgml-data.list sgml-data.list.corrupt
sudo apt-get remove sgml-data --purge
sudo apt-get install php-mysql
     which installed fine, but there is still no sgml-data.list, so I did
sudo apt-get install sgml-data
     and now sgml-data.list is a readable list of files. (cat sgml-data.list displays a text list of files)
I ran Software Updater without error and I am now up to date!

Thanks to those who posted solutions in the other threads.

---

