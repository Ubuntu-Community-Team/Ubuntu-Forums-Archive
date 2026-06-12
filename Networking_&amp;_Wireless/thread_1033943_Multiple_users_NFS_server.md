---
title: "Multiple users NFS server"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by anonymousnobody on 2009-01-07
I don't know what to call it, so I'll just describe it.

I have 3 computers running various versions of Ubuntu and I want to consolidate all data files onto 1 computer. Computer A will hold all data (i.e. /home). I want login to Computer B and mount Computer A's /home as Computer B's /home. Computer B will have its own programs installed locally on its hard drive, but will save all data to Computer A's /home. The same goes for Computer C, D, etc. 
(A side note: Computer A's /home stored on physically separate hard drive, say /dev/sdb for example, whereas all the other folders /boot, /usr, etc are on /dev/sda)

I have already set up an NFS server on Computer A ([http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)). I have also installed an NFS client on Computer B. However, I will not the only user of these computers. There will be several users, say 5 total users. They should be able to access their own /home from any computer (A, B, C, etc.) 

I have sort of got NFS server and client to work. However, I noticed that I can created files in someone else's /home (i.e. I can create a file in bob's home even though I am login in as john and the permissions are set such that I should not be able to.) Maybe I don't have it configured correctly.

Another problem I encountered is that NFS requires all computers (A, B, C, D, etc) to have consistent login ID's on all machines. That means I have to hand create new users and make sure they all have the same ID's. Is there a way to create say a login server that will allow users to access /home once they have been verified by the login server?

Lastly, I have not been able to figure out how to replace Computer B's /home with Computer A's home. I am able to mount it as /home2.

So to summarize, I want to create a smaller version of a login system they have at university. Such that I am able to login in from a different workstation but retain changes I make to their home directory. I know some remote login programs already exist like xdmcp or vncviewer, but those programs use up a lot of bandwidth and offload the processing onto the remote machine. I want to keep the load on the local machine and minimize bandwidth usage by not sending tons of graphical data (like the data vnc and xdmcp send).

It doesn't have to be NFS. I only thought of NFS because I don't of any other options. If you know of an alternative to what I describe, that is good too.

I'm not trying to set up a file sharing server, rather a multi-user login kind of system. Like at work or school. Kind of like an ssh server, but a graphical login and when you login you will be able to mount Computer A's /home locally.

Thanks in advance for your help.

---

### Post by 2hot6ft2 on 2009-01-07
Maybe these 2 will help. The NFS is first.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

Sounds like what you're after is a server that 5 workstations can log onto. Basically.
I don't know if those links will help much or not but I'm sure someone here can.

---

### Post by albinootje on 2009-01-07
> **anonymousnobody said:**
>  I have sort of got NFS server and client to work. However, I noticed that I can created files in someone else's /home (i.e. I can create a file in bob's home even though I am login in as john and the permissions are set such that I should not be able to.) Maybe I don't have it configured correctly.


The problems you describe are known "problems" with NFS.
The uid differences per computer that is.

You can solve the uid problems by using NIS (pretty simple) or LDAP (quite complex) as a centralized user authentication setup, which would run on your data server.

Concerning the permissions :
It comes from a long tradition of sharing files that new users in /home can actually *look* into each others home directories. 
But writing should normally not be possible. 
It must be the different uid which lets you write into the other user's home dir.

You can change that easily :
```

sudo chmod 700 /home/*

```
Now your users cannot cd into the other users directories anymore.
In some computers I've put that command in /etc/rc.local just like
```

sudo chmod 700 /root/

```

There's the package ugidd, I've tried it years ago, but at that time I couldn't manage to make that working well. Just FYI.

> 
Description: NFS UID mapping daemon
 This package contains the UID mapping daemon (rpc.ugidd) which is used on
 NFS clients to do UID/GID mapping.


---

### Post by dougpan on 2009-01-07
Not sure if this is what you want but... you may want to try generating some ssh keys that don't require user login that keeps the many servers in sync using rsync?

You can have individual security but rsync can run in behind the scene.
No one would have the rsync keys but you.

The you can have users login to any server anywhere and all the data will be synchronized by you using a cron job that calls rsync every 15 to 30 minutes or so.

Computer A <-+
                              |
                              +------  rsync ---+    
                                                                   |
Computer B  <-+---------------+
                              |
                              +------  rsync ---+
                                                                   |
Computer C  <-----------------+

