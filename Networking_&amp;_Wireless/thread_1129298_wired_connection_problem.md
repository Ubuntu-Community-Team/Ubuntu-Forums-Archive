---
title: "wired connection problem"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by tony67 on 2009-04-18
i have just installed ubuntu 8.10 in my pc and I can't connect to the router,wired so I can access to the internet.I am using a realtek RTL 8111C chip. please help!!!!!

---

### Post by puppywhacker on 2009-04-18
could you post some more information, for instance some printouts? problems can be on any part of the system, so any specific feedback helps

lsmod | grep r8
sudo mii-tool
ifconfig
lspci
dmesg

---

