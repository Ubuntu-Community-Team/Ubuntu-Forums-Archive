---
title: "NFS File Sharing"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2011-02-13
I was looking through this book, "A Practical guide to Ubuntu Linux," and I was interested in a NFS files system for my setup.

My question is: 

Let's say I want all of the /home/user directories on this server.  How would I install/setup a new Ubuntu installation on the client machine to work this way?  How would the user log on this client machine without the /home/user directory on the client?  Would the user be logging in using LDAP and then the file system would connect?  Is there some file that is associated with the boot process that tells the client to connect to /home/ben if ben logs on?

I'm just really fuzzy on how this stuff works.

Thanks.

---

### Post by movieman on 2011-02-13
The simple solution is to configure the automounter so that it will automatically mount /home/user if you try to access it.

---

### Post by pepsifx357 on 2011-02-13
Ok, just so I get the whole picture this is what I do?

On the client machine I install Autofs.  I change the /etc/auto.master.

According to the community document, I should add the line to /etc/auto.master that says:

/nfs   /etc/auto.nfs

This line will point to a file that I have to make.

So I make the file /etc/auto.nfs and create a line that says something like:

server   10.10.10.101:/home/ben

This is so that when the computer starts it looks for the server at 10.10.10.101 to have /home/ben and then mount it. Right?

Now when I'm installing Ubuntu on this machine and create a user ben, do I need to delete the /home/ben on the client machine to make room for the server's /home/ben to be mounted?  I'm confused as to how the computer handles the /home folder.

---

