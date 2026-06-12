---
title: "sshd segfault"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by weliwarmer on 2010-01-06
Hi All,

I've started to get segfaults in sshd when trying to connect.  There has been no reboot and (until I restarted the sshd to try to fix the problem) there was still another ssh session connected.

The log messages:
```
==> kern.log <==
Jan  6 21:33:38 shuttle kernel: [ 1928.611128] sshd[9548]: segfault at bf30e534 eip b7f51b4c esp bf30e510 error 6

==> auth.log <==
Jan  6 21:33:38 shuttle sshd[9427]: debug3: fd 4 is not O_NONBLOCK
Jan  6 21:33:38 shuttle sshd[9548]: debug1: rexec start in 4 out 4 newsock 4 pipe 6 sock 7
Jan  6 21:33:38 shuttle sshd[9427]: debug1: Forked child 9548.
Jan  6 21:33:38 shuttle sshd[9427]: debug3: send_rexec_state: entering fd = 7 config len 731
Jan  6 21:33:38 shuttle sshd[9427]: debug3: ssh_msg_send: type 0
Jan  6 21:33:38 shuttle sshd[9427]: debug3: send_rexec_state: done
Jan  6 21:33:38 shuttle sshd[9548]: debug1: inetd sockets after dupping: 3, 3
Jan  6 21:33:38 shuttle sshd[9548]: debug3: Normalising mapped IPv4 in IPv6 address
```


The ssh session from client:
```
$ ssh 192.168.1.8 -v -v -v
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.8 [192.168.1.8] port 22.
debug1: Connection established.
debug1: identity file /home/tim/.ssh/identity type -1
debug3: Not a RSA1 key file /home/tim/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
...repeated lots....
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/tim/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/tim/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
```

If anyone has any ideas, I'd be most grateful.  It's going to be a real pain if I cannot get a remote connection to the server for a while.

Thanks,
Tim

SSHD version  1:4.7p1-8ubuntu1.2
sshguard installed
denyhosts version 2.6-2.1

---

### Post by weliwarmer on 2010-01-06
Further information:

If I comment out the first line of hosts.deny it works again:

```
sshd: /etc/denyhosts/ignored : allow
sshd: ALL EXCEPT /etc/denyhosts/blocked
```

Nothing has changed in /etc/denyhosts/ignored - it's strange that it causes a segfault, even if the file is empty.

Thanks again,
Tim

---

