---
title: "Ubuntu, Elisa and Windows Network Shares"
date: 2008-12-11
forum: Multimedia Software
---

### Post by corman420 on 2008-12-11
I have a Ubuntu 8.10 host with Elisa Media Centre installed. 

I have been trying to figure out a way to add Windows Network Shares on my Ubuntu machine within Elisa - but I'm failing miserably. 

I have found out that there is a bug in gnome which has messed up windows authentication.

My question is: What is the best way to add my Windows Vista network share within Elisa? And is there a way to bypass this bug in gnome?

I'm new to Elisa, so I have no idea where the conf file is, and how to put in it...

Im also new to samba...

Any help would be greatly appreciated. Thanks!

---

### Post by corman420 on 2008-12-11
Ok, I foiund out downgrading SAMBA might help, but I can't seem to get that to work either...I get an error when running the "dpkg -i --force-downgrade" command...

cor@ubuntu:~/Desktop$ sudo dpkg -i --force-downgrade samba-common_3.0.26a-1ubuntu2.5_i386.deb
dpkg - warning: downgrading samba-common from 2:3.2.3-1ubuntu3.3 to 3.0.26a-1ubuntu2.5.
(Reading database ... 118109 files and directories currently installed.)
Preparing to replace samba-common 2:3.2.3-1ubuntu3.3 (using samba-common_3.0.26a-1ubuntu2.5_i386.deb) ...
Unpacking replacement samba-common ...
dpkg: dependency problems prevent configuration of samba-common:
 samba-common depends on libldap2 (>= 2.1.17-1); however:
  Package libldap2 is not installed.
dpkg: error processing samba-common (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 samba-common

---

### Post by corman420 on 2008-12-11
I'm happy to report I found a solution for the bug in gnome, as well as I was able to add the shares in Elisa :)

It was easy!!!

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Wihtin that post, it tells you how to mount the share in /media/. I simply changed that to /home/USERNAME/ and mounted my Videos, Pictures, Music shares into the appropriate folders on Ubuntu. And then opened ELISA and added them. Simple!!!

---

