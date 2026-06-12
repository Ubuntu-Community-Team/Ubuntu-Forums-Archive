---
title: "Networking - Smaba, SSH, FTP which one?"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by Ordes on 2009-07-18
When i started with Ubu i used samba to share my files between my Laptop and PC. But sometimes Samba doesnt really satisfy me, specially when u need stuff that is not shared yet... So i tried SSH. And i really like it. But of course i see the possibulity of exploit. And all those pages in the www are pointing it out to.

My question:
1. My network is behind a router. with firewall on and no ports forwarded

How secure is this? are people still able to scan through my router? and find my ssh?

I also changed the ssh default ports, and in firestarter only allowed ssh/port/IP. With ssh/port/IP the only open inbound port allowed for one certain IP

2. Is there a option to just allow ssh for inner network IPs.

3. Or is there something else that only allows me something like the file managment of SSH, without the ability of become a remote user?

4. SSH keys: Tried to figure it out. But always when i read through the instructions getting confused.
is it:
A) Server: a) create key b) copy publicKey to the machines u want to connect from (thats what i thought it should be.. but when i read through the instructions it sound like)
B) MyPC: a) create key b) copy publicKey to server u want to connect to

If b is right, how do i:
1) create multiple public keys, for my laptop and pc and how unite them in server?

-----
Or should i just use FTP, for the file sharing? But than again.. people say ftp is not secure... sftp is... but sftp is as far as i see connect to ssh.. so i will still need ssh... and as it seems... mounted ftp is also not browsable for some apps..

What i want is basiclly for my two PCs to connect, share the files, without opening the whole command prompt to others...


thanks

---

### Post by mr.josep on 2009-07-18
Hi:
If your computers are in the same net without firewalls between then, you can use NFS to share files.
To share files using NFS, on the computer that exports them, you must file on /etc/exports the directories you want to export and the computers & rights you want to export to.
NFS is better than samba because of security on files: on remore system, you put owner/group and mode on every file as in local one.
Regards

---

### Post by enz1m3 on 2009-07-19
1. If people learn your external IP at the moment they can get to your router (I don't know if it allows external login or not) but not necessarily login and certainly not scan ssh unless they've logged into the router and sniffed the network.

2. I'm sure there is a way to do that, probably with iptables, but I'm sure someone out there knows more about it than me.

3. NFS would be a good choise, like mr.josep said, but FTP would also be, and imo, it's easier to setup and if you're working just within your internal network (no external "sniffers" lurking on it), that's not unsecure.

4. Again, not sure, but I believe it's A. But you can't trust me on this one, wait for someone more experienced on this particular issue to reply.

---

### Post by Ordes on 2009-07-19
txs so far...

pretty meets with my thoughts...

My router doesnt allow external login...

----------

thinking about ftp... the only thing u seem to not be able to mount your drive with ftp like u can with ssh+fuse...

----------
i think i basicly got the concept... except for the keys....

but now my mind boggles about firewalls...

[http://ubuntuforums.org/showthread.php?p=7644015#post7644015](http://ubuntuforums.org/showthread.php?p=7644015#post7644015)

any ideas?

thanks again

---

### Post by Ordes on 2009-10-20
..txs...

just using ssh now.. its awesome when you get into it.. 

just they keys are not working yet... but as i am only on a home network.. i dont mind using first login/pass

---

