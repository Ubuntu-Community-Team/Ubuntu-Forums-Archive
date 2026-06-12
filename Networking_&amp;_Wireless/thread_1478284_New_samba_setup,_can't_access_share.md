---
title: "New samba setup, can't access share"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by mfcallahan on 2010-05-09
Hello all, I've been searching through many a posts here and have found some similar threads, but nothing thus far to solve my problem.  Here's the low down: I'm running Karmic, newly installed with the lastest version of Samba.  Here is my (very basic) smb.conf:

[global]
    netbios name = MATTSERV-SERVER
    guest account = guest
    writeable = yes
    workgroup = MSHOME
    os level = 20
    username map = /etc/samba/user.map
    encrypt passwords = true
    create mode = 777
    public = yes
    directory mode = 777

[share]
path = /home/mattserv/Shared
comment = Shared files

Right clicking the "Shared" folder in /home/mattserv/ gives the following error when attempting to setup a share: 'net usershare' returned error 255: net usershare add: cannot convert name 'Everyone' to a SID.  Memory allocation error.

Restarting Samba from the command line (/etc/init.d/samba restart) gives the following messgae:
*Stopping Samba daemons
start-syop-daemon: warning: failed to kill 2154: No such process
*Starting Samba daemons

/etc/init.d/samba status indicates:
* nmbd is running
* smbd is not running

Webmin indicates everything is running normally, though when attemping to connect to the server through another linux machine, I am able to see the server on the network and see the "Shared" folder.  I get this message when attempting to connect: Unable to mount location.  Failed to mount Windows share.

I've set up samba many times usually with minimal problems, though this time I am stumped...    

Matt

---

### Post by mfcallahan on 2010-05-09
Posted this in the wrong category initially:

Hello all, I've been searching through many a posts here and have found some similar threads, but nothing thus far to solve my problem. Here's the low down: I'm running Karmic, newly installed with the lastest version of Samba. Here is my (very basic) smb.conf:

[global]
    netbios name = MATTSERV-SERVER
    guest account = guest
    writeable = yes
    workgroup = MSHOME
    os level = 20
    username map = /etc/samba/user.map
    encrypt passwords = true
    create mode = 777
    public = yes
    directory mode = 777

[share]
path = /home/mattserv/Shared
comment = Shared files

Right clicking the "Shared" folder in /home/mattserv/ gives the following error when attempting to setup a share: 'net usershare' returned error 255: net usershare add: cannot convert name 'Everyone' to a SID. Memory allocation error.

Restarting Samba from the command line (/etc/init.d/samba restart) gives the following messgae:
*Stopping Samba daemons
start-syop-daemon: warning: failed to kill 2154: No such process
*Starting Samba daemons

/etc/init.d/samba status indicates:
* nmbd is running
* smbd is not running

Webmin indicates everything is running normally, though when attemping to connect to the server through another linux machine, I am able to see the server on the network and see the "Shared" folder. I get this message when attempting to connect: Unable to mount location. Failed to mount Windows share.

I've set up samba many times usually with minimal problems, though this time I am stumped...    

Matt

---

### Post by mfcallahan on 2010-05-09
Also, no firewall running at the moment...

---

### Post by mfcallahan on 2010-05-09
Also, no firewall running at the moment...

---

### Post by rkd2398 on 2010-06-01
I am having the same problem, any one have any ideas on this?

---

### Post by capscrew on 2010-06-02
> **rkd2398 said:**
> I am having the same problem, any one have any ideas on this?

Is your install configured the same as the OP?  It would be best if you start your own thread and explain what you have done so far.

---

### Post by cariboo on 2010-06-02
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by capscrew on 2010-06-02
> **mfcallahan said:**
> Hello all, I've been searching through many a posts here and have found some similar threads, but nothing thus far to solve my problem.  Here's the low down: I'm running Karmic, newly installed with the lastest version of Samba.  Here is my (very basic) smb.conf:

[global]
    netbios name = MATTSERV-SERVER
    guest account = guest
    writeable = yes
    workgroup = MSHOME
    os level = 20
    username map = /etc/samba/user.map
    encrypt passwords = true
    create mode = 777
    public = yes
    directory mode = 777

[share]
path = /home/mattserv/Shared
comment = Shared files

Right clicking the "Shared" folder in /home/mattserv/ gives the following error when attempting to setup a share: 'net usershare' returned error 255: net usershare add: cannot convert name 'Everyone' to a SID.  Memory allocation error.

Restarting Samba from the command line (/etc/init.d/samba restart) gives the following messgae:
*Stopping Samba daemons
start-syop-daemon: warning: failed to kill 2154: No such process
*Starting Samba daemons

/etc/init.d/samba status indicates:
* nmbd is running
* smbd is not running

Webmin indicates everything is running normally, though when attemping to connect to the server through another linux machine, I am able to see the server on the network and see the "Shared" folder.  I get this message when attempting to connect: Unable to mount location.  Failed to mount Windows share.

I've set up samba many times usually with minimal problems, though this time I am stumped...    

Matt

Matt,

You are using multiple methods of configuring Samba.  Sometimes they conflict.  If you are using the GUI then don't configure via the smb.conf file.  Usershares are usually configured by using the Nautilus GUI. 

If you want to configure via the smb.conf file then no usershares configuration is needed.  

I have never used Webmin and it is not part of the repos.  I know that it can significantly modify how Ubuntu functions.

My advice is to select one method of configuring Samba and see what happens.  This might include you having to reinstall.

---

