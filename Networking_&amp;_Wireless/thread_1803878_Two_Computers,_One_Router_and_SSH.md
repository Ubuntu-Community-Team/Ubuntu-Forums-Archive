---
title: "Two Computers, One Router and SSH"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by Rikeshar on 2011-07-14
Hello everyone. I've got two desktop computers, one connected by LAN and the other connected wireless to a single router. I'm trying to set up to be able to SSH into each one individually. 

The one I have had working before putting the second computer on the network was setting up in the port forwarding: 192.168.1.50:22   I then went to Network Connections, Wired, clicked on ethernet connection, and manually edited the DHCP address to 192.168.1.50, the netmask to 255.255.255.0, and the gateway to 192.168.1.1. Once I did this, I could remote in perfectly fine.

Now, I tried setting the other computer up to be 192.168.1.60 and opened port 32 on the router. However, now whenever I put set up the SSH program to go to My.IP.Here:32, it routes it to the first computer, and not the second. 

Would anyone have an idea on how I can get it to route to the second computer?

EDIT: I should mention that I also have, on the first computer, 192.168.1.50:5900 set as the VNC connection. I can connect, on the local network, to 192.168.1.60:5900 to the second computer, even though in the router this port isn't open for an IP ending in .60

---

### Post by papibe on 2011-07-14
A couple of things:
[LIST]
[*]You don't need to open ports in the router if the machines are inside your LAN (that's for traffic that comes outside your network).
[*]It is easer to use hostnames instead of IPs.
[*]If you really want to use IPs, you need to config your router and/or machines to use static IPs .
[*]The default port for ssh is 22, and does not produces conflict to have several machines using it. If you want to change that port you do it on /etc/ssh/sshd_config
[/LIST]

Hope it helps.

---

### Post by Rikeshar on 2011-07-14
Thanks for the quick reply! The reason I'm opening ports is because I want to be able to SSH into this second computer from outside the network as well. 

When I set the first computer to 192.168.1.50 and the second to 192.168.1.60 I thought I was configuring them to have static IPs, is this not the case? From my limited understanding, when I open I port on the router, I tell it what IP to route it to.  For instance, when the router gets traffic trying to come through port 22, it sends it to 192.168.1.50. Is this not how it works? If not that would explain why when I opened port 32 to go with 192.168.1.60, it's not working.

---

