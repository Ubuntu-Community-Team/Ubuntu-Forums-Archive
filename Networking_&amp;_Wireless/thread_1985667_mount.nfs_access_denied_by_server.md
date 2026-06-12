---
title: "mount.nfs: access denied by server"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by MG&amp;TL on 2012-05-23
Hello forumgoers. ):P

I have a slight problem setting up NFS on my local network (behind a router/wireless combo, I believe it's DHCP).

So, here's what I've done so far:


On server:
```
sudo apt-get install nfs-kernel-server nfs-common

```

/etc/exports:

```

[...]
#
/home/share 192.168.1.0/0(rw,nohide,insecure,no_subtree_check,async)

```

On client:

```
sudo apt-get install nfs-common
```

Here's the problem:

```
michael@laptop:~$ sudo mount -v 192.168.1.65:/home/share /media/share
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Wed May 23 19:05:02 2012
mount.nfs: trying text-based options 'vers=4,addr=192.168.1.65,clientaddr=192.168.1.67'
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.1.65:/home/share
michael@laptop:~$
```

Although:

```
michael@laptop:~$ showmount -e 192.168.1.65
Export list for 192.168.1.65:
/home/share 192.168.1.0/0
michael@laptop:~$ 

```

What have I done wrong?

---

### Post by roelforg on 2012-05-23
> **MG&TL said:**
> Hello forumgoers. ):P

I have a slight problem setting up NFS on my local network (behind a router/wireless combo, I believe it's DHCP).

So, here's what I've done so far:


On server:
```
sudo apt-get install nfs-kernel-server nfs-common

```/etc/exports:

```

[...]
#
/home/share 192.168.1.0/0(rw,nohide,insecure,no_subtree_check,async)

```On client:

```
sudo apt-get install nfs-common
```Here's the problem:

```
michael@laptop:~$ sudo mount -v 192.168.1.65:/home/share /media/share
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Wed May 23 19:05:02 2012
mount.nfs: trying text-based options 'vers=4,addr=192.168.1.65,clientaddr=192.168.1.67'
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.1.65:/home/share
michael@laptop:~$
```Although:

```
michael@laptop:~$ showmount -e 192.168.1.65
Export list for 192.168.1.65:
/home/share 192.168.1.0/0
michael@laptop:~$ 

```What have I done wrong?

Okay, replace 192.168.1.0/0 with 192.168.1.0/24 (or /16 if that doesn't work) in your /etc/exports and add
```

-t nfs

```
to your mount command.

---

### Post by MG&amp;TL on 2012-05-23
Thanks, roelforg. That mounted it, but nautilus freezes if I go to that location, and 'ls' just doesn't respond.

Any suggestions, or just the lack of speed from my network? (and therefore needing a different solution for my filesharing).

EDIT: just teething problems. Seems to work fine now. :) Thank you!

---

### Post by roelforg on 2012-05-23
> **MG&TL said:**
> Thanks, roelforg. That mounted it, but nautilus freezes if I go to that location, and 'ls' just doesn't respond.

Any suggestions, or just the lack of speed from my network? (and therefore needing a different solution for my filesharing).

Well, a freeze is something...
Does the hd-led on your server turn on and do the network leds on either system blink while it freezes?
It could be network, but then you'll only see the network leds blink and not the hd-led (as the hd alreade finished and the sys is waiting on the network).
Or a slow hd in the server.

---

