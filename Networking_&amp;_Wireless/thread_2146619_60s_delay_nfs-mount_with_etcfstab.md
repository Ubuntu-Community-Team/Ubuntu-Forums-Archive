---
title: "60s delay nfs-mount with /etc/fstab"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by Mirko76 on 2013-05-19
Hi,

i try to mount a nfs share from my server. The server ist 12.04 and the client also.

My /etc/fstab:

192.168.1.12:/home /home/xxx/test nfs _netdev,defaults 0 0

After exactly 60s the mount visible.

Why does it take 60s to mount the share? The network is available immidiatly after the boot.

Thx
Mirko76

---

### Post by futo on 2013-05-19
Please explain what exactly you mean by "The network is available immidiatly after the boot" ...

There should normally only be a deleay for the disks to start up. I assume your network drive is running all the time.

---

### Post by Mirko76 on 2013-05-19
I can log in per ssh after 5s, ping is also successful, so i think, the network is started.

I solved the problem with adding nfsvers=3 to my fstab.

---

### Post by futo on 2013-05-19
Congratulations :D ... please mark the thread as solved; [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

