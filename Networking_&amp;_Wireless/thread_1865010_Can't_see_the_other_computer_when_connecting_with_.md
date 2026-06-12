---
title: "Can't see the other computer when connecting with Ethetnet cable"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by stevenlake on 2011-10-19
[SIZE=2]I have two computers.

----------------------------------------------------

01.
Desktop: Windows XP SP3

(Manual IP address:192.168.1.1)

02.
Laptop: Linux Mint (Ubuntu-based edition)

(Manual Ip address:192.168.1.2)

-----------------------------------------------------

I am trying to use an Ethernet cable to share files between these two computers.
[COLOR=Red]
Problem:

I can not see the XP shared files from Linux laptop.

(But I can see the Linux shared files from XP desktop.)

(Rephrase: Desktop can see laptop but laptop can not see desktop.)
[/COLOR] [/SIZE][SIZE=2]
Please advise how to solve this issue.

Thank you.

xp1.
[IMG]https://lh4.googleusercontent.com/-HcOHztv7sII/Tp8OU_lNniI/AAAAAAAAAWI/lFmwjE8LWzc/s1600/xp1.png[/IMG]

xp2.
[IMG]https://lh3.googleusercontent.com/-kDgb5-VKpVI/Tp8OVWgaUWI/AAAAAAAAAWU/zShCRLd5BjA/s1600/xp2.png[/IMG]

xp3.
[IMG]https://lh5.googleusercontent.com/-7ZcppboiOFU/Tp8OVbt8m5I/AAAAAAAAAWQ/MITZhhX9SLI/s1600/xp3.png[/IMG]

xp4.
[IMG]https://lh5.googleusercontent.com/-50zRR4q6QXU/Tp8OWMM5riI/AAAAAAAAAWk/_MOAZM9Eg1c/s1600/xp4.png[/IMG]

xp5.
[IMG]https://lh3.googleusercontent.com/-zgQFm5RIYgw/Tp8aOZjyBSI/AAAAAAAAAYc/2bIFHeoOd8U/s1600/xp5.png[/IMG]

m1.
[IMG]https://lh4.googleusercontent.com/-g1Pobg7i9LA/Tp8OWOBwqOI/AAAAAAAAAWo/q3Z3iAXF0RE/s1600/m1.png[/IMG]

m2.
[IMG]https://lh5.googleusercontent.com/-2hw4Juq9usU/Tp8OWlG7RTI/AAAAAAAAAW0/4iYjTOJ4Y4k/s1600/m2.png[/IMG]

m3.
[IMG]https://lh6.googleusercontent.com/-D0WjlODnIM4/Tp8OXrv4NSI/AAAAAAAAAXM/7ZslzFnGfg8/s1600/m3.png[/IMG]

[/SIZE][URL="https://sites.google.com/site/stevenlakeshih/home/ubuntu"]
[/URL]

---

### Post by jonobr on 2011-10-19
Im guessing that this is also a closed in network because the configuration doesnt really mirror a real home network

Any who This is more a networking thing then a sharing thing, but the gateway on each device is incorrect.

The gateway should be the device that handles your traffic if it is not on the local network.

Ie your on a 192.168.1.x network
if you have a packet destined for 172.18.1.x the computer will know that this is not on the local network and so will send to the default gateway.

Im not sure if its messing up your shares, but I would recommend setting the default gateways to a 3rd different IP address just for a test.
It may be messing something up,

Additional, as I think about it, if this is a routing issue, then ping from one machine to the other and see if one side fails.

---

### Post by papibe on 2011-10-19
How the machines are connected? Do you have a router? if so, what's its address?

Are you able to ping to each other?

Regards.

---

### Post by stevenlake on 2011-10-20
The IP addresses and the method I use is modified from "damgar" reply #7 on this page.
[http://www.linuxquestions.org/questions/linux-networking-3/file-transfer-using-ethernet-cross-over-cable-802756/](http://www.linuxquestions.org/questions/linux-networking-3/file-transfer-using-ethernet-cross-over-cable-802756/)

How the machines are connected? 
-- using a straight through Ethernet cable.
It seems my network adapters can automatically "cross over".

Do you have a router? 
-- Yes, but I didn't use it.
I do have one to access the Internet.
But in this case I just directly connect two computers with an Ethernet cable.

Are you able to ping to each other?
-- Yes and No.
XP can ping Linux.
Linux can't ping XP.

Thank you.

---

### Post by docbop on 2011-10-20
Describe the physical network.   hub, switch, computers.    Also make sure you haven't plugged one of the computer into the uplink port.

---

### Post by jonobr on 2011-10-20
Your xp firewall (if your using it) could be blocking ICMP,
IPtables -on linux, did you modify or change that?

Posting results from /etc/network/interfaces may also help.
also the results of netstat -rn


The post 7 you mention, Im not shure of the reasoning of putting the other machine as the gateway.

The gateway on a network is the device which will route packets when the are not destined for the local network, so again that config doesnt make a whole heap of sense.

One thing is for sure, its not a samba issue, its much lower then that

---

### Post by stevenlake on 2011-10-20
> **jonobr said:**
> Your xp firewall (if your using it) could be blocking ICMP,
IPtables -on linux, did you modify or change that?

Posting results from /etc/network/interfaces may also help.
also the results of netstat -rn


The post 7 you mention, Im not shure of the reasoning of putting the other machine as the gateway.

The gateway on a network is the device which will route packets when the are not destined for the local network, so again that config doesnt make a whole heap of sense.

One thing is for sure, its not a samba issue, its much lower then that

Problem solved.

I leave the default gateway field blank and disable the firewall.

Now it works.

Thank you everyone so much for all your help. I really appreciate it.

:p  :p  :p  :p  :p

---

