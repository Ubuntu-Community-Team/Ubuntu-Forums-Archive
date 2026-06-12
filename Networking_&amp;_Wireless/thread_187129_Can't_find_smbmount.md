---
title: "Can't find smbmount"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by bhaskar on 2006-06-02
I can't find smbmount to mount a Windows share.  Which package has it?  Please see below.  Thanx muchly.

-- Bhaskar

---------------------------------------------
sh-3.1$ sudo find / -xdev -iname smbmount
sh-3.1$ dpkg -l smbclient
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                   Version                Description
+++-======================-======================-============================================================
ii  smbclient              3.0.22-1ubuntu3        a LanManager-like simple client for Unix
sh-3.1$ apt-cache search smbmount
sh-3.1$ 
---------------------------------------------

---

### Post by bhaskar on 2006-06-02
OK, it's in smbfs:

sh-3.1$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  smbfs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 378kB of archives.
After unpacking 909kB of additional disk space will be used.
Get: 1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main smbfs 3.0.22-1ubuntu3 [378kB]
Fetched 378kB in 1s (232kB/s)
Selecting previously deselected package smbfs.
(Reading database ... 137874 files and directories currently installed.)
Unpacking smbfs (from .../smbfs_3.0.22-1ubuntu3_i386.deb) ...
Setting up smbfs (3.0.22-1ubuntu3) ...
sh-3.1$ which smbmount
/usr/bin/smbmount
sh-3.1$

-- Bhaskar

---

### Post by Jamesmccloud on 2006-11-03
Sticky please. this was a pretty hard tidbit to locate! :KS 

anyway, to translate to noob: (nothing personal, fellow noobs)
what bhaskar just did was install a package which enabled support for smbfs. if you're anything like me, you probobly googled the commands to mount a windows share into linux, because, well, lets face it, you cant do anything in linux unless you mount it first. (freud would have a field day, lols)
you probobly got a lot of errors to the effect of:

```
mount: wrong fs type, bad option, bad superblock on //WINDOWS/SHARED,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
--this is because by default, ubuntu dapper does not install smbfs. you have to install it with the command bhaskar gave us, minus the "sh-3.1$" of course.

ps-looking back, this bit wasnt entirely on-topic, which was locating file packages, but im just really happy this worked after a week of googling. ](*,)

---

### Post by yellow beard on 2006-11-13
When i try to mount a share like this: ```
sudo mount -t smbfs //192.168.1.1/F ~/mnt
``` I get this result:

cli_negprot: SMB signing is mandatory and we have disabled it.
10151: protocol negotiation failed
SMB connection failed

What am i doing wrong?

---

