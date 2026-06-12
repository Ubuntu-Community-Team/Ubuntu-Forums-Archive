---
title: "flush iptables"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by gontofe on 2009-09-06
Hello all,

Just a quick question regarding cups + networking.

I am currently using Jaunty Jackalope, and have been trying to get my networking sorted.

The only way to get my computer to connect to the windows workgroup and allow remote printers to access my printer via cups is to flush the IP tables with

```
sudo iptables -F
```

then

```
sudo iptables -P INPUT ACCEPT
```
```
sudo iptables -P OUTPUT ACCEPT
```
```
sudo iptables -P FORWARD ACCEPT
```

Why is this? What is causing the iptables to contain old/incorrect info? What are the iptables?:P

---

