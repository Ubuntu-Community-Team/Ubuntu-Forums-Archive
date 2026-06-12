---
title: "Network printing using global  ip"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by Slavians on 2011-07-22
Have smb such experience?
How to make   network printer  hp 2035n accessible  by Internet.

I have such scheme.

hp2035n printer (192.168.5.31) <== ubuntu_serv_11_04  (eth0=192.168.5.1 eth1=92.18.11.11)

such ports  on the hp 2035n
```

[Nmap]("http://en.wikipedia.org/wiki/National_Maternity_Action_Plan") scan report for 192.168.5.31
Host is up (0.0021s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
7/tcp    open  echo
80/tcp   open  http
515/tcp  open  printer
8290/tcp open  unknown
9100/tcp open  [jetdirect]("http://en.wikipedia.org/wiki/JetDirect")

```
I want to print worldwide using  address  92.18.11.11
(may be help  1  line in iptables for some port forwarding?)

Thanks.

---