### Post by Bucky Ball on 2011-07-14
Yea, not that difficult. If you have static IPs, then Places>Connect to Server. Choose SSH from the drop down menu. Insert the IP and password of the machine you are trying to network with. You will be warned about some certificate or the other (because first time you are connecting to the networked machine, you won't get it next time), and you're there (or at least should be). An icon labelled with the IP of the networked machine should appear on your desktop. You can make a permanent link also so the connection is always in your Places, but see if you can get the network happening first.

Yes it is that easy, or should be. As mentioned, you shouldn't need to open ports. Just put in the standard IP. ;)

---

### Post by papibe on 2011-07-14
> **Rikeshar said:**
> When I set the first computer to 192.168.1.50 and the second to 192.168.1.60 I thought I was configuring them to have static IPs, is this not the case
That probably should do it, but you have to check a couple of things. There're routers that only supports static IPs in a predefined range. If that the case, make sure that those addresses are in that range.

> **Rikeshar said:**
> From my limited understanding, when I open I port on the router, I tell it what IP to route it to.  For instance, when the router gets traffic trying to come through port 22, it sends it to 192.168.1.50. Is this not how it works? If not that would explain why when I opened port 32 to go with 192.168.1.60, it's not working.

I would recommend to first have the ssh working on your LAN, and then trying to config and use it from the Internet.

In that regard: in order to the connect to port 32 on 192.168.1.60 you need to:
[LIST=1]
[*]Change the line 'Port 22' to 'Port 32' in /etc/ssh/sshd_config
[*]Restart the ssh service by running:
```
$ sudo service ssh restart
```
[/LIST]

Hope it helps.

---

### Post by Rikeshar on 2011-07-14
It seems like it should be that easy, but it's not!

I've got a program on my iphone called Remoter, which allows both VNC and SSH access. This is what I"m using to test to this with.

My router's IP is 12.34.567.899 (an example of course).

In my router I have the sever ip address of 192.168.1.50 and on that I've opened port 22 for SSH and 5900 for VNC. 

Now, to be able to remote into my first computer, after enabling Remote Desktop, I had to go to Network Connections, click the connection and click edit. From there I go to the tab called IPv4 and change the Method drop down box from Automatic (DHCP) to Manual. When this is done I make the "Address" 192.168.1.50, the "Netmask" as 255.255.255.0, the "Gateway" as 192.168.1.1 and the DNS server as 4.2.2.2.

I have to set this in order to be able to remote in to the computer. Someone told me it was because I was behind a NAT firewall, but I'm not sure. 

So, after I do this, I can VNC on port 5900, and SSH on port 22 by setting up 12.34.567.899:5900 or :22.

So, now I have a second computer on the network, and I want to be able to remote into it from my phone or another computer. So, in the router I open up ports 6900 and 32, on server ip 192.168.1.60, and on my computer's Network Connections I add the above information, except with the 192.168.1.60.

So, I can connect locally within the network just fine. But if I try connect using my VNC or SSH program with 12.34.567.899:6900 or :32, it actually connects to the first computer, instead of the second one.


Also, I have changed the ssh config file to look for port 32, but it's still routing to the first computer :(

---

### Post by papibe on 2011-07-14
Interesting.

It looks like is the router's fault. Did you check your router, so that you can confirm that it recognized your static IP settings on your machines?

BTW, which brand and model is it? are you using DD-WRT?

Regards.

---

### Post by xpresshred on 2011-07-14
> **Rikeshar said:**
> Hello everyone. I've got two desktop computers, one connected by LAN and the other connected wireless to a single router. I'm trying to set up to be able to SSH into each one individually. 

The one I have had working before putting the second computer on the network was setting up in the port forwarding: 192.168.1.50:22   I then went to Network Connections, Wired, clicked on ethernet connection, and manually edited the DHCP address to 192.168.1.50, the netmask to 255.255.255.0, and the gateway to 192.168.1.1. Once I did this, I could remote in perfectly fine.

Now, I tried setting the other computer up to be 192.168.1.60 and opened port 32 on the router. However, now whenever I put set up the SSH program to go to My.IP.Here:32, it routes it to the first computer, and not the second. 

Would anyone have an idea on how I can get it to route to the second computer?

EDIT: I should mention that I also have, on the first computer, 192.168.1.50:5900 set as the VNC connection. I can connect, on the local network, to 192.168.1.60:5900 to the second computer, even though in the router this port isn't open for an IP ending in .60

I think its your router fault. please check it.

---

### Post by Rikeshar on 2011-07-14
What should I be checking exactly? I know next to nothing about networking :-/

My router is a Netgear WPN824v2

How can I check to see if it recognizes the routes? I know it recognizes the 192.168.1.50 at least.

---

### Post by Rikeshar on 2011-07-14
Oh my goodness. I feel so dumb. My ssh client was defaulting to port 22, and where I thought I was supposed to change it, I wasn't, and it kept defaulting to port 22 instead of what I set up. When I corrected this, all works fine.

So sorry to waste your time, but thank you for the help!

---

### Post by Drenriza on 2011-07-14
> **Rikeshar said:**
> Hello everyone. I've got two desktop computers, one connected by LAN and the other connected wireless to a single router. I'm trying to set up to be able to SSH into each one individually. 

The one I have had working before putting the second computer on the network was setting up in the port forwarding: 192.168.1.50:22   I then went to Network Connections, Wired, clicked on ethernet connection, and manually edited the DHCP address to 192.168.1.50, the netmask to 255.255.255.0, and the gateway to 192.168.1.1. Once I did this, I could remote in perfectly fine.

Now, I tried setting the other computer up to be 192.168.1.60 and opened port 32 on the router. However, now whenever I put set up the SSH program to go to My.IP.Here:32, it routes it to the first computer, and not the second. 

Would anyone have an idea on how I can get it to route to the second computer?

EDIT: I should mention that I also have, on the first computer, 192.168.1.50:5900 set as the VNC connection. I can connect, on the local network, to 192.168.1.60:5900 to the second computer, even though in the router this port isn't open for an IP ending in .60

Now i dont know how advansed your router is, but the easiest in my eyes is to do, the following.

#1 give the computer, you want to ssh to from outside your network. A static ip address. 192.168.50.x 255.255.255.0
#2 give your second computer a 192.168.50.x 255.255.255.0 address aswell.
#3 on your router, configure static NAT.
#3,1 Configure NAT so, whenever traffic comes to your public ip address x.x.x.x on port 22 (ssh) it will automatically be forwarded to 192.168.50.x (your local lan machine). 

And from their you would be able to ssh to the rest of your lan.

EDIT: I just saw in #10 that this is resolved.

---

### Post by papibe on 2011-07-14
There must an admin page on your router, so you can see the list of machines that are connected and which IP addresses were assigned to them.

Some routers have 'memory' and always set the same IP to a particular computer (based on its mac). That is usually a very good feature, but since you changed your settings on the client machines, maybe that is causing problems.

Go to the router's manufacture website and get as much information on how is the best way to use statics IPs on a network using your router.

If the router have the ability to assign static addresses to its clients by itself, one solution could be to reset your machines to dynamic and use the server to map the IPs to the computers.

Just some thoughts,
Regards.

---

### Post by papibe on 2011-07-14
> **Rikeshar said:**
> When I corrected this, all works fine,
Glad you solved it.

> **Rikeshar said:**
> ...So sorry to waste your time, but thank you for the help!...
:D  Don't worry, keep enjoying the forums!

Regards.

---

