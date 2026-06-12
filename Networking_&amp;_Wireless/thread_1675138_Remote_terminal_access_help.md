---
title: "Remote terminal access help"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by Fracta on 2011-01-25
Can anyone point me to (a) tutorial/s that explains how to set up remote access to my pc via terminal?
I want to be able to go on to another linux pc and install ssh and whatever basic programs and connect to my pc and do things like ls, chmod, scp or any small file transfer alternative, but only using commands through the terminal. The internet here isn't very good, and I don't need to actually see the desktop to do what I want. Starting programs remotely on my pc would also be really good.
A basic tutorial would be best. I am quite new to networking, especially on linux.
At this point, I have a domain set up at dyndns.com and I'v also installed and mostly configured ddclient. I'm stuck at the point of actually starting ddclient as a daemon. It is set to true in /etc/default/ddclient but /etc/init.d/ddclient keeps saying its not. Yeah I am not too sure what I'm doing yet. 
Thanks

P.S. I would also like to use as few programs as I can. For simplicity, as well as ease of access when I go somewhere else. Please don't tell me about security because I do know and as soon as I have it working without security, I will add keys etc. 

Also, I have my computer and a laptop that are both connected wirelessly on the same local network, and this is the setup I am using for testing. 
I just tried ssh 127.0.0.1 on the laptop (which I haven't done anything to yet) and it can't even connect to the localhost. What basic setup procedures have I forgotten?

---

### Post by Smart Viking on 2011-01-25
```
sudo apt-get install openssh-server
```
^to install on the server side.
```
sudo /etc/init.d/ssh start
```
^To start the ssh server daemon manually on the server side
```
ssh <local-ip>
```
to connect form the client side.


Make sure the linux firewall isn't blocking incoming on port 22 on the server side.

---

### Post by Fracta on 2011-01-25
Thanks. That part is done. I can now connect two pcs and ssh between them on a local network. Helps to make sure that ssh is actually installed even if the command appears to run. 
However, I am still having trouble connecting to my pc through dyndns. Tell me if I have the syntax right, and if I am being stupid trying to connect to myself. This next part is all I need to get remote access working properly.

ssh -l *username* *pcname*@*dnsname*.dyndns.info

I am pretty sure I have the port forwarding set up correctly on my router and my hosts file looks correct.
I can ping *dnsname*.dyndns.info and get the ip for it and when I put that ip address in my browser it takes me to the router settings page just as if I had typed 192.168.1.1

---

### Post by Smart Viking on 2011-01-25
The syntax to connect is:

ssh username@computername

where the computer name can be an IP, or DNS. When you use a DNS it basically only takes the IP from the DNS and connect to the PORT that is, set(22 by default, -p to set another). so you would do this:

ssh *username*@*dnsname*.dyndns.info


The ssh manpage contains a lot of useful info.
good luck.

EDIT: Btw, you don't have to specify username, of you only connect with "ssh computername" it will use the username you are logged in as on the client side

---

### Post by Fracta on 2011-01-25
I'm still getting Connection Refused and it is using the default port 22. I checked on yougetsignal.com and the port is definitely open. I can ping every step but can't connect.
I'll have a read of the man page for ssh now. 
Also I take it (I know about the -p switch for ssh) that you can't specify a different port by adding it after the ip address with a colon? For example:
192.168.1.1:22

---

### Post by Fracta on 2011-01-26
Ok I asked someone else from outside the network to ping my router's wan ip and the request timed out so maybe I haven't got something set right? I'll leave the dns for now and concentrate on just connecting thru my wan ip which should then be forwarded thru the port to my pc. I am still getting connection refused tho.

---

