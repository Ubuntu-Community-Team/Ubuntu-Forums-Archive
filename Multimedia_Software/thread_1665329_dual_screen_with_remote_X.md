---
title: "dual screen with remote X"
date: 2011-01-12
forum: Multimedia Software
---

### Post by orionzrh on 2011-01-12
Hi all,

i need a little bit of help. I have a problem with a Intel Corporation  82945G/GZ Integrated Graphics Controller.
My xorg.conf is working good. I get the second screen running in the  cinerama mode. But when i make a ```
X :2 -query IP ADDRESS
``` i  get the connection but not with the  cinerama mode.
I did this also with CENTOS and it worked. 
This is the error message when i execute the command.

> _XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/admin7:2
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
XDMCP warning: INET6 UDP socket creation failed

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux admin7 2.6.35-24-generic #42-Ubuntu SMP  Thu Dec 2 01:41:57 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic  root=UUID=15dd80f4-c42b-43d0-b956-b229f8c659b9 ro ipv6.disable=1 quiet  splash
Build Date: 23 November 2010  09:54:06PM
xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.18.4
        Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Wed Jan 12 11:11:14 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Requested Entity already in use!
(EE) Screen 1 deleted because of no matching config section.
Can someone help me with this issue? I'm stocking at the moment  and i do not see any errors.
I also attached the xorg.conf file. maybe something is wrong in the  file.

Thanks for your help

---

