---
title: "mp3 apt-get errors"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by lunaz on 2007-02-24
i'm following a guide i found & accidentally posted to. :) i got stuck while trying to install w32codecs:
```

gail@gail-oldpos:~$ sudo apt-get install gxine
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmodplug0c2 libxine1 libxvmc1
Suggested packages:
  realplayer libdvdcss2 libdvdcss gxineplugin libartsc0
Recommended packages:
  libxine-extracodecs
The following NEW packages will be installed:
  gxine libmodplug0c2 libxine1 libxvmc1
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3627kB of archives.
After unpacking, 8598kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com edgy/main libmodplug0c2 1:0.7-5 [115kB]     
Get:2 http://security.ubuntu.com edgy-security/main libxine1 1.1.2+repacked1-0ubuntu3.2 [3222kB]
Get:3 http://archive.ubuntu.com edgy/main libxvmc1 2:1.0.2-0ubuntu2 [12.1kB]   
Get:4 http://archive.ubuntu.com edgy/main gxine 0.5.7-1ubuntu6 [278kB]         
Fetched 3627kB in 2m18s (26.3kB/s)                                             
Selecting previously deselected package libmodplug0c2.
(Reading database ... 86601 files and directories currently installed.)
Unpacking libmodplug0c2 (from .../libmodplug0c2_1%3a0.7-5_i386.deb) ...
Selecting previously deselected package libxvmc1.
Unpacking libxvmc1 (from .../libxvmc1_2%3a1.0.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package libxine1.
Unpacking libxine1 (from .../libxine1_1.1.2+repacked1-0ubuntu3.2_i386.deb) ...
Selecting previously deselected package gxine.
Unpacking gxine (from .../gxine_0.5.7-1ubuntu6_i386.deb) ...
Setting up libmodplug0c2 (0.7-5) ...

Setting up libxvmc1 (1.0.2-0ubuntu2) ...

Setting up libxine1 (1.1.2+repacked1-0ubuntu3.2) ...

Setting up gxine (0.5.7-1ubuntu6) ...

gail@gail-oldpos:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
gail@gail-oldpos:~$ 
gail@gail-oldpos:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  amarok-xine kdelibs-data kdelibs4c2a libarts1c2a libartsc0 libavahi-qt3-1
  libifp4 liblua50 liblualib50 libnjb5 libopenexr2c2a libpcre3 libqt3-mt
  libruby1.8 libtunepimp3 python-qt3 python-sip4 ruby ruby1.8
Suggested packages:
  libvisual-0.4-plugins libqt0-ruby1.8 amarok-engines libqt3-mt-psql
  libqt3-mt-mysql libqt3-mt-odbc libtunepimp3-dev libtunepimp-bin
  python2.3-qt3-gl python-qt3-doc ruby1.8-examples rdoc1.8 ri1.8
Recommended packages:
  kdemultimedia-kio-plugins perl-suid libarts1-akode
The following NEW packages will be installed:
  amarok amarok-xine kdelibs-data kdelibs4c2a libarts1c2a libartsc0
  libavahi-qt3-1 libifp4 liblua50 liblualib50 libnjb5 libopenexr2c2a libpcre3
  libqt3-mt libruby1.8 libtunepimp3 python-qt3 python-sip4 ruby ruby1.8
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.6MB of archives.
After unpacking, 121MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com edgy/main libartsc0 1.5.4-0ubuntu1 [13.9kB]    
Get:2 http://security.ubuntu.com edgy-security/main libavahi-qt3-1 0.6.13-2ubuntu2.4 [24.7kB]
Get:3 http://archive.ubuntu.com edgy/main libqt3-mt 3:3.3.6-3ubuntu3 [3138kB]
Get:4 http://security.ubuntu.com edgy-security/main kdelibs-data 4:3.5.5-0ubuntu3.1 [7211kB]
Get:5 http://archive.ubuntu.com edgy/main libarts1c2a 1.5.4-0ubuntu1 [1024kB]
Get:6 http://archive.ubuntu.com edgy/main liblua50 5.0.2-6 [45.5kB]       
Err http://archive.ubuntu.com edgy/main liblua50 5.0.2-6                  
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:7 http://archive.ubuntu.com edgy/main liblualib50 5.0.2-6 [29.3kB]         
Get:8 http://archive.ubuntu.com edgy/main libopenexr2c2a 1.2.2-4.3 [281kB]     
Get:9 http://archive.ubuntu.com edgy/main libpcre3 6.4-2ubuntu1 [174kB]    
Get:10 http://archive.ubuntu.com edgy/main amarok-xine 2:1.4.3-0ubuntu10 [51.3kB]
Get:11 http://archive.ubuntu.com edgy/main ruby 1.8.2-1 [19.0kB]         
Get:12 http://archive.ubuntu.com edgy/main python-sip4 4.4.5-2ubuntu1 [80.7kB]
Get:13 http://archive.ubuntu.com edgy/main python-qt3 3.16-1.2ubuntu1 [2262kB] 
Get:14 http://security.ubuntu.com edgy-security/main kdelibs4c2a 4:3.5.5-0ubuntu3.1 [9555kB]
Get:15 http://archive.ubuntu.com edgy/main libifp4 1.0.0.2-3 [32.0kB]     
Get:16 http://archive.ubuntu.com edgy/main libnjb5 2.2.5-4.1ubuntu1 [96.2kB]   
Get:17 http://archive.ubuntu.com edgy/main libtunepimp3 0.4.2-3ubuntu3 [229kB] 
Get:18 http://archive.ubuntu.com edgy/main amarok 2:1.4.3-0ubuntu10 [14.7MB]   
Get:19 http://security.ubuntu.com edgy-security/main libruby1.8 1.8.4-5ubuntu1.2 [1451kB]
Get:20 http://security.ubuntu.com edgy-security/main ruby1.8 1.8.4-5ubuntu1.2 [191kB]
Fetched 40.6MB in 25m11s (26.8kB/s)                                            
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblua50_5.0.2-6_i386.deb Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
gail@gail-oldpos:~$ sudo apt-get --fix missing
Password:
E: Command line option --fix is not understood

```

is this just a matter of trying again? what does --fix missing do?

---

### Post by yabbadabbadont on 2007-02-24
--fix-missing

You left out the "-" between fix and missing.  :)

---

### Post by lunaz on 2007-02-24
apt-get --fix-missing = command not found :(

---

### Post by yabbadabbadont on 2007-02-24
Did you remember to put the "sudo" on the front of it?

---

### Post by lunaz on 2007-02-24
```

gail@gail-oldpos:~$ sudo apt-get fix-missing
Password:
E: Invalid operation fix-missing

```

and gail@gail-oldpos:~$ sudo apt-get --fix-missing
gave me the help page for apt.

---

### Post by lunaz on 2007-02-24
[http://ubuntuforums.org/showpost.php?p=1620069&postcount=35](http://ubuntuforums.org/showpost.php?p=1620069&postcount=35)
this seemed to work so far. i can now play mp3s off my computer or off my flash drive. :P just wish my real speakers didnt die on me lol.

---

