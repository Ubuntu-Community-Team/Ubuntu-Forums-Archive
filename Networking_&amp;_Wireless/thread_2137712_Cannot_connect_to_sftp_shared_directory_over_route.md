---
title: "Cannot connect to sftp shared directory over router."
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by yoramdavid on 2013-04-21
Hi all,

I have a Ubuntu 12.04 machine and a LinuxMint 3.5 and used to share a folder from the LinuxMint machine through dolphin over a router.
I created a short-cut in Dolphin for ease of access.
The IP address is static in LinuxMint (192.168.10.2).

All of the sudden I cannot access that folder any more, I get the error (translated from Portuguese):
Connection to server. The key of the machin to the server 192.168.10.2 was altered.
This might signify that there is a conflict in course, or that the IP of the machine and its key was altered at the same time.
The digital impression of the key sent by the remote machine is:
 f8:88:27:fd:72:9c:e7:f1:c4:4a:42:cc:ef:36:90:b2
Contact your administrator
was broken.

I search for answers without luck, does any one can help me on this?

Thank you.

Yoram

---

### Post by steeldriver on 2013-04-21
That's normal if you have changed the server's interface, I think - it means your client machine has a 'stale' host key in your known_hosts file. You should be able to remove it with ssh-keygen on the client machine e.g.

```
ssh-keygen -R 192.168.10.2
```

If you have NOT changed the server interface then it would indicate that someone is trying to 'spoof' your server - see the link below for more info

[http://serverfault.com/questions/29262/how-to-manage-my-ssh-known-hosts-file](http://serverfault.com/questions/29262/how-to-manage-my-ssh-known-hosts-file)

---

### Post by yoramdavid on 2013-04-22
Hi steeldriver,

That I know I have not changed anything.
What is the server? The machine where I have a shared folder LinuxMint?

The code returned an error:
```
ssh-keygen -R 192.168.10.2
ssh-keygen: /home/user/.ssh/known_hosts: No such file or directory
```


Thank you.

---

