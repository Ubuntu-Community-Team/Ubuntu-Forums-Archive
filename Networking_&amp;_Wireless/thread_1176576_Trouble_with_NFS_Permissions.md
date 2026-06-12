---
title: "Trouble with NFS Permissions"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by King_Koopa on 2009-06-02
On my Ubuntu 9.04 Server I have successfully installed the NFS Server, and configured */etc/exports* as follows:

/home/linux-share *(rw,sync,no_root_squash)

On my Ubuntu 9.04 Client machine I have successfully mounted the NFS share to the desktop, but when I attempt to write anything to the folder I am denied permission.

Why do I not have write permissions even though I have set it up so that I should? I have checked the uid for both the server and the client, and they both sync up fine.

What else is there to check?

---

### Post by King_Koopa on 2009-06-02
I solved the problem by changing the folder's permissions on the server.

*On Ubuntu 9.04 Server:*
```
sudo chown root:users /home/linux-share
```

Now users can read and write to the NFS share. If anyone else was looking for the answer, I hope this helps.

---

### Post by freakalad on 2009-06-06
Have a similar problem, and missing something simple yet crucial.
Jaunty-64. Tried a few options/combinations:

Host /etc/exports :
/media/vm/vm.data 10.0.0.0/24(rw,sync,no_subtree_check)
or
/media/vm/vm.data 10.0.0.0/255.255.255.0(rw,sync,no_subtree_check)

Client /etc/fstab :
10.0.0.100:/media/vm/vm.data /media/vm.data nfs suid,dev,exec,rw  0 0
or
10.0.0.100:/media/vm/vm.data /media/vm.data nfs defaults 0 0

Tried changing permissions & ownership of host, but still getting the same results.

What am I missing?

---

