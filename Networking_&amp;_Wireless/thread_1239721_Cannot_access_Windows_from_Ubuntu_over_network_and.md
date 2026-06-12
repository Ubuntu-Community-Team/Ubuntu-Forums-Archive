---
title: "Cannot access Windows from Ubuntu over network and vice-versa"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by IAmNotAUser on 2009-08-13
I have a fairly typical home network setup, a Windows Vista PC and a Linux box acting as a media store, both wired to a router, and a laptop (dual-booting Windows and Ubuntu Home 9.04) connecting wirelessly.

The Linux box used to run Kubuntu 8.04, however I decided to change to Ubuntu 9.04 Server to have a tool more dedicated to the job from scratch and to give me a chance to play with some other features.

I installed a Samba server at install time, and have also added a GUI to the box. Upon plugging in the wire from the router, the Netowrk manafer responds by telling me that a connection is made.

However, if I enter the network places window, all that pops up is Windows Network, which open trying to open returns "Unable to mount location. Failed to retrieve share list from server."

If I open the network window on either other machine, they show the other, but neither show the Server.

Before the complete reinstall the Kubuntu Server showed up fine, so what's changed for this not to?

If it's any help/hinderance, I have also installed Webmin to admininster the server.

I have checked the Workgroup of each machine in question, they are all the same, and on the config site for my router, the Server has an IP address assigned, however shows up with the name "ubuntu" which is not what is called. I cannot access any machine from the Server just by typing an IP either.

Any suggestions on places to look for answers, or suggestions to fix the problem would be very helpful, as I can't seem to find anywhere that replicates my exact problem.

---

### Post by swerdna on 2009-08-14
This error:>  Unable to mount location. Failed to retrieve share list from servercan result from the default firewall (called UFW) being closed to  Samba. Try turning it off and see if things improve:```
sudo ufw disable
```

