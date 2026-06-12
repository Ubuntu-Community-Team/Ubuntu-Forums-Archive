---
title: "Mount to NFS server failed (8.10 -&gt; 8.04)"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Cordate on 2009-05-06
Hello Ubuntu folks. I am getting a curiously undescriptive failure message on an NFS share mount and hope someone here might be able to shed some light on things. I've shared folders via NFS before but this time I seem to be stumped on what might be going on.

The setup is as follows:

I am attempting to share my /home/username folder (and its subdirectories) on a 8.10 machine with one on the same network running 8.04. Both are configured to have static IPs and both can see each other via tracepath, though the 8.10 oddly shows the 8.04 machine twice when I do this:

```
1:  Leandra (192.168.0.22)                                 0.609ms reached
 1:  Leandra (192.168.0.22)                                 0.546ms reached

```

Here is the relevant line from the 8.10 machine's /etc/exports file:

```

/home/stacy 192.168.0.22(ro,sync,no_subtree_check)

```

And I am attempting to mount it on the other machine using 

```
sudo mount carrot:/home/stacy /media/carrots
```

Carrot being the hostname of the 8.10 machine. I have tried swapping that for the LAN ip address of the machine as well with no change in behavior, the consistent (and unhelpful) error message that returns from the mount command is:

```
mount to NFS server 'carrot' failed.
```

And that is all :( I have looked in /var/log/messages on both machines but I see no feedback about the mount attempt in either file.

The odd thing here is that when I first set this NFS share up, it -worked-. Now, after reboots on both machines it no longer works.

Edit- I am able to go in the other direction and mount folders from the 8.04 machine on the 8.10 one. Rather curious.

---

