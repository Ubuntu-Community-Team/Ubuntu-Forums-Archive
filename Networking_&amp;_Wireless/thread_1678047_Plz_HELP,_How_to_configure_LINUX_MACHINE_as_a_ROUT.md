---
title: "Plz HELP, How to configure LINUX MACHINE as a ROUTER with one Network Card"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by Ketobbey on 2011-01-29
I am such a noob at this. I really need to find a Ubuntu for Noobs book to get me up to speed with Linux.

I want to set my PC up like this but I have no Idea what I have to do, terminal window wise, to do any of this.

Could someone please help me but "noobing" this up for me so I can get the network finished, please.

Thanks Heaps.

> It’s a bit older but a very cheap way to use a Linux Machine as an  internet Router/Gateway. There is no need to be a LINUX expert to do  this task. No need to have two physical fast Ethernet cards. Sharing  internet connection with only one physical fast Ethernet card is very  easy using the under given rules.
 Required Items to configure a Router on LINUX Machine are given as under;
 
[LIST]
[*]One Physical **Fast Ethernet** Card
[*]**DSL/Cable/Fiber Optic** Internet Connection with Public IP Address.
[/LIST]
 1) Please configure the Fast Ethernet first like under given;
 a) Assign Public IP address to the Fast Ethernet Card with the followings;
 **i) ****Eth0**
 ii) IP Address **(61.5.156.1)** change with your public IP address
 iii) Net Mask (Provided by the Internet service provider) **(255.255.255.248)** change with your net mask
 iv) Default Gateway **(61.5.156.146)** change with your Default Gateway
 v) Preferred DNS **(203.143.22.22)** change with your preferred DNS
 vi) Alt. DNS **(203.153.240.10)** Change with your alt. DNS
 b) Create a virtual IP address on this Fast Ethernet Card
 i) Copy and paste the configuration file of the eth0 with a new name **eth0:0**
 c) Assign a private IP Address like you have assigned the other computers in your local area network
 **i) ****Eth0:0**
 ii) IP Address **(192.168.1.10)**
 iii) Net mask **(255.255.255.0)**
 iv) Default Gateway (leave this blank)
 2) Creating forwarding rules with iptables:
 # Delete and flush. Default table is “filter”. Others like “nat” must be explicitly stated.
 3) iptables –flush – Flush all the rules in filter and nat tables
 4) iptables –table nat –flush
 5) iptables –delete-chain
 # Delete all chains that are not in default filter and nat table
 6) iptables –table nat –delete-chain
 # Set up IP FORWARDing and Masquerading
 7) iptables –table nat –append POSTROUTING –out-interface eth0 -j MASQUERADE
 8 ) iptables –append FORWARD –in-interface eth0 -j ACCEPT
 9) echo 1 > /proc/sys/net/ipv4/ip_forward
 # Enables packet forwarding by kernel
 10) Create a route for internal packets:
 11) route add -net 192.168.1.0 netmask 255.255.255.0 gw **61.5.156.146 **dev eth0
 # Change **61.5.156.146 with your Gateway IP Address**
 Configuring PCs on the office network:
 All PC’s on the private office network should set their “gateway” to  be the local private network IP address of the Linux gateway computer. **192.168.1.10 change with your own gateway**
 The DNS should be set to that of the ISP on the internet.
 **Or you can configure your own DNS server on this LINUX machine; I will try to explain that in a later post.**
 **Configure the firewall to control the security.**
 **First flush everything and then allow limited ports and IP Addresses**
 12) iptables -F
 13) iptables -A INPUT -i lo -p all -j ACCEPT – Allow self access by loopback interface
 14) iptables -A OUTPUT -o lo -p all -j ACCEPT
 15) iptables -A INPUT -i eth0 -m state –state ESTABLISHED,RELATED -j ACCEPT – Accept established connections
 16) iptables -A INPUT -p tcp –tcp-option ! 2 -j REJECT –reject-with tcp-reset
 17) iptables -A INPUT -p tcp -i eth0 –dport 21 -j ACCEPT – Open ftp port
 18) iptables -A INPUT -p udp -i eth0 –dport 21 -j ACCEPT
 19) iptables -A INPUT -p tcp -i eth0 –dport 22 -j ACCEPT – Open secure shell port
 20) iptables -A INPUT -p udp -i eth0 –dport 22 -j ACCEPT
 21) iptables -A INPUT -p tcp -i eth0 –dport 80 -j ACCEPT – Open HTTP port
 22) iptables -A INPUT -p udp -i eth0 –dport 80 -j ACCEPT
 23) iptables -A INPUT -p tcp –syn -s 192.168.1.0/24 –destination-port 139 -j ACCEPT – Accept local network Samba connection
 24) iptables -A INPUT -p tcp –syn -s trancas –destination-port 139 -j ACCEPT
 25) iptables -P INPUT DROP – Drop all other connection attempts. Only connections defined above are allowed.
 26) alter the Linux kernel config file: /etc/sysctl.conf
 Set the following value:
 27) net.ipv4.ip_forward = 1
 28) Service iptables save
 Now you can test by opening a page in internet explorer that your  Linux router/gateway for internet connection sharing is working or not.  If everything goes according to the above given instructions your  router/gateway is ready to be used by your users in your local network.
