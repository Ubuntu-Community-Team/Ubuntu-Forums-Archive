---
title: "Trouble with iptables...please help"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by 2quick on 2009-08-13
Hello! I am using Ubuntu 9.04 and working on installing squid for a web cache. At the end I am needing to modify iptables. So when I finished up and typed the save command I got:

```

$ sudo service iptables save
$iptables: unrecognized service
```

so I tried to see if it was installed:

```
$ dpkg --list iptables
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ri  iptables       1.4.1.1-4ubunt administration tools for packet filtering an
```
So is there a way to get the "r" to go back to installed? I tried running upgrade, install, and update but it is still there.

Another bit of information for the status:

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
Also it will not start:

```
$ sudo service iptable start
$iptable: unrecognized service
```

Thanks for any available input!

---

