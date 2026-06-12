---
title: "SSH, Belkin,chaos"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by confick3r on 2009-07-17
Dear Friends,  

 hello to everyone  .. New member to the forum so far.. I use ubuntu for several years, along with Window$ (unfortunately..). I have managed to set up an OpenSSH Server 2-3 times, and whenever problems arise, always it's function would be "out of the box". The other day I tried again to install a pc with ubuntu 9.04 and I faced a problem. Please note here that: 
 -I upgraded to a new router Belkin F5D7633, with enabled firewall, DHCP Server with static ip to the pc-ssh-server and virtual server / port forwarding from external port 22 to internal ip on port 22 at the server. 
 -I normally install sudo apt-get install openssh-server openssh-client and restart the ssh several times, but don't change any configuration files, and each time everything is working "out of the box". 
 -can connect with ssh myusername@192.168.1.4 where 192.168.1.4  the address of  server.  
 -I have set up a dyndns.org address  

 The problem is that I cannot "see" the server from WAN, whenever  this is my IP address directly or  my dyndns address. I tried tweaking, and only I did manage to connect to the router's ssh service (!) while I am forwarding the  port 22 elsewhere. 

 Whatever your idea is, it is  accepted ..  

 Thanks,
confick3r

---

### Post by martinbaselier on 2009-07-17
It seems the router uses port 22 for it's own remote login. Why don't you try to set up a new port for ssh on the remote machine? 

Just add Port PORTNUMBER to
/etc/ssh/sshd_config

and change the setting in the router accordingly.

see **man sshd_config** and **man sshd** for more info.

---

### Post by prshah on 2009-07-17
> **confick3r said:**
> 
 The problem is that I cannot "see" the server from WAN, 

To check if you ssh server is accessible from the WAN, you need to connect to another network, ie, dialup or a neighbor's house, or so. 

In other words, to check WAN access to your SSH server, your client cannot use the same connection as your server.

Aside from that, if, when accessing through WAN, you connect to your router, rather than your machine, then you need to :

EITHER: Change your ssh port number as outlined earlier (this is a good thing to do) ** recommended, and set up port forwarding to allow access to your ssh server from the WAN.

OR: Disable ssh access on your router, and set up port forwarding to allow access to your ssh server from the WAN.

Note that in either case you need to setup port forwarding. To know the exact steps, visit [www.portforward.com](www.portforward.com) and select the model of your Belkin router for exact steps.

---

### Post by confick3r on 2009-07-17
[[IMG]http://img17.imageshack.us/img17/5907/98062984.th.jpg[/IMG]](http://img17.imageshack.us/i/98062984.jpg/)

I've already done these steps.. I tried with port 4445.
I cannot understand what to put on inbound and private ports.
I tried putting 4445 to inbound,private and sshd_config file.
No connection.

portforward.com simply describes how to put port 22 for port forward in my router. Nothing more.

---

### Post by prshah on 2009-07-17
> **confick3r said:**
> 
I've already done these steps.. I tried with port 4445.
I cannot understand what to put on inbound and private ports.
I tried putting 4445 to inbound,private and sshd_config file.

You're so close.

Here it is, step by step;

[indent]
a. Set your port to 4445 by adding/editing the following line in /etc/ssh/sshd_config```
Port 4445
```
b. Restart your server for the new port to take effect```
sudo /etc/init.d/ssh restart
``` Note that in this case, the ssh server is ssh, not sshd.
c. In the router config page (as posted above) put in the following settings:[indent]Enable: checked (ticked)
Description: SSH (or whatever you like)
Inbound port (1st box): 4445
Inbound port (2nd box): 4445
Type: Both
Private IP address: The LAN address of your computer; check it with ifconfig on the computer that is running ssh server
Private port (1st box): 4445
Private port (2nd box): 4445[/indent]
Save the settings ( You _may_ need to reboot your router)
d. Enable port 4445 in your firewall (assuming ufw)
```
sudo ufw allow 4445
```
e. From the same machine on which your server is running, check if you can access the server with ```
ssh -p 4445 127.0.0.1
``` 
f. Get your WAN IP by visiting a website such as [www.whatismyip.com](www.whatismyip.com).
g. Now, using another machine, connected to the Internet in a separate way (Not through the same router), try to connect to your WAN IP's ssh server```
ssh -p 4445 yourusername@yourserverip
```
[/indent]

That's it, with that everything should be working. In case of any doubts, post back with the point at which you are stuck.

---

### Post by confick3r on 2009-07-17
> **prshah said:**
> You're so close.

Here it is, step by step;

[indent]
a. Set your port to 4445 by adding/editing the following line in /etc/ssh/sshd_config```
Port 4445
```
b. Restart your server for the new port to take effect```
sudo /etc/init.d/ssh restart
``` Note that in this case, the ssh server is ssh, not sshd.
c. In the router config page (as posted above) put in the following settings:[indent]Enable: checked (ticked)
Description: SSH (or whatever you like)
Inbound port (1st box): 4445
Inbound port (2nd box): 4445
Type: Both
Private IP address: The LAN address of your computer; check it with ifconfig on the computer that is running ssh server
Private port (1st box): 4445
Private port (2nd box): 4445[/indent]
Save the settings ( You _may_ need to reboot your router)
d. Enable port 4445 in your firewall (assuming ufw)
```
sudo ufw allow 4445
```
e. From the same machine on which your server is running, check if you can access the server with ```
ssh -p 4445 127.0.0.1
``` 
f. Get your WAN IP by visiting a website such as [www.whatismyip.com](www.whatismyip.com).
g. Now, using another machine, connected to the Internet in a separate way (Not through the same router), try to connect to your WAN IP's ssh server```
ssh -p 4445 yourusername@yourserverip
```
[/indent]

That's it, with that everything should be working. In case of any doubts, post back with the point at which you are stuck.

ssh -p 4445 127.0.0.1 
Password denied please try again.. 


how can it be ? I know my password very well :P

---

### Post by confick3r on 2009-07-17
I connected with my username 
ssh -p 22 username@127.0.0.1
but I cannot with root's.. maybe it is disabled

Also I can connect with other computers within my home network as with 192.168.1.xxx

But when I am trying with my IP or dyndns...
Connection refused

Router firewall shut off.. Demilitarized zone to the server's address
Ubuntu has no firewall, I uninstalled firestarter and iptables

I set up a new port... 1234 both in sshd_config, and router
I used [https://www.grc.com/x/portprobe=1234](https://www.grc.com/x/portprobe=1234)
and the port appears to be open... it seems something in ubuntu is blocking WAN addresses..

---

### Post by martinbaselier on 2009-07-17
It's most probably your router doing that. The router should transfers the external request to the internal network. For ubuntu it makes no difference if the signal comes from the router (and the outside world) or from another computer within the local network.

---

### Post by confick3r on 2009-07-18
well.. I am going to send back the router for warranty replacement..
I read somewhere the new firmware is defective..
Belkin's international support is great..

---

