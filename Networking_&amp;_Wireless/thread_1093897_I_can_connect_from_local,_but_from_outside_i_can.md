---
title: "I can connect from local, but from outside i can"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by tondop on 2009-03-12
I have a problem. I can connect to remote computer with external IP from the outside but not from LAN. I can ping this external IP from all computers that are not from LAN. 	
Can you advise what to do with it? Thanks in advance for advice?

---

### Post by blackened on 2009-03-12
All the terminology is great, but unless you use it properly and in a very specific and detailed way, then it's just downright confusing.

What exactly are you trying to do? What exactly is your network setup? In what situations (if any) do you have the connectivity you want? Do you have all appropriate ports forwarded on your router (if applicable)?

---

### Post by tondop on 2009-03-12
This will help to clarify?

computer#A
external IP: 195.168.63.162
mask: 255.255.255.248
default gw: 195.168.63.161
DNS: 195.168.1.2 and 195.168.1.4


computer#B
IP: 192.168.252.57
mask: 255.255.255.0
default gw: 192.168.252.1
DNS: 195.168.1.2 and 195.168.1.2

My problem is, that I cant connet/ping computer#B from computer#A

---

### Post by dmizer on 2009-03-12
Does computer A have a direct connection to the internet, or is there a router between computer A and the internet?

---

### Post by tondop on 2009-03-12
> **dmizer said:**
> Does computer A have a direct connection to the internet, or is there a router between computer A and the internet?

The sequence from computerA is as follows:
computerA -> router -> Internet


The sequence from computerB is as follows:
computerB -> switch -> router -> Internet


To help it?

---

### Post by MaxIBoy on 2009-03-12
Do you have any ports open?

(I can't ping you either. Sorry, but I couldn't resist.)

---

### Post by sahabcse on 2009-03-12
Hi

Check the following

nmap 195.168.63.162
nmap 192.168.252.57

---

### Post by tondop on 2009-03-12
> **MaxIBoy said:**
> Do you have any ports open?

(I can't ping you either. Sorry, but I couldn't resist.)
	
sorry but I do not know this. How to find? The problem is that my router managed provider.

---

### Post by sahabcse on 2009-03-12
Hi

Install the nmap tool and check whether any ports are in closed state..........

Installing nmap 

#apt-get install namp

---

### Post by tondop on 2009-03-12
#nmap 192.168.252.57 -PN

Not shown: 1711 filtered ports
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3389/tcp open  ms-term-serv


and

#nmap 195.168.63.162
Not shown: 1714 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

So what now??

---

### Post by sahabcse on 2009-03-12
Hi

Install openssh client and server. 

sudo apt-get install openssh-client openssh-server. Then try to connect lan machine using ssh,

#ssh username@ip-address

---

### Post by nelskurian on 2009-03-12
Is their any firewall rules that restrict you from pinging the another.
Check the below in both machines.
# iptables -L
Check whether the 'openssh' port open in remote external host.In most cases the 'ssh' port closed in public servers for security reasons

---

### Post by dmizer on 2009-03-12
Is the router connected to machine A the same as the router connected to machine B?

No ping is no problem. The router for machine A probably just has [ICMP]("http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol") disabled.

---

