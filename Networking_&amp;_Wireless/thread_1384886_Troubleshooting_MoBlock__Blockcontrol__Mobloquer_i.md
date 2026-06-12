---
title: "Troubleshooting MoBlock / Blockcontrol / Mobloquer install"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by slowrolling on 2010-01-18
Hi all,

I'm pretty new to linux and have been trying to troubleshoot a moblock/blockcontroll install error I am getting under Ubuntu 9.10

I followed these instructions, and used aptitude to install.
[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

The first error I can see when I installed is "invoke-rc.d: initscript blockcontrol, action "start" failed."
any help or suggestions are appreciated log is here:

> 
bill@penguin:~$ sudo aptitude install moblock blockcontrol mobloquer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  blockcontrol libaudio2{a} libnetfilter-queue1{a} libnfnetlink0{a} libqtcore4{a} 
  libqtgui4{a} moblock mobloquer p7zip{a} 
0 packages upgraded, 9 newly installed, 0 to remove and 178 not upgraded.
Need to get 5,980kB of archives. After unpacking 18.6MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  moblock mobloquer blockcontrol 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
Get:1 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) intrepid/main moblock 0.9~rc2-23~intrepid [36.0kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libnfnetlink0 0.0.41-1 [14.0kB]
Get:3 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) intrepid/main blockcontrol 1.6.9-1~intrepid [94.5kB]
Get:4 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) intrepid/main mobloquer 0.6+svn20090817-1~intrepid [262kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libnetfilter-queue1 0.0.17-1 [8,564B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libaudio2 1.9.2-1 [84.6kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libqtcore4 4.5.3really4.5.2-0ubuntu1 [1,505kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libqtgui4 4.5.3really4.5.2-0ubuntu1 [3,617kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe p7zip 9.04~dfsg.1-1 [359kB]
Fetched 5,980kB in 5s (1,175kB/s)    
Preconfiguring packages ...
Selecting previously deselected package libnfnetlink0.
(Reading database ... 116781 files and directories currently installed.)
Unpacking libnfnetlink0 (from .../libnfnetlink0_0.0.41-1_i386.deb) ...
Selecting previously deselected package libnetfilter-queue1.
Unpacking libnetfilter-queue1 (from .../libnetfilter-queue1_0.0.17-1_i386.deb) ...
Selecting previously deselected package moblock.
Unpacking moblock (from .../moblock_0.9~rc2-23~intrepid_i386.deb) ...
Selecting previously deselected package blockcontrol.
Unpacking blockcontrol (from .../blockcontrol_1.6.9-1~intrepid_all.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9.2-1_i386.deb) ...
Selecting previously deselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package mobloquer.
Unpacking mobloquer (from .../mobloquer_0.6+svn20090817-1~intrepid_i386.deb) ...
Selecting previously deselected package p7zip.
Unpacking p7zip (from .../p7zip_9.04~dfsg.1-1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
Processing triggers for desktop-file-utils ...
Setting up libnfnetlink0 (0.0.41-1) ...

Setting up libnetfilter-queue1 (0.0.17-1) ...

Setting up moblock (0.9~rc2-23~intrepid) ...
Setting up blockcontrol (1.6.9-1~intrepid) ...

moblock will soon be started ...
If any blocklists are missing, they will be downloaded. This may take several
minutes. Please be patient and don't abort. If you want to follow the update
process, then do in another terminal a
 tail -f /var/log/blockcontrol.log
The lists are saved to /var/spool/blockcontrol/.
The installation of blockcontrol will fail, if starting moblock fails. So if
downloading the blocklists fails temporarily, the installation will fail.
To workaround this, you can turn the automatic starting of moblock off by setting
in /etc/blockcontrol/blockcontrol.conf:
 INIT="0"
Please be patient ...
Starting IP block daemon: moblock failed!
invoke-rc.d: initscript blockcontrol, action "start" failed.
dpkg: error processing blockcontrol (--configure):
 subprocess installed post-installation script returned error exit status 8
Setting up libaudio2 (1.9.2-1) ...

Setting up libqtcore4 (4.5.3really4.5.2-0ubuntu1) ...

Setting up libqtgui4 (4.5.3really4.5.2-0ubuntu1) ...

dpkg: dependency problems prevent configuration of mobloquer:
 mobloquer depends on blockcontrol; however:
  Package blockcontrol is not configured yet.
dpkg: error processing mobloquer (--configure):
 dependency problems - leaving unconfigured
Setting up p7zip (9.04~dfsg.1-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
           Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 blockcontrol
 mobloquer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up blockcontrol (1.6.9-1~intrepid) ...

moblock will soon be started ...
If any blocklists are missing, they will be downloaded. This may take several
minutes. Please be patient and don't abort. If you want to follow the update
process, then do in another terminal a
 tail -f /var/log/blockcontrol.log
The lists are saved to /var/spool/blockcontrol/.
The installation of blockcontrol will fail, if starting moblock fails. So if
downloading the blocklists fails temporarily, the installation will fail.
To workaround this, you can turn the automatic starting of moblock off by setting
in /etc/blockcontrol/blockcontrol.conf:
 INIT="0"
Please be patient ...
Starting IP block daemon: moblock failed!
invoke-rc.d: initscript blockcontrol, action "start" failed.
dpkg: error processing blockcontrol (--configure):
 subprocess installed post-installation script returned error exit status 8
dpkg: dependency problems prevent configuration of mobloquer:
 mobloquer depends on blockcontrol; however:
  Package blockcontrol is not configured yet.
dpkg: error processing mobloquer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 blockcontrol
 mobloquer
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done


---

### Post by jre on 2010-01-19
[same thread also here: [http://forums.phoenixlabs.org/showthread.php?p=129045]](http://forums.phoenixlabs.org/showthread.php?p=129045])

You added a wrong entry to your /etc/apt/sources.list. Your distribution seems to be **karmic**, but it looks as if you added **intrepid** sources of moblock-deb to the file.
So the correct entry for you is
```
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
```
You definitely should change this! Then update your package manager (you have to download the new package lists. If you were using aptitude as package manager, you had to type [FONT="Courier New"]sudo aptitude update[/FONT]), and then try the install again.

Now, if this doesn't help, I noticed another thing: your post shows error 8, which means that something with iptables caused errors. To see what this was exactly you have to look at /var/log/blockcontrol.log.

---

### Post by Primary Consult on 2011-10-26
I realize this is an old thread however I had run into the exact problem the OP had, and solved it, so I hope this helps someone else.
When it asked for whitelisting ports, I used "http https dns"; apparently dns is not a real alias.  This caused iptables to fail, and the log would say:
```
Inserting iptables ...
iptables: Chain already exists.
 failed!
```

Just clearing that up in blockcontrol.conf and running:
```
blockcontrol stop; blockcontrol start
``` solved it.

---

