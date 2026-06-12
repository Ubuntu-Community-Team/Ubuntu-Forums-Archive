---
title: "Network port"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by any.linux12 on 2008-12-18
I want to open a port in a server but I can't do it with the iptables bla bla bla command

is there any chance to open by a conf file




PLEASE HELP

---

### Post by iponeverything on 2008-12-18
> **any.linux12 said:**
> I want to open a port in a server but I can't do it with the iptables bla bla bla command

is there any chance to open by a conf file




PLEASE HELP


```
iptable -L -n 
```will tell you if you are blocking any ports. If your not blocking them, they are open. You do need something listening on the port though..

---

### Post by any.linux12 on 2008-12-18
Ok. So i need to put the server listening to the 40000 port

Help please

---

### Post by The Cog on 2008-12-18
Then just configure your server program to listen on port 40000. If you don't know how to configure the server software to listen on port 40000, perhaps if you say what server software it is, someone here will know how to configure it.

---

### Post by any.linux12 on 2008-12-19
I don't think that someone knows this service. It's from a swiss company and it is a business software. ABACUS

The service it's AbaSioux

---

### Post by The Cog on 2008-12-19
I've never heard of it. Not that this matters too much. A few questions though:

Why specifically port 40000 - is this the port the server normally listens on?

Is your server actually listening on that port? Use this command:
```
netstat -lnt
```
on the PC running the server software to see if that port is listening.

Use this command:
```
sudo iptables -nvL
```
to see the firewall rules that are active. You may have difficulty following them, so post the output here and we can have a look.

What is the actual problem you are having? Is it difficulty in connecting to the server from clients? If so, are they in the same building or are you trying to go over the internet?

---

### Post by any.linux12 on 2008-12-19
hi!

The port 40000 is the port to connection from the client to the server. And at the moment the server is not listening to the port because (I think) I can't put the service running, and I have no idea howto put that s**t running.

---

