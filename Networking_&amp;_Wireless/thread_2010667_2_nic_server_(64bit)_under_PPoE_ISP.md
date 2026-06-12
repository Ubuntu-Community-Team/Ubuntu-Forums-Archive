---
title: "2 nic server (64bit) under PPoE ISP"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by hawaiiman on 2012-06-25
Ubuntu 12.04 server(64bit) running from an ADSL ISP. This was a clean install. 
Goals: to reduce traffic (to ISP), increase security for win clients, add dns cache,database,print server, on ADSL connected network.
Little experience, so having a hard time.
I installed eth1 and updated to new driver onboard eth0 is 8111b eth1 is 8111c. Both support r8168.
I don't believe ISP will allow static ip. The modem/wifi outer/switch is a TP-Link w8901G. There is an advanced setup which has an option for bridge mode. 
The threads I've read seem to focus on eth0 with a static ip I want to divide the LAN by using 192.168.1.0 255.255.255.224 as we have 3 buildings of 18 classrooms each, a library with student access to internet, and teacher/administrative machines.Ideally would like to have diferent security settings for each group, and some printer sharing.
I believe having dns cache will hopefully reduce traffic on the ADSL line.
So far, despite best efforts, I've had no luck in getting eth1 to link with my laptop (through a switch) as a test bed. I am setting up at home, as we have the same isp at school.
I have no problem with re-installing 12.04 to eliminate wasted time back tracing what I've already done. Eth0 will link to internet at times, and router is still PPoE.

---

### Post by houstonbofh on 2012-06-26
You are really trying to reinvent the wheel here.  There are several free projects that will give you what you want without all the work.  Untangle and M0n0wall are two that I have contributed to in the past.

However, if you want to get it to work, and you will be using the TP link for routing, NAT, and all the Internet connectivity, read up on bridging with brctl, and setting up a filtering bridge and Squid.  Not trivial.

---

### Post by hawaiiman on 2012-06-26
[houstonbofh]("http://ubuntuforums.org/member.php?u=123056"), Thank you very much. After beating my head against it for a while, I was coming to that realization. Fortunately, it isn't about achieving a particular goal I have in mind as much as it is making the greatest possible improvement in the situation for the school. Until recently I had been setting this up for a fiber connection with static ip, but last week the isp was changed. My purpose in outlining the situation at the school and my goals was invite to suggestions as to how to make this new server a truly useful tool in the present environment
Print server? the clients are currently all winxp, so I suppose printer sharing in win?
Database? Right now important files for particular projects are stored on individual clients, with no file sharing. Under the prior regime, there was an older hp ml350 running freebsd as server, and something was preventing file and printer sharing under win.
Caching dns? Just my idea as a means to reduce bandwidth on an already undersized internet connection.
Subnetting? A way to improve security by applying specific firewall rules appropriate to classes of users.
One issue that has been troubling, even when attempting a static ip connected server, I can't get eth1 to link to anything. Can't ping it,doesn't get an ip, if i assign an ip it doesn't help.
If it helps, I can turn off PPPoE and run bridge mode in the tp-link.
I'll take a look at the places you mentioned. Tanks again

---

### Post by hawaiiman on 2012-10-11
I found I can do it with IPTABLES POSTROUTUNG command to forward to eth0 without a bridge or much else. Works great.

---

