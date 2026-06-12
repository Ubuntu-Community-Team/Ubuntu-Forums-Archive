---
title: "Port 22: opened and then closed again"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by LordZaamus on 2010-06-01
Hi all

Now I'm still not expert with ubuntu and have a problem with ssh on my Ubuntu 8.04 on a 64 bit machine: I try to connect to other machines (a computer of the university) from my laptop and, after some minutes, the connection times out.

[PHP]ssh: connect to host computername.ifca.unican.es port 22: Connection timed out[/PHP]

Also, if I do something like

[PHP]ping www.google.com[/PHP]I get

[PHP]PING www.l.google.com (209.85.227.103) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6009ms
[/PHP]Instead of a continuous list of ping every second

Following some forums (and also this one) I fixed the problem (trying many commands, like adding permissions to the iptables and other but I really don't remember how I fixed it) and I have been able to connect with

[PHP]ssh -X user@computername.ifca.unican.es[/PHP]from my home wireless connection. Now I'm at the university, with the university wifi connection and ssh doesn't work. Do I have to make configurations for every connection I use? One last thing: now I can't verify if, with my home connection, ssh still works because the service is temporarily down.

Thanks all

---

### Post by LordZaamus on 2010-06-02
P.S. Now I have verified and ssh does work from my home. So the problem is halved but I'd like to have the ssh command work from any connection I use. Do I simply have to make all the fixes whenever I use a new connection or is there an universal solution? 

Thanks again

---

### Post by tad1073 on 2010-06-02
do you have rights to access the schools network over ssh?

---

### Post by xifer on 2010-06-02
do you need X11 forwarding when connected by the wifi? Some edu places are worried about hackers for some reason.

---

### Post by LordZaamus on 2010-06-05
> **tad1073 said:**
> do you have rights to access the schools network over ssh?
 
 
I should have it, since I first tried to solve this with a professor...
 
>  
do you need X11 forwarding when connected by the wifi? Some edu places are worried about hackers for some reason. 

 
Really don't know, I'll try to ask or verify it when I'll connect next time to the wifi (by the way how can I verify this? Do I have to ask or do I have to look in
 
/etc/ssh/ssh_config
 
?
 
Thanks again, sorry, I can't be very fast in my aswers.

---

### Post by xifer on 2010-06-05
> **LordZaamus said:**
> I should have it, since I first tried to solve this with a professor...
 

 
Really don't know, I'll try to ask or verify it when I'll connect next time to the wifi (by the way how can I verify this? Do I have to ask or do I have to look in
 
/etc/ssh/ssh_config
 
?
 
Thanks again, sorry, I can't be very fast in my aswers.

You're using the command: ssh -X 

which will forward graphical output over ssh to run things like kde or gnome-desktop or even xterm.


The server may not permit this.  But you can easily check by trying a simple ssh without the -X instead and if that's ok then it's a security issue with X11.  When you're using this wifi there must be different network route to that when you're at home and if that's ok with X11 perhaps the other wifi network is using a firewall that blocks the ssh port.  Are there any other services on the server your trying to connect to that you can see? can you get to 

[http://your_host_ip_address:80](http://your_host_ip_address:80) 



for example?

---

