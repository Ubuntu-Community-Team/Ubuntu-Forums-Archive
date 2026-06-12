---
title: "Ubuntu 11.10 +NFS problem"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by nyamaa on 2012-04-20
Hi
I am just trying to make NFS file sharing.I installed Ubuntu 11.10 on two Windows computers using wubi. Then I mounted one to other. Mount is no problem. But I can not view the second computer's files in the first computer and vice versa. Before I did the file sharing multiple times without any troubles on Ubuntu 11.10, 11.4, 10.10, 8.10. 
Is there any specific procedure I should follow in this case?

---

### Post by Jose Catre-Vandis on 2012-04-20
You say you have had success before (using wubi on both machines?) have a good read through here:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Can you also provide more details of your settings/setup?

---

### Post by nyamaa on 2012-04-20
Thank you sir.
I just followed my usual procedure to create NFS sharing on Ubuntu computers.
I usually do this when I create Beowulf clusters on Ubuntu only computers. But this time I need to build the cluster on university computer lab which shared my multiple lecturers most of whom want to stick with Windows.
Ok, at first I created an user on every computers. The users' names are mpiuser, same.They have administrator right. Then I installed nfs-kernel-server on the first computer. Then I added that line /home/mpiuser   2-nd pc's hostname(rw,sync) to exports. I usually reboot after this step to restart nfs-kernel-server.I am pretty sure nfs-kernel-server is starting, because when I try to start manually by service nfs-kernel-server start, I got two OKs. Then I mount from my second computer by sudo mount 1-st pc hostname:/home/mpiuser /home/mpiuser. It is ok, no error. By df , i can see the directory is mounted. But when I create files on my second computer, I can not see them from my 1-st computer and vice versa.It is Ubuntu 11.10 and installed by wubi on Windows computers.

---

### Post by nyamaa on 2012-04-21
What is portmap? Is there any bug in Ubuntu 11.10 that sometimes portmap would not start after boot? If protmap wo'nt start, is it possible to happen above-mentioned situation? I

---

### Post by drdos2006 on 2012-04-21
You may need nfs-common on each machine as well with :

sudo apt-get nfs-common

regards

---

### Post by Jose Catre-Vandis on 2012-04-21
Yes I always install portmap and nfs-common on my nfs clients.

---

### Post by nyamaa on 2012-04-22
nfs-common, portmap are automatically installed with Ubuntu 11.10. In my other cluster, I uprgaded by do-release upgrade from 10.10 to 11.10 for all PCs. NFS has no problem. Actually there was one problem, when I use NFS4, slave computer's shared directory appeared as it is owned by nobody. So I used nfs3 in that cluster.

---

### Post by SeijiSensei on 2012-04-22
> **nyamaa said:**
> nfs-common, portmap are automatically installed with Ubuntu 11.10.

That's news to me.  I always have to install nfs-common on a new installation to enable the machine to be an NFS client.  I just did so with a 12.04b2 installation the other day.  Maybe it's included with Ubuntu but not with Kubuntu, which is what I use?

---

### Post by nyamaa on 2012-04-27
I solved the problem. I restarted portmap after my mount on the NFS client. I think wubi installed Ubuntu 11.10 have a bug in this situation. But I stiil have problem for NFS4 where clients shared files owned by nobody. Currently I workaround by NFS3.

---

