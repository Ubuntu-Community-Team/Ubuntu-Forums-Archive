---
title: "Network problem to get internet access"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by kmabuntu on 2012-01-01
Hi All 
I'm Glad to share in this forum for the first time 

I'm new in ubuntu 
i install an ubuntu server on my machine.
but i need to install the GUI ubuntu desktop 
but it need to connect my pc to internet 
i fix the network cable into my machine but i don't know how can i configure this machine to my network and accessing the internet 

any one help me plz ??

note i need the help depend on the comand line not in GUI plz 
thanks

---

### Post by anandu on 2012-01-01
whats the o/p of ifconfig command?

---

### Post by kmabuntu on 2012-01-01
> **anandu said:**
> whats the o/p of ifconfig command?sorry i'm new in ubuntu and plz answer me in details plz

---

### Post by praseodym on 2012-01-01
Hi,

for a server you dont need a GUI like "Ubuntu-desktop" if you dont want it. But:

Please show the terminal outputs of the commands:

```
lspci -nnk | grep Ethernet
lsmod
ifconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
```
How do you connect? Router/modem combination or a single modem?

---

### Post by gordintoronto on 2012-01-01
Ubuntu server is good for hosting high-volume web sites, but it's a lot easier to use Ubuntu Desktop, and install any server bits as needed.

---

