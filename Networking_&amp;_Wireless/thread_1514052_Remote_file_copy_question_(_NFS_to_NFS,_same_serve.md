---
title: "Remote file copy question ( NFS to NFS, same server)"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by nastysquar3d on 2010-06-20
I have two NFS mounted shares, both of them reside on the same server.

When I copy files from one mounted NFS share to another using Nautilus from a client computer (connected through 54g wireless) the copy goes painfully slow. What I'm assuming is happening is that the client computer is grabbing the file from the server, then putting it back on the server in the destination directory.

When I SSH into the machine and do a copy via command line it goes much faster.

Is my assumption correct? Is there some way to tell Nautilus to copy server to server and not server to client to server?

I'm Ubuntu 10.04 LTS on both the client and the server machines.

Thanks in advance.

---

### Post by cariboo on 2010-06-20
> **nastysquar3d said:**
> I have two NFS mounted shares, both of them reside on the same server.

When I copy files from one mounted NFS share to another using Nautilus from a client computer (connected through 54g wireless) the copy goes painfully slow. What I'm assuming is happening is that the client computer is grabbing the file from the server, then putting it back on the server in the destination directory.

When I SSH into the machine and do a copy via command line it goes much faster.

Is my assumption correct? Is there some way to tell Nautilus to copy server to server and not server to client to server?

I'm Ubuntu 10.04 LTS on both the client and the server machines.

Thanks in advance.

You're assumption is correct everything is running through nautilus, so the data is making a trip to the desktop computer and back to the server. I can't see a way of stopping that. 

I use mc, it is in the repositories, for doing most file operations on my server, just ssh into the server and start mc from the prompt.

---

### Post by nastysquar3d on 2010-06-21
Thanks for confirming my suspicions and suggesting mc

I installed it earlier today and it works wonderfully.

---

