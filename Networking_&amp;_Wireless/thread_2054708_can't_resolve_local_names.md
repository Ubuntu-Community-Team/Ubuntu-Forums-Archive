---
title: "can't resolve local names"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by petermg on 2012-09-07
ok so I'm on my laptop, running 12.04 trying to connect to a network share on another 12.04 PC, it's a desktop.  They are both connected wirelessly.  The name of the PC I'm trying to connect to is "kids-ubuntu", but when I ping it I get this:

```
$ ping kids-ubuntu
PING kids-ubuntu (69.16.143.25) 56(84) bytes of data.
```

Now that IP address is NOT a local one.  What's up?  I checked my host file but it looks fine:


```
$ cat hosts
127.0.0.1	localhost
127.0.1.1	SilverStream-Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Where is that IP coming from?  If I ssh into the local IP address
of the machine I can reach it but when I want to access a network share on it via Nautilus, it gives me an error.  It's like a paragraph long.
[IMG]http://img580.imageshack.us/img580/4394/networkerror.jpg[/IMG]

---

### Post by iponeverything on 2012-09-07
have the hosts files on every machine contain host entries for every other machine they need to reach on the network and you'll be fine.

as for remote file system access install sshfs and openssh-server on the boxes, and when you use the "connect to server" choose "ssh" from the dropdown.

---

### Post by petermg on 2012-09-07
> **iponeverything said:**
> have the hosts files on every machine contain host entries for every other machine they need to reach on the network and you'll be fine.

as for remote file system access install sshfs and openssh-server on the boxes, and when you use the "connect to server" choose "ssh" from the dropdown.

The only problem with me editing the hosts file is that the machines are DHCP so their IP addresses will change periodically.

---

### Post by iponeverything on 2012-09-08
add dhcp reservations on the wireless router for the hosts..

---

### Post by Morbius1 on 2012-09-08
** There's something very odd if you are leaving the lan to resolve a hostname. Since both machines are Ubuntu instead of this:
> ping kids-ubuntuTry this:
```
ping kids-ubuntu.local
```** The "could not display 'network://'" error is reminiscent of a very old bug. Does the remote share require authentication and did you connect to it once and have it remember the password forever?

[COLOR=Blue]*Side Note: If your host name on this box really is "SilverStream-Ubuntu", kids-ubuntu will never see it because it's 4 characters too long. You can fix that for samba purposes ( and I'm assuming you're using samba ) in smb.conf itself if you are interested.*[/COLOR]

---