[LEFT][COLOR=#000000]
Read more: [http://www.itoperationz.com/tag/linux-machine-as-a-router/#ixzz1CSeK70zf](http://www.itoperationz.com/tag/linux-machine-as-a-router/#ixzz1CSeK70zf)[/COLOR][/LEFT]


---

### Post by gordintoronto on 2011-01-29
Where did you find this steaming pile of dung? Any idea how old it is?

---

### Post by Ketobbey on 2011-01-29
> **gordintoronto said:**
> Where did you find this steaming pile of dung? Any idea how old it is?
???
No, haven't a clue.
Why is it a steaming pile of dung? I figure your from the city? Cause that stuff it really good on your roses.
But anyways, do you know a better way to do this??? I really need help and your comment is anything but helping. 

Cheers for your interest,

Ketobbey:lolflag:

---

### Post by Rab22 on 2011-01-29
> **Ketobbey said:**
> I want to set my PC up like this but I have no Idea what I have to do, terminal window wise, to do any of this.


Are you asking for each of the commands to do this? To set the IP addresses provided in the document you quoted, you'll want to use [ifconfig]("http://manpages.ubuntu.com/manpages/maverick/en/man8/ifconfig.8.html"). I believe your biggest problem is going to be that it's likely your external IP address (the one provided by your ISP) will be dynamic and assigned via DHCP. If that is the case, you'll need to perform some additional steps.

---

### Post by kerry_s on 2011-01-29
it's useless with out 2 ethernet cards. 1 for the isp, 1 for the pc.
have you ever seen a router with 1 ethernet only?

---

### Post by Ketobbey on 2011-01-30
> **kerry_s said:**
> it's useless with out 2 ethernet cards. 1 for the isp, 1 for the pc.
have you ever seen a router with 1 ethernet only?

So how does windows do it so easy?

1 Ethernet card, 1 hub(switch), other PC's Connect to it using only  1 Ethernet card.

Widows gets a bad rap yes, but From all I have read it make networking so easy.

So if windows can connection share with 1  Ethernet card, why can't Ubuntu(Linux) do it then?

---

### Post by Ketobbey on 2011-01-30
> **Rab22 said:**
> Are you asking for each of the commands to do this? To set the IP addresses provided in the document you quoted, you'll want to use [ifconfig]("http://manpages.ubuntu.com/manpages/maverick/en/man8/ifconfig.8.html"). I believe your biggest problem is going to be that it's likely your external IP address (the one provided by your ISP) will be dynamic and assigned via DHCP. If that is the case, you'll need to perform some additional steps.

wow thats a good point. I was really stuck on that one.

Well that make things read a little easier now, thanks heaps. But yeah I would have to configure the Linux server (ubuntu) each time I reset the network. Grrr

I have never had any issues setting up a network with Windows but Linux is really lacking in this area.

If you have 1 windows machine and 1 ethernet card in it, you set your connection (the one connecting to the net) to internet connection share and your done, run your modem into a switch and then run cables out into other PC's and your done. Internet shared.

Why is Linux so late in making ICS simple?

---

### Post by robert shearer on 2011-01-30
@Ketobbey  > I really need to find a Ubuntu for Noobs book to get me up to speed with Linux.

This book is freely downloadable...
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

This page has much of what you will need to ease you into Ubuntu...
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by Ketobbey on 2011-01-30
> **robert shearer said:**
> @Ketobbey  

This book is freely downloadable...
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

This page has much of what you will need to ease you into Ubuntu...
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

Nice one there mate, Thanks heaps :D

I will read them both. I found Ubuntu/Linux for dummies but it's as basic as they come. I need to learn the command lines and the bases of all Unix/Linux stuff. I loved DOS back in the day. taught myself to make batch files, then learned goldtree to edit in hexadecimal. And then taught myself how to network. But all under windows. I really want to get the hang of Ubuntu/Linux. Thanks you so much for this info.

Ketobbey

---

### Post by Rab22 on 2011-01-30
> **kerry_s said:**
> it's useless with out 2 ethernet cards. 1 for the isp, 1 for the pc.
have you ever seen a router with 1 ethernet only?

Actually, I believe you can do just that if you alias the interface. You'll make eth0 and eth0:0, and then assign eth0:0 the external IP address. Using iptables, you can route data from eth0:0 to eth0 for the network.

> **Ketobbey said:**
> wow thats a good point. I was really stuck on that one.

Well that make things read a little easier now, thanks heaps. But yeah I would have to configure the Linux server (ubuntu) each time I reset the network. Grrr

I have never had any issues setting up a network with Windows but Linux is really lacking in this area.

If you have 1 windows machine and 1 ethernet card in it, you set your connection (the one connecting to the net) to internet connection share and your done, run your modem into a switch and then run cables out into other PC's and your done. Internet shared.

Why is Linux so late in making ICS simple?

I wouldn't say that Widows networking is "easier", it's just that you are more used to doing it. Also, I find that Windows either "works" or it "does not work" and when it doesn't I find it difficult to do good problem resolution as there are so many different things to look at (ipconfig, net commands, network and sharing center, devices, etc). I can say that 95% of all the things I need for problem resolution in Linux for networking is a few commands -- not that there aren't GUI applications to help :)

No, you wouldn't have to reassign/restart the interface each time. You would most likely just need to setup [dhcp client]("http://linuxpoison.blogspot.com/2009/03/how-to-configure-dhcp-client.html").

Hope this helps!

---

### Post by kerry_s on 2011-01-30
> **Ketobbey said:**
> So how does windows do it so easy?

1 Ethernet card, 1 hub(switch), other PC's Connect to it using only  1 Ethernet card.

Widows gets a bad rap yes, but From all I have read it make networking so easy.

So if windows can connection share with 1  Ethernet card, why can't Ubuntu(Linux) do it then?

you didn't mention a hub. 
that is connection sharing, different from being a router!
linux can do that, it can be a hardware router, it can be a hardware firewall.

try the docs:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by mips on 2011-01-30
In this thread of yours [http://ubuntuforums.org/showthread.php?p=10400254](http://ubuntuforums.org/showthread.php?p=10400254) you were advised what to do (Post 14 & 16) but you are ignoring that and going in continuous circles.

Which is the same as this [https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu) Internet Gateway Method (iptables)

---

### Post by robert shearer on 2011-01-30
@Ketobbey 
> I really need to find a Ubuntu for Noobs book to get me up to speed with Linux. 

Here's another with more command line examples...
[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

---

### Post by Ketobbey on 2011-01-30
ok this helps too, because thats the second time some one has said that to me.

I am going to read these articles (heaps :D ) and I will try the above ideas out.

Thanks heaps. I will let you know how I am getting on,

If anyone can spell this about in NOOB for me in the mean time feel free.

Cheers all
Ketobbey

---

### Post by Ketobbey on 2011-01-30
> **kerry_s said:**
> you didn't mention a hub. 
that is connection sharing, different from being a router!
linux can do that, it can be a hardware router, it can be a hardware firewall.

try the docs:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I am using 1 and only 1 network card/ ethernet card.

The above article requires 1 card, but lets me nothing of how I set the card as eth0:0?
I need help with this... :C

> **Re: Plz HELP, How to configure LINUX MACHINE as a ROUTER with one Network Card** 			
 			 			 		   		 		 		In this thread of yours [http://ubuntuforums.org/showthread.php?p=10400254](http://ubuntuforums.org/showthread.php?p=10400254) you were advised what to do (Post 14 & 16) but you are ignoring that and going in continuous circles.

Which is the same as this [https://help.ubuntu.com/community/In...Sharing#Ubuntu]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu") Internet Gateway Method (iptables)
 		                   		  		  		 		 			 				__________________
				[COLOR=DeepSkyBlue]**So Long, and Thanks for All the Fish**[/COLOR]
[COLOR=Blue][How To Ask Questions The Smart Way]("http://www.catb.org/%7Eesr/faqs/smart-questions.html")[/COLOR]
spiralinear.org for inquisitive minds 			
 		 		  		  		 		 			 				 				* 					 						Last edited by mips; 1 Hour Ago at 07:12 PM.. 					 					 				*


thanks mate, but there is very little info given here as to the how of it all for a new Ubuntu user. I need more help than this thats why I have taken this to the next level with the help I have been given. I would like to have the trail of this end with a simple way for any new user with a little understanding to be able to do themselves with little help.

The way the info has been give to me so fare is like this: to send a rocket to the moon with an man in it you will need a man and a rocket. Have fun at the moon when you you get there...

I am not being disrespectful I am a noob and need to be breast feed Ubuntu :C Waaa

But as I have said before all help is much welcomed as I plane to tie this all up neatly when the answer is made simple and clear.

I don't know how to make my ip read it's self and to what place I would add the commands. I don't understnd where I am to get the eth0:0 configuration comands to make the eth0 be eth0:0 as well. I have only been at this about a week and I have most functions doing what I want but making the  Ubuntu PC ICS is being a bit harder to do than I first thought it would be, as I am used to windows, and clicking on 1 setting to change my pc in a server(ish) PC under windows.

Keep the help coming, I am thank full for it all.

P.S I have read a lot of the free PDF and all of the Ubuntu for dummies. Ubuntu for dummies is just that, But the Free PDF is most like what I need. I am having a brake from it now and will start up with it tomorrow again after I have applied for more jobs.

Ketobbey

---

### Post by YesWeCan on 2011-01-30
> Widows gets a bad rap yes, but From all I have read it make networking so easy.
:mrgreen::mrgreen::mrgreen:
Now that's funny!

Really, I know it appears to you to be the case but this is the first time I have ever heard Windows praised for making networking easy! He he.


Why are you insisting on using 1 ethernet card for a router? This is a real hack. Whether or not Windows supports it does not make it less of a hack. Actually, that is a general statement about Windows.

---

### Post by YesWeCan on 2011-01-30
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

You need to set up the ISP ethernet interface as dhcp so that it gets assigned its IP address from the ISP's modem. The local ethernet interface needs to have a static address and subnet because your other local PCs will need to use it as a gateway. They may have to use it for dhcp too in which case you need to set up a dhcp server.

A router normally provides several functions: firewall, gateway (between subnets), dhcp and port switch, and sometimes fancy features like website screening and VPN and anti-virus.

It is normal to have physically separate ethernet interfaces on a router so that the local subnet is physically separate and protected behind the firewall. What you are proposing puts everything on the same physical network.

For the sake of a $10 ethernet card...

---

### Post by Ketobbey on 2011-01-31
> **YesWeCan said:**
> [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

You need to set up the ISP ethernet interface as dhcp so that it gets assigned its IP address from the ISP's modem. The local ethernet interface needs to have a static address and subnet because your other local PCs will need to use it as a gateway. They may have to use it for dhcp too in which case you need to set up a dhcp server.

A router normally provides several functions: firewall, gateway (between subnets), dhcp and port switch, and sometimes fancy features like website screening and VPN and anti-virus.

It is normal to have physically separate ethernet interfaces on a router so that the local subnet is physically separate and protected behind the firewall. What you are proposing puts everything on the same physical network.

For the sake of a $10 ethernet card...

I wish this was the case. I have $0 dollars to my name most days, I have been out of worth for 6 months and I am still looking but can't get past the face to face interview.
In my case the $10 Ethernet card aslo will need a $10 cable, a $50+ router/or switch as I have filled my other switch up and have to switch out lan cables.
Windows = 1 nic - switch = network easy.
Ubuntu = 2 nics - switch = network behind the times.
This is a fact and not a burn thread reply.
I can see most of you are very Linux smart but you need to also see that this way of using 2 NIC's in redundant an unnecessary.
Windows does it with out any issues (except bad network adim) I have never had networking issues. I am runing my network now using my win 7 pc, and was running it with my XP pc until the other day I thought, "Linux is a safe way to network, this my be the best idea t change to it." - that was my true thoughts
But how old shcool is using 2 nics when another "less advanced" OS can do it with only 1???

I still don't know how to make my eth0 an eth0 and eth0:0
or even where to start.

Please help me work this out;

How do I do this please?

Ketobbey

---

### Post by Ketobbey on 2011-01-31
I am not enjoying UBUNTU!

I have a router now. Works to connect the Wii, PS3 and win7 machines but UBUNTU is not letting me on the net or even connect to the UBUNTU Laptop or UBUNTU PC.

What is going on? I am having so much issue with the network now That I am thinking of just reinstalling XP on both the UBUNTU pc....

Your help would be fantastic.

Ketobbey

---

### Post by Ketobbey on 2011-01-31
> **Ketobbey said:**
> I am not enjoying UBUNTU!

I have a router now. Works to connect the Wii, PS3 and win7 machines but UBUNTU is not letting me on the net or even connect to the UBUNTU Laptop or UBUNTU PC.

What is going on? I am having so much issue with the network now That I am thinking of just reinstalling XP on both the UBUNTU pc....

Your help would be fantastic.

Ketobbey
Hey it's working now! UBUNTU FTW!!!!!!!!!!!

It just did it's own thing while I was at this pc typing to you guys.
[solved] - got a router and passed around the issue.

THANKS TO EVERYONE THAT OFFERED HELP! I AM STILL READDING THE HELP FILES YOU SENT ME LINKS FOR!

ALL THE BEST

Ketobbey

[www.youtube.com/Ketobbey](www.youtube.com/Ketobbey)   :guitar:     ):P

:p
:popcorn:

---

