---
title: "File sharing using nfs"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by Amy_1990 on 2010-08-04
I have tried to set up file sharing using ssh,samba with no luck.I now have it set up using NFS the only thing is it is just one way and i need it both ways.I was wondering if i installed the same packages on the other pc if i could make this work both ways.The command i used on the first pc was

sudo apt-get install nfs-kernel-server nfs-common portmap

and on the other pc the command was

sudo apt-get install nfs-common portmap

or is there a better way?

Thank you

---

### Post by drdos2006 on 2010-08-04
NFS is the way to go. Check this out.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

regards

---

### Post by Amy_1990 on 2010-08-04
I have nfs set up and working one way i just need to know how to make it work both ways do i install the nfs-server on both pc's to do this?

---

### Post by Joe of loath on 2010-08-04
What do you mean 'both ways'? Each having their own drives shared? That requires each to have its own nfs server running.

---

### Post by drdos2006 on 2010-08-04
No, you need to set up the server on one machine and the client on the second machine. Then you can make a directory on your client machine. map the server shared directory and the files can be exchanged between the server machine and the client machine.

regards

The server side files can be installed on a Desktop installation of Ubuntu, you do not need Ubuntu server to install the server files.

---

### Post by Amy_1990 on 2010-08-04
> **drdos2006 said:**
> No, you need to set up the server on one machine and the client on the second machine. Then you can make a directory on your client machine. map the server shared directory and the files can be exchanged between the server machine and the client machine.

regards

The server side files can be installed on a Desktop installation of Ubuntu, you do not need Ubuntu server to install the server files.


I can do from server machine to client machine what i am trying to do now is from client machine to server machine.Here is the guide i went by [http://tuxtweaks.com/2008/10/how-to-set-up-a-home-network-with-ubuntu-part-2/](http://tuxtweaks.com/2008/10/how-to-set-up-a-home-network-with-ubuntu-part-2/)

---

### Post by Joe of loath on 2010-08-04
Then you'll need to be able to set the permissions so that the client can modify the shared directory. try 'sudo chmod 777 /insert-nfs-directory-here'

---

### Post by Amy_1990 on 2010-08-04
Ok so thats what is wrong with my set up

Thank you so much

---

