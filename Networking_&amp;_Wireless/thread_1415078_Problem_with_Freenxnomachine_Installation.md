---
title: "Problem with Freenx/nomachine Installation"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by rhonaldmoses on 2010-02-24
Hi,

I am not exactly newbie with GNU/Linux, but definitely new to SSH/NX stuffs. I followed the below tutorials for installing FreeNX so that I can access my desktop like TeamViewer in windows.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

But I don't see the folder NX like the one mentioned here.

[CENTER]**Then edit the file /usr/NX/etc/server.cfg **
[/CENTER]

I don't see a folder called NX to proceed. Also when I use nomachine client to connect from Windows, it couldn't connect and I get the below errors.

***nxssh: <host-name>: no address associated with name.***

Any help on how to make connect to freenx server from windows using nomachine client?

Regards & Thanks,
Rhonald

---

### Post by Peter09 on 2010-02-24
NX uses ssh - you should be able to get to the server using a command like
 
```
ssh -Xv <username>@<machine name> 
```
 
replace machine name with ip address if necessary. The v gives you some debug information.
 
If you are on a windows machine try the PuTTY application for ssh.
 
Once you can connect with ssh then try NX.

---

### Post by derpishi on 2012-05-04
I used [http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html]("http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html") to install FreeNX on 12.04 LTS. It says it's installed. 

Can you help me verify it is installed and lead me down a path to get it working with windows nomachine client. right now it says SSH connection timed out. 

I do see a directory for /usr/NX

I also can not connect to SSH via PuTTY.

---