If necessary, firewall manipulation can be found here: [Opening the UFW firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

Might be that, worth a shot

---

### Post by alphanaut on 2009-08-14
Try having identical users on the both boxes. Username/passord.
Does the ping reach the linux box?

---

### Post by IAmNotAUser on 2009-08-14
> **swerdna said:**
> This error:can result from the default firewall (called UFW) being closed to Samba. Try turning it off and see if things improve:```
sudo ufw disable
```If necessary, firewall manipulation can be found here: [Opening the UFW firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

Might be that, worth a shot

I tried that, restarted and still nothing.

> **alphanaut said:**
> Try having identical users on the both boxes. Username/passord.
Does the ping reach the linux box?

I added a new user to the Ubuntu box, and still no help.
Also, I get no ping response from the Windows machine. The request times out.

---

### Post by superprash2003 on 2009-08-14
try accessing the machines by its direct ip address like smb://x.x.x.x where x.x.x.x is its static ip

for reference:  [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by swerdna on 2009-08-14
You say you can't ping the vista machine -- times out:
[LIST]
[*]If you were talking about ping by IP address, then check that the IP addresses of the three machines are consistent, on the same subnet.
[*]If you were talking about ping by network name, then you need to install winbind and adjust the hosts line in /etc/nsswitch.conf to be like this:```
hosts: files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
[/LIST]

---

### Post by IAmNotAUser on 2009-08-14
> **swerdna said:**
> You say you can't ping the vista machine -- times out:
[LIST]
[*]If you were talking about ping by IP address, then check that the IP addresses of the three machines are consistent, on the same subnet.
[*]If you were talking about ping by network name, then you need to install winbind and adjust the hosts line in /etc/nsswitch.conf to be like this:```
hosts: files mdns4_minimal [NOTFOUND=return] [COLOR=Red]wins[/COLOR] dns mdns4
```
[/LIST]


The main Windows machine is on:
IP: 192.168.1.65,
subnet 255.255.255.0, 
with the default gateway as 192.168.1.254 
using ipconfig /all at the command prompt in Windows. 

The Ubuntu machine reports 
IP 192.168.1.64, 
mask 255.255.255.0 from ifconfig -a, 
with the Bcast 192.168.1.255. 

Is the difference between the gateway/Bcast causing the issue?

Pinging the Ubuntu box from Windows returns the request time out, sorry. Pinging FROM the Ubuntu machine returns

```
PING 192.168.1.65 (192.168.1.65) 56(84) bytes of data.
ping: sendmsg: Operation not permitted.
ping: sendmsg: Operation not permitted.
ping: sendmsg: Operation not permitted.
ping: sendmsg: Operation not permitted.
```

I already had winbind installed, i added the line, do I need to restart a process or should it just work?

> **superprash2003 said:**
> try accessing the machines by its direct ip address like smb://x.x.x.x where x.x.x.x is its static ip

for reference:  [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

Attempting that on the Ubuntu machine I receive a message saying "Could not display "smb://192.168.1.65" Error - failed to retrieve share list from server. Please select another server and try again."

---

### Post by swerdna on 2009-08-15
> Is the difference between the gateway/Bcast causing the issue?No that's OK

Where is the gateway as seen from the Linux box? Run this command: ```
sudo route
```It will show in the second column (Gateway column) at the bottom.

---

### Post by dmizer on 2009-08-15
Do you have a firewall enabled on the Windows machine?

---

### Post by IAmNotAUser on 2009-08-15
> **dmizer said:**
> Do you have a firewall enabled on the Windows machine?

I did, but it was set to allow file sharing and password protected sharing was off. I turned off the firewall and nothing changed, I then turned the firewall back on and told it to ignore Local Area Connection 2 (the wired line) and no change again. Also, the laptop connects fine to the Windows machine when I boot that in Ubuntu, so why would the server not connect?

> **swerdna said:**
> No that's OK

Where is the gateway as seen from the Linux box? Run this command: ```
sudo route
```It will show in the second column (Gateway column) at the bottom.

This is my output:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
```

---

### Post by dmizer on 2009-08-15
> **IAmNotAUser said:**
> I did, but it was set to allow file sharing and password protected sharing was off. I turned off the firewall and nothing changed, I then turned the firewall back on and told it to ignore Local Area Connection 2 (the wired line) and no change again. Also, the laptop connects fine to the Windows machine when I boot that in Ubuntu, so why would the server not connect?


Well, something is blocking you, because you can't even ping. So you have something between your Ubuntu box and your Windows box. Maybe an antivirus or some other network security tool on either your Ubuntu or Windows box.

---

### Post by swerdna on 2009-08-15
When I google this:> ping: sendmsg: Operation not permitted.

I see cases where iptables is blocking transmission. What do you get when you run this:```
sudo ufw status
```Also, try turning UFW off and then try to ping out. Is there a firewall other than UFW running?

---

### Post by IAmNotAUser on 2009-08-15
> **swerdna said:**
> When I google this:

I see cases where iptables is blocking transmission. What do you get when you run this:```
sudo ufw status
```Also, try turning UFW off and then try to ping out. Is there a firewall other than UFW running?

That command returns:
```
Status: inactive
```

I cannot find any other modules installed on the server that are causing a firewall to run, what should I be looking for? I went through webmin and did not see anything else, and I did not install any other firewalls knowingly at any point.

I don't think it's anything on the Windows box when my laptop booted to Ubuntu can see the machine fully.

---

### Post by IAmNotAUser on 2009-08-15
I looked into iptables and here is the output of sudo iptables -L.

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.1           
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       all  --  anywhere             224.0.0.1           
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  anywhere             224.0.0.1           
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

```

Is that how it should be?

---

### Post by swerdna on 2009-08-15
Mine is so different from that. But I simply can't understand it.

This is concerning, present in all three:```
DROP       all  --  anywhere             anywhere
```

I can't advise on this.

I did see, after I googled that string, that someone had a similar problem that cleared after they flushed iptables (run man iptables and look at option -F).

But I emphasise that I know no more about this than you do.

---

### Post by dmizer on 2009-08-15
When IP tables is allowing all traffic, it will look like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

Do you have Firestarter installed or is there some particular reason (internet connection sharing) that you need a firewall enabled locally?

---

### Post by IAmNotAUser on 2009-08-15
> **swerdna said:**
> Mine is so different from that. But I simply can't understand it.

This is concerning, present in all three:```
DROP       all  --  anywhere             anywhere
```I can't advise on this.

I did see, after I googled that string, that someone had a similar problem that cleared after they flushed iptables (run man iptables and look at option -F).

But I emphasise that I know no more about this than you do.

> **dmizer said:**
> When IP tables is allowing all traffic, it will look like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

Wow, man iptables is nice and long :| I did notice that swerdna, but was not sure whether that was normal, hence posting it onto the forum.

Thanks for posting yours dmizer, that was a lot of help. Using the -F switch did flush the tables correctly, however the policy remained at DENY which when I use the commands

```
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
```combined with the flush command, suddenly I can ping out of the system, the Windows machine appears on the network page of the Ubuntu machine, and I connect remotely on the Windows machine :D Thanks for all your help.

However:

> **dmizer said:**
> Do you have Firestarter installed or is there some particular reason (internet connection sharing) that you need a firewall enabled locally?

On restart, the iptables are repopulated back to policy of DENY and drop in every table. I do not have Firestarter installed. I do not really need a firewall enabled locally. My net connection is complex in that I have a wireless router for my LAN with only one Windows computer connected to the internet via a mobile broadband dongle. That computer does not share the connection.

How would I find out what is populating the iptables on reboot?

I don't want to have to do anything messy such as create a bash script to reset the table how I want them on login, I want to find the problem at the source if possible.

---

### Post by dmizer on 2009-08-15
This is something you would have done yourself, as IPtables isn't turned on by default. You probably followed a howto somewhere that included iptables directions. Since there are numerous ways of saving IPtables configurations, it could be in a number of locations.

First check /etc/iptables.rules (or anything in /etc/ that references iptables) and if it exists, delete it.

Also check the /etc/network/interfaces file to see if there is any reference to a "pre-up iptables-restore ..." remove the line.

There may be a reference in /etc/rc.local as well. It really just depends on how knowledgeable the person was who wrote the tutorial you followed. It might help if you can remember what tutorial you followed.

---

### Post by IAmNotAUser on 2009-08-17
> **dmizer said:**
> This is something you would have done yourself, as IPtables isn't turned on by default. You probably followed a howto somewhere that included iptables directions. Since there are numerous ways of saving IPtables configurations, it could be in a number of locations.

First check /etc/iptables.rules (or anything in /etc/ that references iptables) and if it exists, delete it.

Also check the /etc/network/interfaces file to see if there is any reference to a "pre-up iptables-restore ..." remove the line.

There may be a reference in /etc/rc.local as well. It really just depends on how knowledgeable the person was who wrote the tutorial you followed. It might help if you can remember what tutorial you followed.

There is nothing in any of those places about iptables. I saved a blank profile to /etc/iptables.rules and added the rule to /etc/network/interfaces as pre-up iptables-restore, and yet it still repopulates the table on reboot.

I did not follow any tutorials, I have installed a number of packages, but the only one I can think of that has anything to do with iptables is Webmin, which offers a way to modify the rules, but did not have those specific rules in the config.

I have finally found a way to get it to work though. I created a script called iptablesclear.sh which contained:

```
#!/bin/bash
sudo iptables INPUT ACCEPT
sudo iptables FORWARD ACCEPT
sudo iptables OUTPUT ACCEPT
sudo iptables -F
sudo iptables -X
```

and then added the strict to /etc/rc.local.

This clears the tables on login, and works great. :)

However, are there any other suggestions as to where the script could be that is setting the deny rules?

---

### Post by dmizer on 2009-08-17
There are several firewall modules in webmin, I suggest looking through all of them to see if there are any default rules in place there.

---

