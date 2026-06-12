---
title: "Network Mapping"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by bugfinder on 2010-08-15
Hi Everybody,

                  I have just setup a system with Ubuntu 10.04 and it was great using it and knowing new things. I was trying to set up a Network Mapping on my Ubuntu 10.04 Machine, i have gone through so many forum but it didn't help me. I have tried all the Steps that are mentioned on this link :- [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

But still i'm not able to map a network driver.

My machine :- Ubuntu 10.04(desktop version); IP :- 10.11.1.56
File server is on Ebox; IP :- 10.11.1.200

I have edited the the fstab file with appropriate Info .. but still not working. can anyone help me on this.

---

### Post by Morbius1 on 2010-08-15
Post the line in fstab you're using to mount the share - the more people that see it the better your chances are that someone could spot the problem.

You might want to try this as well. With the system booted run the following command and post any errors it might give:
```
sudo mount -a
```Actually, after you do that see if you can now access the share. There is a known bug in 10.04 where fstab is executed before the network is up so it tries to mount a remote share that isn't available yet.

---

