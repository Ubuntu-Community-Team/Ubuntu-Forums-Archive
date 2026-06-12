---
title: "Samba folder over a shared network is rarely accessible"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by CorySimmons on 2013-04-13
I installed Ubuntu Server 12.04, Samba, configured smb.conf, added a Samba user, and restarted Samba, to create a shared folder between my VM guest (Ubuntu), and my host (Windows 7). I also set my Network to Bridged instead of NAT.

I was able to access \\UBUNTU for a while, but now I'm not able to, and it seems like randomly I'll be able to access \\UBUNTU for brief amounts of time.

I'm new to Ubuntu, Samba, VMs, and networking in general, so I tried making the VM's IP static in hopes it would fix this to no avail.

I'm at a complete loss and have worked on this for 3-4 days straight now.

Here's what I appended to smb.conf:

```

[my_share]
  path = /home/cory/apps
  read only = no
  admin users = cory

```

I get the feeling this is a problem with the network changing when other people connect to it, and/or some Samba settings.

---

### Post by TheFu on 2013-04-14
Rather than dealing with Samba, have you considered using the built-in file sharing that virtualbox supports?  It is pretty solid, if limited by the hostOS file system limitations on permissions, ownership and groups.

---

### Post by CorySimmons on 2013-04-14
I have, and I got them working, but I'm using the Meteor JS framework and have permission errors with MongoDB when I try to write to that folder. This error: [http://stackoverflow.com/questions/10103830/problems-to-run-examples-in-meteor](http://stackoverflow.com/questions/10103830/problems-to-run-examples-in-meteor)

I couldn't figure out if Mongo had an assigned user or what, but couldn't find any help with the error either.

Ordered a Mac. :(

---

### Post by TheFu on 2013-04-14
> **CorySimmons said:**
> I have, and I got them working, but I'm using the Meteor JS framework and have permission errors with MongoDB when I try to write to that folder. This error: [http://stackoverflow.com/questions/10103830/problems-to-run-examples-in-meteor](http://stackoverflow.com/questions/10103830/problems-to-run-examples-in-meteor)

I couldn't figure out if Mongo had an assigned user or what, but couldn't find any help with the error either.

Ordered a Mac. :(

Accessing a DB over a network file system is asking for failure and corruption of the DB.  NFS might handle it, but SMB/CIFS will not. You want to use a block device for remote DB access - something like iSCSI or BDB or AoE.   Or run a DBMS on the remote system and connect to it using normal network methods with whatever client/server method it supports.

There are probably some complexities that I'm missing in your setup that make this a bad idea too?

A Mac will not help you here.

---

### Post by CorySimmons on 2013-04-14
The setup in my original post works for writing to the db, but for some reason I just lose access to the share randomly. I'm 99.9% sure it has something to do with sharing the network with other people. Maybe an IP or some other thing is being refreshed or something. :\

The Mac will help in the sense that I won't be on Windows and Meteor works in native Mac/Linux environments.

---

### Post by TheFu on 2013-04-14
> **CorySimmons said:**
> The setup in my original post works for writing to the db, but for some reason I just lose access to the share randomly. I'm 99.9% sure it has something to do with sharing the network with other people. Maybe an IP or some other thing is being refreshed or something. :\

The Mac will help in the sense that I won't be on Windows and Meteor works in native Mac/Linux environments.

I'm 99.99999999999% certain the issue with the DB losing access is due to using samba shares with a database.  Some text editors fail when using file shares over Windows or samba too. Network file locking is "different" than local file locksor block storage file locking.  NTFS shares are not designed for this.

Regardless .... let's take the DB out of this picture and troubleshoot purely network file access.

Do both systems know how to find each other directly?  Did you edit the /etc/hosts files on both the hostOS and clientOS with the correct static IP addresses? Are both on the same subnet? We need to avoid having any router in the middle between the two OS installs.

Does the **testparm** tool return no errors?  Can you post the non-commented smb.conf that testparm outputs?  The simplified version would be best - about 20 lines.

Do the samba and nmbd log files provide any help?  They are in /var/log/samba/, I believe.  You can run smbd -vvvv to get lots of information. Check the man page to verify the actual verbose switch.

---

### Post by CorySimmons on 2013-04-15
So far as the db access thing, I'm pretty positive that's a problem when I'm using Guest Addition Devices > Shared Folders, but when I'm using a Samba share, it doesn't seem to be a problem. That is... when I'm using the Samba share and I can connect to the guest machine via the network, I have no problem with Mongo writing to the shared folder. The problem is, I'm only able to detect the \\UBUNTU Samba share rarely.

I haven't changed the /etc/hosts file on the Ubuntu guest, but I did change the /etc/networks/interfaces file to have a static IP on the guest, and I did change the hosts file on my Windows host to have the same IP. This might be a problem. The /etc/hosts file on my guest system looks like this: [http://i.imgur.com/nnwFLyf.jpg](http://i.imgur.com/nnwFLyf.jpg) Should I change the "localhost" and/or "ubuntu" to match the static IP?

testparam isn't a command on my system. Isn't it bundled with apt-get samba? Regardless, the only thing I've changed in smb.conf is I appended this to the end of smb.conf:

```

[my_share]
  path = /home/cory/apps
  read only = no
  admin users = cory

```

I've also ensured my workgroup is the same on guest/host (WORKGROUP).

Here's my log.nmbd: [http://i.imgur.com/bNwjEDq.jpg](http://i.imgur.com/bNwjEDq.jpg)

And the log.smbd: [http://i.imgur.com/BTHYKHz.jpg](http://i.imgur.com/BTHYKHz.jpg)

I'm not sure how to interpret them. :(

(funny, I'd copy/paste from PuTTY if I could connect to the network, but I can't copy/paste on Ubuntu Server even with Guest Additions/gpm so I just have to tape together screenshots for now)

smbd -vvv (V V V?) returns invalid argument.

---

### Post by TheFu on 2013-04-15
It seems that you may need basic networking help at this stage of the issue. [http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/](http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/) should help with the mechanics.  Until that is handled, samba cannot work correctly.

In short, the machines need to be 
a) on the same subnet (not just 127.0.0.1 or localhost) 
b) on different IPs
c) able to resolve each other in a bi-directional way - /etc/hosts is usually how that happens.
I'm amazed that anything works at all without this configured.

Just to check things, since I could be wrong, what is the output of **ifconfig **and **ipconfig **on the Ubuntu/Windows machines, respectively?

---

### Post by gorkypah on 2013-04-15
...

---

### Post by CorySimmons on 2013-04-15
I can't follow the directions on sudo-juice because apparently my VM no longer has internet access either... ugh...

I did, however, set all those things (except the prefix) in /etc/network/interfaces: [http://i.imgur.com/SG2wOBS.jpg](http://i.imgur.com/SG2wOBS.jpg) and do the service restarts.

a) I have the same subnet mask (255.255.255.0) but I'm not sure how to check and see what the subnet itself is...
b) They see to have different IP's
c) Not sure how to make them resolve each other in a bi-directional way. :(

Here's the ip/ifconfig: [http://i.imgur.com/ccBterh.jpg](http://i.imgur.com/ccBterh.jpg)

---

### Post by gorkypah on 2013-04-15
...

---

### Post by CorySimmons on 2013-04-15
Kinda nervous to be showing off all my IP stuff and changing security options in registry without fully understanding it or having others chime in.

---

### Post by gorkypah on 2013-04-15
...

---