Check out the command
rsync -av -e ssh [email]james@mycomputer.dyndns.org[/email]:./*.* .

The above command will typically get all files in the users home area and move them to  whatever area the rsync command is calling from because of the single dot at the end.

Check out the command
ssh-keygen -t rsa

Check out: [http://www.petefreitag.com/item/532.cfm](http://www.petefreitag.com/item/532.cfm)

Doug

---

### Post by anonymousnobody on 2009-01-08
> **2hot6ft2 said:**
> 
Sounds like what you're after is a server that 5 workstations can log onto. Basically.


Yes, I guess basically I want to set up a server that multiple workstations can log onto. But only to access data, not to do the processing.

The first link ([https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)) helped. I was able to install autofs and following the steps I was able to "replace" the local /home with the remote /home.

I'll look into NIS next.

---

### Post by anonymousnobody on 2009-01-08
> **2hot6ft2 said:**
> 
Sounds like what you're after is a server that 5 workstations can log onto. Basically.


Yes, I guess basically I want to set up a server that multiple workstations can log onto. But only to access data, not to do the processing.

The first link ([https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)) helped. I was able to install autofs and following the steps I was able to "replace" the local /home with the remote /home.

I'll look into NIS next.

---

### Post by anonymousnobody on 2009-01-22
> **albinootje said:**
> The problems you describe are known "problems" with NFS.


What do you mean "known" problems? Meaning NFS was implemented that way? or that no one has written a patch to fix these problems?

---

### Post by albinootje on 2009-01-22
> **anonymousnobody said:**
> What do you mean "known" problems? Meaning NFS was implemented that way? or that no one has written a patch to fix these problems?

I don't know the exact history of NFS, but I did mention ugidd before, here are two related links :
[http://blog.cfrq.net/chk/archives/2008/03/12/rpcugidd/](http://blog.cfrq.net/chk/archives/2008/03/12/rpcugidd/)
[http://tldp.org/LDP/nag2/x-087-2-nfs.daemons.html](http://tldp.org/LDP/nag2/x-087-2-nfs.daemons.html)

---

### Post by anonymousnobody on 2009-01-28
I somehow foobar'ed the installation of nis. 

I set up nis on 2 computers. A is the server, B is the client. I rebooted B and now when I try to login via gdm it tells me that it can't find my home directory.

Restarting nis fails.
```
bash$ sudo /etc/init.d/nis restart
* Starting NIS services
* binding to YP server...     
* .... 
* .... 
* ....                                                                         
* ....                                              [fail]
```

I've tried double checking the conf files (/etc/yp.conf, /etc/ypserv.securenets) I've even tried to apt-get autoremove nis. But none of it works. Right now, I just want to be able to revert back (being able to log into the client directly and load its home directory).

---

### Post by albinootje on 2009-01-28
> **anonymousnobody said:**
> I somehow foobar'ed the installation of nis. 

Was it working before ?
> 
I've tried double checking the conf files (/etc/yp.conf, /etc/ypserv.securenets) 

Did you follow the documentation from /usr/share/doc/nis/ or something else ?

---

### Post by anonymousnobody on 2009-01-28
> **albinootje said:**
> Was it working before ?


Did you follow the documentation from /usr/share/doc/nis/ or something else ?

No, I wasn't able to get it to work at all. I was following the directions on a webpage, but since there are no longer any directories in /home, I can't cite the url.

So I tried reconfiguring with a different set of instructions: ([http://ubuntuforums.org/showthread.php?t=348015](http://ubuntuforums.org/showthread.php?t=348015)) to , but that didn't work either.

Why would all the home directories be missing anyway? Just because it wasn't able to bind should be any reason they are missing. Does this have more to do with automounting nfs?

The config files for both server and client are below. I am pretty sure /etc/hosts is config'ed correctly since I can ping and ssh with just the hostnames. Running sudo /etc/init.d/nis restart from the server also fails.

Server config files:

This is /etc/yp.conf. I am not sure it is configured correctly.
```

#
# yp.conf       Configuration file for the ypbind process. You can define

# ypserver ypserver.network.com
domain mydomain.com server myservername
```

```
#
# securenets    This file defines the access rights to your NIS server

# Always allow access for localhost
255.0.0.0       127.0.0.0
255.255.255.0   IP of myclient
255.255.255.0   IP of myserver


```

```
#
# /etc/defaults/nis     Configuration settings for the NIS daemons.
#

# Are we a NIS server and if so what kind (values: false, slave, master)?
NISSERVER=master

# Are we a NIS client?
NISCLIENT=false

```

Client config files:
```
#
# yp.conf       Configuration file for the ypbind process. You can define

# ypserver ypserver.network.com
IP of myclient myclient.mydomain.com

```

```
#
# /etc/defaults/nis     Configuration settings for the NIS daemons.
#

# Are we a NIS server and if so what kind (values: false, slave, master)?
NISSERVER=false

# Are we a NIS client?
NISCLIENT=true

```

---

### Post by anonymousnobody on 2009-01-29
Deleted.

---

### Post by albinootje on 2009-01-29
> 
Was it working before ?


Did you follow the documentation from /usr/share/doc/nis/ or something else ?
---End Quote---
No, I wasn't able to get it to work at all. I was following the directions on a webpage, but since there are no longer any directories in /home, I can't cite the url.

Please start from scratch and use the instructions in /usr/share/doc/nis/
It's a gzipped file which needs to be gunzipped, or use zless or zcat to read it.
And if the NFS automounting of your /home is a problem, try adding an user with /tmp or /home2 as home dir for testing.

---

