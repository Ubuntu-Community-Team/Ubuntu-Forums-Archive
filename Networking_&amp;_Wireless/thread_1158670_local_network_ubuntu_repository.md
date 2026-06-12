---
title: "local network ubuntu repository"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by dbuttera187 on 2009-05-13
This is the page I was trying to follow but I know it is going to need a bit more up to date information in some areas: 

[http://keystoneit.wordpress.com/2006/08/25/local-network-ubuntu-repository/](http://keystoneit.wordpress.com/2006/08/25/local-network-ubuntu-repository/)

Does anyone know how to edit this piece of script to make it geared towards intrepid ibex instead of dapper drake?

[INDENT]#!/bin/bash -x
 /usr/bin/debmirror –nosource -m –passive –host=archive.ubuntulinux.org \
–root=ubuntu/ –method=ftp –progress –dist=dapper \
–ignore-release-gpg –section=main,multiverse,universe,restricted \
–arch=i386 /backups/ubuntu/




[/INDENT]Go to the link to see more about it please. Thanks in advance :)

---

