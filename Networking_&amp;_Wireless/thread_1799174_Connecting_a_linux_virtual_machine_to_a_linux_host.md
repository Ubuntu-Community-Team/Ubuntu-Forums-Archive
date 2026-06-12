---
title: "Connecting a linux virtual machine to a linux host via NFS"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by lauriane on 2011-07-07
Hi,
I am currently running ubuntu on a qemu-kvm virtual machine, and the host is fedora.
I would like to mount a folder of the host machine on my VM, but never succeeded.
The result of the command is :

root@armnlib-kvm:~# mount -v 192.168.1.10:/nfs /nfs
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Thu Jul  7 06:02:43 2011
mount.nfs: text-based options: 'addr=192.168.1.10'
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.1.10:/nfs

And the showmount -e on the host gives :

Export list for cudak:
/nfs                        10.0.2.15

Does someone have an idea to solve my pb ?
Thanks !

---

### Post by HermanAB on 2011-07-07
Maybe this will help:
[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

---

### Post by lauriane on 2011-07-08
Ok, thanks, but the pb was due to redirection port, since VM and host have the same ip-address. 
Launching the VM with qemu-kvm, you have to use the option -redir and redirect both ports 2049 and 111

---

