---
title: "CIFS mount causes hard crash (Intrepid)"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by rmcd on 2008-12-03
I have no trouble with most CIFS mounts but one is causing my machine to freeze. I am executing the following command:

```
sudo mount -t cifs //servername/docs/ /mnt/servername -o user=name,domain=dname

```

The mount seems to connect properly and I am able to ls, cd, and so forth, a few times. After several cd and ls commands, however, my machine locks up hard and I have to reset with the power button. This is consistently reproducible from my laptop running 8.10, with smbfs version 2:3.2.3-lubuntu3.3. 

I can connect to this resource using nautilus without problem. Here is a description of the server I am trying to connect to (I got this from tech support):

> When you map servername now, you are actually mapping a pointer to a share on a storage device (the share is servername1\docs)
  
In Use Active   
Server Name servername1   
Server Function Administrative Shares/Home Directories   
Service Tag [redacted] 
Server Role APPLIANCE-NAS   
Service Level 1 High   
Operating System    
Server Model NetApp 3050   
 
The content on this device is served out using the recently deployed content management system (SiteCore) which runs on a pair of redundant Windows servers

Active   
Server Name servera and serverb   
Operating System Windows Enterprise Server 2003   
Server Model Dell PowerEdge 2950  

I assume there is a bug somewhere (nothing should cause a freeze) but I wonder how to narrow this down before reporting. 

Any and all suggestions appreciated. Thanks.

Bob

---

### Post by antoinv on 2009-01-20
I have excactly the same issue, and I've contributed to this bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=509428](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=509428)

I advise you to report the bug as well.
I recently upgraded one of my laptops to 8.10, and it crashes hard once I enter a share on one of the netapp servers at my work. I cannot even shut it down anymore, and have to remove the battery. I can connect well to Debian servers.
I still have laptops running 8.04, and they have no problem with the same netapp shares.

I would like to know if you also see the strange thing I see with the permissions in the share with 8.10 like I reported in the bug report.
When you do an ls -la in the top level of the share, is it writable ?

I consider this a critical issue, as we will not replace our netapps easily, and I can imagine there are more companies using these :-).

So I also wonder what options do I have:

-Do a downgrade and install 8.04 (another weekend configuring)
-Build a new kernel. Not prefered
-Install more recent Samba (does that solve the issue ?)
-Wait till 9.04 and hope it is solved 
-Use M$ windows XP for now 
-Something else ?

I cannot wait till April to get this solved, as I do have to do some work. I have the impression that the bug is not considered serious though, so that leaves me with the options of installing 8.04 or using XP. I hope somebody else has a better idea.

What would you do ?

Antoin

---

### Post by bgiannes on 2009-03-11
good god..  don't go back to XP

i just setup smbfs instead of cifs.

works great....  no more crashs

UPDATE
mmmmm......
still crashs, but only crashs the client PC

---

### Post by bgiannes on 2009-03-16
if i set the client PC to read-only on it's smb mounts the PC don't crash?

---

