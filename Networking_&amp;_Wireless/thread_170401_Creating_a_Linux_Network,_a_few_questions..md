---
title: "Creating a Linux Network, a few questions."
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by NeghVar on 2006-05-04
Sorry if this has been asked a million times, whenever I search on the web all I get is setting up a file server with Windows 2000 or how to configure Apache for a web server and such.

What I want to do is build a file server running Ubuntu for my Ubuntu Computer. If I was doing this with all Windows I would probably have it already done but I don't have the cash for another license.

What I already have is a Cable connection that goes into a router which connects to my Ubuntu box and a Windows box which I have no control over. Now coming into this room is 1 LAN cable and I would like to keep it that way so basically the first part of my question is;

Can I take the line from my Router plug it into a switch then have a line going out to my Ubuntu Box as well as the proposed File Server. The idea behind this is obviously the network but also the Internet, so would that work?

Onto my second part, KVM switches, will I have any problems with getting one or are there any companies that don't like Linux? I'm kinda short on space so the idea here is to just run the server in the corner and use the KVM to control it if I ever had to, basically the Server is going to just sit there and offer up its HD space for my use.

Thats all I can think of for now, but if anyone has any other suggestions are good reading relating to this situation I would greatly appreciate any of it. I'll probably come back with a few more questions in a bit but that should be enough to get me going.

---

### Post by matthewstory on 2006-05-04
Can't answer anything about the KVM switch, but about the first part:

> Can I take the line from my Router plug it into a switch then have a line going out to my Ubuntu Box as well as the proposed File Server.

This shouldn't be a problem and can be done with a low end switch, it won't affect in anyway how the boxes interact with the router and the WAN in general.

> The idea behind this is obviously the network but also the Internet, so would that work?

This will take more work but should also be no problem.  I'm assuming that what you mean by this is that you want to be able to access your fileserver from the internet and have your fileserver access the internet from behind the router.  It should automatically be able to do the second part.  

To access the file server from the internet you should probably set the server up with sshd (for sftp, vastly superior to ftp) or ftpd if you really want to transmit data insecurely.  Make sure that this port accepts incoming connections from anywhere (if you have iptables configured on the box), if you do and don't know how to do this respond back and i'll let you know.  Then log on to the router that you can control, and have the router foreward all incoming connections over port 22 (if sftp, not sure what the ftp port is off the top of my head) to your box, identified by the private ip, and Viola.  The router should then open a pinhole for port 22 and through NAT foreward all incoming file server traffic to the file server.  You probably want this box to have a static IP, so configure the /etc/network/interfaces file and give it one:

auto eth0
iface eth0 inet static
address <ip address>
netmask <netmask, probably 255.255.255.0>
gateway <ip address of the router>
broadcast <first 3 numbers of ip address .255 (most likely)>

---

### Post by NeghVar on 2006-05-04
Great information. Im not so concerned about accessing the data from the net, although that is a good idea if I ever need it when Im away. Its just with networking and networking in Linux in particular Im not great. 

Mainly I was wondering if the switch would allow me to get onto the net with no problems, Ive never had a situation before where I had 2 network sharing devices on the same line and wasnt sure if they would work like that.

---

### Post by matthewstory on 2006-05-04
sorry left out some details.  To install sshd:

apt-get sshd

Before you edit the /etc/network/interfaces file you need to bring down the device:

ifdown eth0

then edit it

nano /etc/network/interfaces

or if you have gnome insalled:

gedit /etc/network/interfaces

make sure you comment out the old eth0 entry, probably looks like this;

auto eth0
iface eth0 inet dhcp

then bring the device back up:

ifup eth0

---

### Post by matthewstory on 2006-05-04
the switch won't change anything at all.  You won't even see the switch from the router or the computer.  By "see" I mean that it doesn't count as a connected device on the router, and the computer's next hop will still be the router, not the switch.  You probably won't even have to renew your DHCP request to get it to work.  Though don't quote me on that.

---

### Post by NeghVar on 2006-05-04
Awesome, thanks for that, now I hope its all so great for a KVM switch to lol

---

### Post by NeghVar on 2006-05-04
Ok, next stupid question.

When I get this stuff all hooked up will I need to do anything special, basically I want it to show me the FS HDs in my computer area, is that possible or am I just dreaming?

---

### Post by Iowan on 2006-05-04
Once you get SSH running, you may discover that the server can run headless.  I have a monitor and keyboard plugged into mine, but almost never use them - I can do (almost?) anything I need to do via SSH.

---

### Post by kmartinson on 2006-05-07
RE: KVM
In case you were still wondering...you should have absolutely no problem with your KVM...I currently use one (a cheap one - on 4 PCs) between 2 seperate windows boxes, 1 SuSe box and 1 Ubunbtu box(Dapper beta w/ xgl and compiz).

---

### Post by NeghVar on 2006-05-07
Cool thanks, I figured they would be fine but i wanted to make sure before I went and waisted money on something that doesnt work, currently i refuse to buy any hardware that will not work on linux out of the box and as far as im concerned ati is like christ... something to be avoided at all costs

---

### Post by bluenova on 2006-05-08
A basic KVM is purly hardware and doesn't interact with any software, so it should work accross with machine with the right connections (PS/2 etc).

---

### Post by jdusablon on 2006-06-10
> In case you were still wondering...you should have absolutely no problem with your KVM...I currently use one (a cheap one - on 4 PCs) between 2 seperate windows boxes, 1 SuSe box and 1 Ubunbtu box(Dapper beta w/ xgl and compiz). Hey I know a guy who also has that config. He also has no problems.

He's a good linuxer, I mean he would never be caught dead with a ./ in front of /usr/local/bin!

---

