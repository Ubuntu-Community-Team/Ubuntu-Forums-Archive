---
title: "sshd resetting connections"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Khol on 2009-11-03
EDIT: Having power cycled, this now seems to be working, though I can't figure out why, since stopping sshd, reloading config, forcing reload of onfig just for the sake of it, an starting it had no effect previously.



I'm trying to set up sshd in order to be able to access my computer remotely. However, whenever I try and login, the connection is just dropped.

H=I've looked online and found a number of similar issues, and have carried out a number of suggested fixes, however none have worked.

There are a couple of  differences between a lot of the problems (for example [here]("http://ubuntuforums.org/showthread.php?t=838873") and [here]("http://www.networksecurityarchive.org/html/Secure-Shell/2007-02/msg00005.html")) in that firstly, I never even get the chance to put in a password it just dies, and secondly, it happens even when I'm connecting to localhost, with no connection whatsoever to any form of network.

I've just reinstalled to 9.10 x64 yesterday, so pretty much a clean install apart from a couple of things which shouldn't touch ssh in any way.

Running 'ssh -vvv localhost -p 2904' gives:

```
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.246 [192.168.1.246] port 2904.
debug1: Connection established.
debug1: identity file /home/tom/.ssh/identity type -1
debug1: identity file /home/tom/.ssh/id_rsa type -1
debug1: identity file /home/tom/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
```Read from socket failed: Connection reset by peer[/code]This happens both using ssh from the command line, and also when connecting from putty on a machine running Win7.

---

