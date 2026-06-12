---
title: "ssh issue while setting up NFS[/"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by jimbren on 2008-12-14
So, I have a fresh installation of 8.10 on my laptop and I was in the process of setting up NFS between my server and the laptop.  I'd had this set up a while back without any issue, but did a reinstall on my server sometime last year and never set up NFS again.  The server is running 6.04 server and the laptop is 8.10.

ssh worked between the two without any issue.  While setting up NFS on the server, I had done the following:
1) installed NFS with:
```
sudo apt-get install nfs-kernel-server
```
this worked.
2) edited /etc/exports with the following entries:
```
/mp3 192.168.1.21(rw)
```
3) edited /etc/hosts.deny with the following code:
```
ALL:ALL
```
4) edited /etc/hosts.allow with the following code:
```
portmap: 192.168.1.21
```
5) then I verified that it was working with the following:
```
rpcinfo -p
```

Then I disconnected from the server, created the mount point on my laptop, and tried to mount the folder.  The answer I got back was:
```
mount: wrong fs type, bad option, bad superblock on zion:/mp3,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

So here's the part that's really awesome and makes me incredibly happy.  I tried to ssh into my server to double check my entries, and I got back:
```
ssh_exchange_identification: Connection closed by remote host
```

My fear is that I screwed up /etc/hosts.allow and put in an incorrect IP address.  Gaining direct keyboard access to the server is a royal pain in the *** that I would love to avoid having to do.

Short of monkeying around with my laptop long enough to figure out what possible typo I could have put in /etc/hosts.allow, can I fix this remotely?

Or am I barking up the wrong tree entirely?

Thanks,

jimbo

---

### Post by HermanAB on 2008-12-14
First try to see what is bugging SSH:
ssh -vvv user@serveripaddress

or:
telnet serveripaddress 22

That should give you some idea of what is wrong.

Cheers,

Herman

---

### Post by cariboo on 2008-12-14
It looks like your problem is with this:

> portmap: 192.168.1.21

If you can somehow reconnect remove that line form /etc/hosts, you should be ok.

Jim

---

### Post by jimbren on 2008-12-14
Herman--
Here's what I got:
```
jim@ingsoc:~$ ssh -vvv jim@zion
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to zion [192.168.1.20] port 22.
debug1: Connection established.
debug1: identity file /home/jim/.ssh/identity type -1
debug1: identity file /home/jim/.ssh/id_rsa type -1
debug1: identity file /home/jim/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

```

---

