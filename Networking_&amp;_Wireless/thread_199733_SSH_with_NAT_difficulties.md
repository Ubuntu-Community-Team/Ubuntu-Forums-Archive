---
title: "SSH with NAT difficulties"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by Aramis on 2006-06-19
Hi y'all,

Here it is I run an isolated network, because my organisation has a public routable IP, for which I access the different hosts with SSH via a Win2k gateway enabled with Network Address Translation.

The setup on the gateway seems okay since I can establish the connection to most of my host.... Yes most but not all, and I don't understand why.

Here is a listing of my current setup:
- 1 FreeBSD host @ 192.168.0.3
- 1 Dapper Drake @ 192.168.0.4
- 1 Breezy Badger @ 192.168.0.5

This demonstration starts by deleting the file .ssh/know_hosts . The host I use to establish the connections is my laptop located on one of my organisation's subnets. This Laptop runs Breezy Badger 5.10, and the SSH version is as follows : OpenSSH_4.1p1 Debian-7ubuntu4.1, OpenSSL 0.9.7g 11 Apr 2005

First of all, I try to connect to the FreeBSD host (success)
```

ssh -p 2203 Gw_address

```
Same for the host running Dapper Drake (success)
```

ssh -p 2204 Gw_address

```
and finally for the host running Breezy (failure)
```

ssh -p 2205 Gw_address

```

Please rest assured that the port forward works because if I try to SSH into the Breezy host first, I fail to connect to the Dapper one afterwards. Strangely enough, in all test combination the SSH connection to the FreeBSD box ALWAYS works....

The error message I get is as follows :
```

 WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
[...]
RSA host key for **Gw_address** has changed and you have requested strict checking.

```

I simply don't understand, it would appear that SSH associated ALL connection to the IP of my gateway (Gw_address in this post) as opposed to the host(s) behind it! It is really annoying because with putTY everything works fine.

What am I doing wrong? Should I change something in the manner in which I establish the connections? Should I alter the configuration of the SSHD on the Dapper/Breezy host(s) ?

Any help trully appreciated.

Cheers!

Ar@mi$ researcher in disstress

---

### Post by Aramis on 2008-02-25
**UPDATE**,

I know this is late and apparently nobody cares :'(

Ok, the problem comes from the fact that all the hosts have the SSH key. Why is that? It simple! I prepared a **single** installation of Ubuntu. Once I had this one setup, I **DD** the configuration onto the other machines. Yes, the hostnames, and IP addresses were changed, this however does not mean that the SSH configuration/hash/keys and what not, change or are updated too.

Voila!

Ar@mi$

---

### Post by Mr. C. on 2008-02-25
See the StrictHostKeyChecking and VerifyHostKeyDNS settings in ssh_config, and the -o option command line options to ssh.

MrC

---

