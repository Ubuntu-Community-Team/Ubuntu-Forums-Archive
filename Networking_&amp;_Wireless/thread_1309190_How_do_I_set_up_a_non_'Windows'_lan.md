---
title: "How do I set up a non 'Windows' lan?"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by bwallum on 2009-11-01
Hi

I want to set up a wired local area network to connect four machines. The computers will be allowed to access various folders on other machines.

When I try to 'share' a folder I get this message.> You need to install the Windows networks sharing service in order to share your folders.When I follow the prompt to install I am told I need to fix broken packages first. In synaptic, there are no broken packages.

Is their any other mainstream way to set up a small lan?

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
what os do the clients run

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
if ur using linux and maybe mac u could use only NFS or NIS for windows you need SAMBA

sudo apt-get install samba smbclient
sudo apt-get install nfs-client nfs-server
 i think

linux also supports samba but i use all 3

---

### Post by bwallum on 2009-11-01
All machines running karmic. Is Samba Winows (i.e. MS) propietory?

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
you could use samba if you wish but it can be hard 2 configure and its slower than nfs ,personally i would still go for samba though as i would say there is more documentation on its setup around and if you ever have a windows machine you can connect 2 ur server

---

### Post by bwallum on 2009-11-01
Thanks for that, I found [http://www.samba.org/](http://www.samba.org/) and discovered that samba is open source. I'll take your advice and go down the samba route, get the network working, then play with nfs [http://nfs.sourceforge.net/](http://nfs.sourceforge.net/) later.

Thanks for the steer,
Rgds, Bob

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
kk

---

### Post by Iowan on 2009-11-01
Most of the client software comes pre-installed, but to share FROM the machine will require installing the server portion of Samba, NFS, SSH, or whatever protocol you choose. If you opt for Samba (although [NFS]("http://ubuntuforums.org/showthread.php?t=249889") is more native), there are several good How-To's available -  [this]("http://ubuntuforums.org/showthread.php?t=202605") one is a good place to start.

---

