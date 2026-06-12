---
title: "After upgrading to 12.04.1, ssh has stricter key rules"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by grewil on 2012-11-19
Hi,

I have a group called remote, and a private ssh-key owned by root:remote, and readable to user (root) and group (remote). Users that are members of remote may use it to connect to another server. This way, I can change the key as frequently as I want without relying on the users following instructions or that they bother to change keys.

This setup has worked well for many years. Now, when I upgraded to Ubuntu 12.04.1, it stopped working, because ssh complains that permissions are too open (readable to group). The whole point of having groups is to be able to selectively share data like this. I can't seem to find an option for this.

Is there a way to configure ssh to work as it used to work before the upgrade?

---

### Post by hawkmage on 2012-11-19
That is odd here is an example from a test system running 12.04 where I changed the group on my ssh key files and granted the group read:
```
hawkmage@vb-ubuntu:~$ ls -l ~/.ssh/
total 12
-rw-r----- 1 root     tempuser  1675 Nov 19 19:17 id_rsa
-rw-r--r-- 1 root     tempuser   404 Nov 19 19:17 id_rsa.pub
-rw-r--r-- 1 hawkmage hawkmage 3536 Nov 19 19:16 known_hosts
hawkmage@vb-ubuntu:~$ ssh server
Last login: Mon Nov 19 19:20:17 2012 from vb-ubuntu
server:~ hawkmage$ 
```

What are the permissions on the key files?

If you want to old less secure functionality you cane add/change the StrictModes directive to the sshd_config file.

---

### Post by grewil on 2012-11-21
Thanks for testing and replying!

This is very strange. Today, the test I created to reproduce the problem succeeds. I've rebooted the machine, otherwise I cannot think of any other changes. Let's assume I made a mistake, until I can properly reproduce it again.

Thanks again for your time! /Greg

---

