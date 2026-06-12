---
title: "Reg: DHCP Server Advantages / Disadvantages"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2013-08-20
We are planning to setup DHCP Server. But however we should know the difficulties in setting up a DHCP Server as well as its advantages & disadvantages. Can anybody clarify us the following pls?

1. How does the server knows, this client belongs to this subnet?
2. Is it possible to offer fixed IP Address from DHCP Server to specific hosts based on its MAC Address?
3. Do we need to have seperate DHCP Server for Seperate VLAN's? If it is not needed then how it is setup?
4. What are the advantages and disadvantages of using a DHCP Server?
5. We have a set of production servers with fixed IP Address which is assigned manually. Can we tell the DHCP Server not serve these IP Addresses to clients as this is already reserved for production environment.

---

### Post by Kevin_Arnold on 2013-08-20
I can answer a few questions.

2: Yes. These are generally called DHCP reservations. We use them for network printers. Before we even plug in the printer, we have the reservation set up and all of the print queue settings are ready to go.
3. No. 1 DHCP server should be able to serve up IPs for all the VLANs. There is configuration needed, though.
4. If you're talking about end user machines and not servers or something, I'm amazed you're not already using DHCP. There is almost no question, go DHCP. Makes management MUCH easier.
5. Yes. We have all of our servers on a 10.0.0.0 /24 network. Everything below 10.0.0.100 is for static IP address use. The DHCP server starts handing out IP address to DHCP clients at 100, so there will never be any overlap.

Edit: I should note, our end user computers are all on 172.16.x.y networks where x is their VLAN based on location or use (such as phones and security nodes.)

---

### Post by karthick87 on 2013-08-20
See we have some 10 to 15 departments. In those departments we have given few users some specific application access based on IP Address.  In this scenario setting up DHCP Server is really a pain, isn't it? Any solution to this problem?

Also each department has different VLAN's, so can anybody tell me how the Servers responds when it receives a request from hostX of VLAN-1 and hostX of VLAN-2. How does the server serves this request? How it identifies, the request is from this VLAN?

---

### Post by 1clue on 2013-08-20
Been there, done that.

Linux-based DHCP is the happy answer for all of what you're saying, and more.  In spite of what my post might sound like, ***DHCP is the ONLY reasonable way to manage a network with more computers on it than you have fingers.***

When I did it, a Linux-based DHCP server worked across VLANs but a Windows-based one did not.  It was probably because I was using the default thing that came with Windows, and there was probably a payware one that did the fancy stuff.

***Edit:** I used a Linux-based server in production, I never got the Windows one to work right.*

OK so here's the stuff I think you should know:
[LIST=1]
[*]For VLANs it's not just DHCP and the DHCP server you have to worry about, but you need to forward the DHCP packets across the switch from the VLAN in question to the DHCP server.
[*]That leads to another thing:  DO NOT send packets from more than one VLAN across the same network card without using 802.1q.  Doing so is broken and you will have errors that make no sense but break your network anyway.
[*]I used Cisco managed switches to handle all this, configuration details will vary based on manufacturer but ANY managed switch worth buying will handle it, and so will Linux-based switches.
[*]In addition to DHCP you will want to configure DNS to handle dynamic names for your clients.  You want to give the clients the names they want, it's a real pain to do it any other way.
[/LIST]

For the servers:
[LIST=1]
[*]You want to give the really critical servers (dhcp, dns, routers) static IP addresses, but you want to register them in DHCP as well with their static MAC address, because sooner or later some bozo (it was me at my office) will turn on DHCP for some stupid reason.
[*]For each VLAN, you want a pool of dynamic addresses, and a reserved range of static addresses even if you don't have immediate plans for something static there.  
[/LIST]

Now finally for the DHCP and DNS:  You NEED a failover server for business environments.  For DHCP at least when I did it, you had a pair of servers you could configure.  Each would be a primary server and a failover.  The way I did it, I had an identical map of each VLAN.  I don't remember the details but this is an approximation:
[LIST=1]
[*]a.b.c.1 -- router
[*]a.b.c.2-19 -- static reservation
[*]a.b.c.20-120 -- Primary reservation for server 1, secondary reservation for server 2
[*]a.b.c.121-250 -- Primary reservation for server 2, secondary reservation for server 1.
[/LIST]

Your DNS is a little different.  At first I tried to be symmetrical matching a dns to a dhcp.  Pain in the rear.  You want a primary and backup DNS for your entire domain.  Again the Linux-based stuff is first class.  You can have an internal-only DNS and an external one, and you can also split the domain if you want, internal inside the firewall and external outside.

You want the DHCP servers to be on separate hardware, separate power sources and uninterruptible power supplies.  If you lose all your DHCP servers your network will work fine for awhile, then slowly your entire network will dissolve into a puddle of misery that makes no sense.  I actually came to consider the DHCP servers to be every bit as important as the database that had our finances on it, or even more so.

Notes regarding hardware:
[LIST=1]
[*]DHCP is not a "heavy" server.  It can be relatively modest hardware (not wimpy, but modest) but you want it to be RELIABLE.  Don't use desktop hardware, IMO.
[*]You also want decently reliable hardware for the DNS.  Again, not the heaviest traffic in your office but it needs to work.
[*]Do yourself a favor and get genuine managed switches from a respected company.  When we got Cisco gear it was the most expensive hardware in the entire office, and we never regretted it.  Later we upgraded to real server hardware which eclipsed the networking cost, and the switches held up fine.
[*]Make sure everything can handle IPV6 even if you don't plan to use it.  Older non-IPV6 hardware is going to be dirt cheap, new or used.
[*]We tried both new and used hardware, and the new was more economically feasible for a real business.  If you try used you will come to understand what I'm talking about.
[/LIST]

I would recommend you find a non-business place to try out your DHCP server.  We made a special experimental VLAN (vlan 13) and kept our stuff on there until we knew what was going on.

I would also recommend using virtual machines at least for your experimental stuff.  You can save a bare-bones server operating system as a backup, and throw away the messed up mess every time you mess up.  Then it takes 5 minutes to get back where you were.

---

### Post by 1clue on 2013-08-20
> **1clue said:**
> Been there, done that.

...

OK so here's the stuff I think you should know:
[LIST=1]
[*]For VLANs it's not just DHCP and the DHCP server you have to worry about, but you need to forward the DHCP packets across the switch from the VLAN in question to the DHCP server.
[*]**That leads to another thing:  DO NOT send packets from more than one VLAN across the same network card without using 802.1q.  Doing so is broken and you will have errors that make no sense but break your network anyway.**
[*]I used Cisco managed switches to handle all this, configuration details will vary based on manufacturer but ANY managed switch worth buying will handle it, and so will Linux-based switches.
[*]In addition to DHCP you will want to configure DNS to handle dynamic names for your clients.  You want to give the clients the names they want, it's a real pain to do it any other way.
[/LIST]

...



Clarification:
802.1q is what defines trunking. You need a network card that supports 802.1q for each host that touches the trunk.  These cards can be aware that there is traffic from more than one network on the same wires.

Nothing good can come from cheating here.  If you have two logical networks running on the same physical network without using 802.1q properly, some things will work and some things will not.  The things that will not will be the things that cost you the most money because they're not working.

The switch configuration that forwards dhcp across VLANs does not count.  By the time it gets to your VLAN the packets are normal ethernet packets with tcp-ip and all the magic happens in the switch.

***Another edit:** I'm talking about my one commercial installation, that was stayed active for about a decade, after which it was no longer my job description.*

---

### Post by karthick87 on 2013-08-20
If some 100 hosts are requesting for IP Address all at the same time, then will DHCP offer IP Address parallely or it offers in a queue manner?

---

### Post by 1clue on 2013-08-20
Packets are handled by the network stack sequentially.  I'm pretty sure the dhcp server was threaded, but I never ran into any issues.  I started with about 80 workstations and maybe 10 servers, and when we finally replaced the old hardware my setup was still running fine with some 250+ workstations and maybe 8 bigger physical servers, with quite a bit of virtualization in there.

We changed them because the hardware was old, not because of a failure.

---

### Post by 1clue on 2013-08-20
Oh yeah.  Basically everyone came in at 8 and turned on their boxes.  So basically 100 hosts probably DID hit it all at the same time.

---

### Post by karthick87 on 2013-08-20
And routers are not necessary if all the hosts on the network are on the same subnet?

---

### Post by 1clue on 2013-08-20
Um.

Technically that's true, but that's not really going to save you money.

The reason for subnets is to limit the amount of chatter any random host has to see.

If you have everyone in a medium sized business on one subnet, that would be the equivalent of trying to have a conversation between two people in the train station at Chicago during rush hour.

If you break it down into subnets, then you have something like a book store, where there are acoustic barriers and a reasonable number of people you have to listen to at any point.

I'm not sure where the practical limit is because it's different for every network.

You CAN make your own router, but it would be cheaper and better to buy one.  A good switch has extremely low latency, which you will definitely notice with 100 hosts.  I had a Linux-based firewall with desktop hardware when we first got started, just an average desktop with Linux on it and two normal network cards, and it was slow.  We spent the same amount on a cheap router and saw a dramatic improvement.  Nowadays I don't even try to do the Linux router thing unless I'm trying to experiment with something.  A cheap switch and a decent home router are much faster.

I'm not a professional at this.  I did my own setup for the network I mentioned above, and I've done a bunch of playing with Linux at home, but that was quite awhile back and there was only one situation (the one I described) where it saw any real traffic.  With the scenario I actually experienced, what I said is my best advice.  At several points we had a professional come in for Cisco configuration and advice, but basically he added some fancy stuff and left what I did alone.  He said it was fine.

We wound up with no more than maybe 30 hosts on any particular VLAN, and less on most.  That was based on organizational/access decisions more than on traffic, but I think the group with the most hosts tended to have the most networking issues.

I know that some networks are more densely populated.  Again, it all depends on how heavy your network traffic is for each host.  We had pretty heavy network traffic.  There was net-to-net VPN traffic on some of them, but on one VLAN we had each user hooking up their individual host to some remote VPN which means a lot of encrypted traffic.  Encryption causes an increase in data.

---

### Post by karthick87 on 2013-08-20
Thanks a ton for a neat and clear explanation [**[COLOR=#000000]1clue[/COLOR]**]("http://ubuntuforums.org/member.php?u=799622") :p

---

### Post by 1clue on 2013-08-20
Maybe you could give some real numbers here?  Don't get too specific about things that might affect your security, but how many workstations, and how many types of work, and how many servers?  What was your intended setup?  What's your budget, what sort of hardware do you already have?

---

### Post by 1clue on 2013-08-20
And what sort of work are you doing?  Is it mostly on the workstation, or a lot of RDP, standard website based stuff, or VPN from hosts, or what?

---

### Post by 1clue on 2013-08-21
BTW I think I may have scared you about that 802.1q thing.

You don't have to use trunking at all on a switch.  You can dedicate each switch port to a single VLAN.  I hadn't even heard of VLANs until I got the Cisco switches.

Another thing you could do if you need to be on a budget:  Get managed switches with a smaller number of ports than you have hosts, and then use cheap switches for each VLAN to expand the number of available ports on each VLAN.

That's a lower bandwidth solution but probably workable for awhile.

If you're dealing with 80 or 100 workstations on your network, then you're at a point where you need to face some uncomfortable facts.  You can use cheap Walmart switches up to 60 or so computers and not suffer too bad.  For a bigger network, you start getting some serious problems that you don't see on a smaller network.

Here's an exercise:  Figure out how much money your company loses for an hour of downtime due to network failure.  This has the following components:
[LIST=1]
[*]The cost of the broken component replacement.
[*]The cost of wages/salary for an idle staff.
[*]The cost of lost revenue for that hour.
[*]The cost of buying a possibly inferior replacement part at local costs rather than having a spare you ordered online.
[/LIST]

Note that there's a double cost to the owner of the business:  You're not only losing money because you have to pay the staff, but you're losing revenue from money you aren't making that you would have made.  And the fact that it's not an hour you're going to be down.  Figure 15 minutes to figure out that it's a broken switch, 20 more to realize you don't have enough ports left over to make it work, and an hour or two to go find the nearest tech store and buy absolutely every cheap switch they have, then race back to work.  Then it's at least an hour to wire a bunch of switches in where one used to be, and then yet another hour to figure out that some of the boxes are on the wrong VLAN.  If you don't have numbers on each end of the ethernet wires so you can match the cable end with the workstation, then you're talking about twice that or more for re-wiring it.  So half a day of downtime and half a day of revenue if you're lucky.  Just ask me how I know.

Now compare that number to the cost of some good network hardware.  The good hardware and maybe even a professional on call to manage it and a nice support contract starts looking pretty good.

That disaster scenario that cost my company a day to get back to the same overloaded, unworkable setup we had before is what convinced me and the management that decent network gear was actually worth something.  It was like a magic spell that made our whole office better.

Another thing, I've not been entirely honest with my analogies.  If you're using a real network switch, even a cheap one, then each host doesn't hear all of the packets on the network, but the switch does.  The problem here is backplane speed, which is basically the speed of the computer that runs the switch.  The analogy still holds because with cheap hardware your weakest point is the switch, and it can get overwhelmed pretty easily.

Cheap switches have slower backplanes, and sometimes they cheat a little bit on bandwidth per port, and maybe even some other things.

A good switch has a high speed backplane, they can handle heavy traffic from every port.  A good *managed* switch not only handles the VLAN support but also some rudimentary rules about which traffic can go where.  It's not a full-on firewall by any means, but you can say that traffic from VLAN 8 can't go to VLAN 9.

A good switch will also bridge together with other similar hardware and allow some sort of failover.  We had two managed switches and one sort-of managed switch.  The sort-of managed switch was still Cisco gear, but couldn't define VLANs or the rules for them.  It knew what a VLAN was, but was basically a slave.  Later on I was not a part of that team anymore, they expanded it but I don't know how.

Those three Cisco switches were bridged together to form a single conceptual switch.  We made it a policy that there would always be one switch worth of ports unused.  We had VLANs allocated so that all the ports in each column of ports were the same VLAN, even across switches.  If a switch went down, we could pull the cables out and move them to one on the same column on another switch without sacrificing our network structure.

To phrase this differently, we had 3 "good" switches.  Each switch had 2 rows of 40 (I think) ports each.  We had the switches on a rack, which basically means that all the ports lined up.  Ports 1 and 2 on each switch were all VLAN 1 for example, while ports 2 and 3 might be VLAN 2.  Each column had 6 ports and we made sure that only 4 were used.  That gave us one switch worth of 'failover.'


At one point we were using a couple Walmart-category switches on the bigger VLANs to give us more ports.  It didn't really work all that well, the backplane speed sucked on the cheap switch.

---

### Post by karthick87 on 2013-08-21
Am into Server Team. Managing and Monitoring Server Performance, Security, Package / OS installation and DB Management..

We have 2 No's Cisco 2960 Routers & 42 Switches (All Managed) & 45 Servers which runs linux / windows..

We have so many departments, say..

Admin = 25 Users

HR = 15 Users

Production = 230 Users

Developers = 185 Users

Compliance = 10 Users

Infra = 385 Users

and so on...

Each department has separte VLAN. And few hosts in the respective VLAN's are given IP Based access to few applications.. As of now IP Addresses are configured manually for all the hosts and network equipments. Planned to go with DHCP in the future.

---

### Post by 1clue on 2013-08-21
Wow.

OK so we had 2 3560's and I can't remember what the other one was.  I don't know if that's better or worse than what you have.  It was good stuff back when we got it.

OK forget whatever I said about switches, you obviously know more than me about it.  I only ever had to deal with 3 managed switches.

You're doing this without DHCP?  That's outrageous.

OK so start out small on the DHCP.  One server, set it up like you expect two servers because the failover will be made second.

A couple points before we start:
[LIST=1]
[*]You can configure the switch to forward DHCP to some server on another VLAN without causing problems, no traffic will happen until somebody tries to use DHCP to that host.
[*]Your control is to only affect a few users when trying out an idea, then add load in a reasonable step, then see how your load is affected.
[*]Don't make grand sweeping changes until you know what works for your network.  Go one VLAN at a time, a few hosts at a time.
[*]I would partially configure one or two less-critical VLANs (meaning not the one the big bosses are on, and not the one the IT staff is on) rather than completely configure each one.  You have another failover server to configure, and it will be the main server for half of each of its VLANs.
[*]Don't go over two VLANs without configuring your failover.
[*]You need to make sure the changes you are making actually work.  For DHCP that takes awhile, you're waiting for the lease to expire.  You can shorten the lease time but that has repercussions for your users and can seriously dent your network traffic if you get carried away.  Once a significant number of people start depending on it, return the lease times to the default.
[*]Once you have two VLANs and failover, let it run for a week or four so you know you don't have unanticipated problems.
[/LIST]


[LIST=1]
[*]I would make a test VLAN that works with a static laptop on it, give it full access like you would normally have.
[*]Then set up the DHCP server on that same network.
[*]Get it to work with your workstation.
[*]Move your workstation back to your normal VLAN if it's a small group and they are all within yelling distance.  Or if you can't tolerate even a single bump in that net, make another VLAN to test from.
[*]Set up the DHCP forwarding, which will certainly be a different command than what mine was years ago.
[*]Get your workstation to work with DHCP across VLANs.  If you're using MAC-based mappings for specific machines then you'll probably need to change the dhcp config on the server too.
[*]When you get it working, set up your config like I said before; leave a few addresses for statics, allocate about half of what's left for your current server, and leave half for the other server.
[*]Move your server to its final place and adjust the configs of your DHCP server and of the switch.
[*]Get it working for your box again.
[*]Choose a smaller, less important VLAN as a guinea pig.
[*]One by one, turn on DHCP on various computers on that VLAN until you have half of the users using DHCP.
[*]Set up another VLAN for DHCP forwarding.
[*]Set up the DHCP server for that VLAN.
[*]Switch half of the users to DHCP.
[*]Set up the second DHCP server to be failover, and get the other half of each VLAN over to DHCP.
[/LIST]

With your network size, you'll probably run into problems I didn't.  You might want to monitor a few days when people come in, and make sure the network bandwidth and CPU and memory utilization on your server are up to snuff.  I used fairly moderate hardware and had no problems, but you've got a single VLAN that was bigger than our entire network.  You may need more DHCP servers.  I wouldn't let any parameter get over about 40% of what you consider to be acceptable.  If you have one server go down the load is likely to go above double the normal load for the remaining server.  Don't know why.

As of when I last looked, dhcpd only had provision for paired servers.  You couldn't link more servers.  If that's still true, you might need more boxes.

You could still put all the DHCP servers on the same network technically, but it might not be prudent.  If one VLAN goes down (switch configuration error for example) you might take the whole office down.  I put one server on one VLAN and the other on another VLAN.  It's easy to tell the DHCP server to ignore the VLAN it's physically attached to and only deal with a few remote VLANs.


There are a lot of things you can configure with DHCP.  You can set up defaults for each VLAN for all sorts of network services.  I would test these on a small scale before you get crazy with that.  DHCP changes trickle through very slowly, and the corrections trickle through every bit as slowly.  Every VLAN you add to a server, test it with one or two hosts for a significant time before you light up the whole VLAN.

The good part is that you can define different lease times for each VLAN.  You could set yourself up on the test VLAN and give it the minimum lease time, then apply the change to other VLANs.  I moved my box from VLAN to VLAN continuously while I set all this stuff up.

It's late and I'm babbling.  I hope this is useful.

---

### Post by karthick87 on 2013-08-21
Thankyou so much for such a brief answer. It was really helpful as we are moving forward with DHCP. But tell me how do we identify the culprits in DHCP environment? For example if somebody has done something wrong which violates the company policy and their IP Address is traced, Using that IP Address we cannot make sure to figure out the user who breached the company policy as the IP will get renewed in given lease period. In this scenario how this case will be handled? It is time consuming one to check for the server logs to find the associated MAC ID and the IP Address for the particular time and then take action. Any other way?

---

### Post by 1clue on 2013-08-21
Well, yes.  There's a bunch you can do.  Unfortunately you're going to pay up front in labor.

I'm not sure if you're being sarcastic about the short answer.  I type about as fast as I can compose what to say, so I tend to get verbose.  Let's just say I'm not on twitter.  :)

Since you're just now setting up DHCP that means you're not using any sort of network boot.  That gives you the most control, but I don't know enough about that to be helpful.

First thing, DHCP has a sort of inertia to it.  Switching IP addresses affects sockets that are already connected. A short lease time and no ability to request the same address you had last time makes for some network errors that are irritating.  Every network stack I know of, and dhcpd, allows keeping the same address.

Network setup:
[LIST=1]
[*]Link your DHCP servers to DNS in a dynamic way.  This is similar to what Windows Active Directory does.  It doesn't sound all that important but it makes things a lot easier.
[*]Once you configure a VLAN, make it reject unknown MAC addresses.  This makes it so they can't add a network interface to get around your restrictions.
[*]Have one or two networks that allow unknowns, like a conference room and your setup VLAN.  Those VLANs either are only accessible from a specific spot (your setup VLAN) or they only get to the Internet (the conference room), not to servers the miscreants might use.  That means if somebody does find a way to circumvent your network setup they can't do work.
[*]The conference room can have a hardwired ethernet port for the presenter, which would have normal access to internal facilities.
[*]Label all the ethernet cables so you can see which desk they go to.
[*]Label the VLANs right on the back of your switches so you can tell exactly what's going on from the switch rack.
[*]Have a time-out VLAN that disables all access to unnecessary resources.
[/LIST]

If somebody breaks a rule, you can go to the switch, yank them out of the current VLAN and put them in time-out.  That's the easy physical way.  Lots of other ways including firewall rules.

Machine setup:
[LIST=1]
[*]Put a password on the BIOS.  This prevents the user from creating a new MAC address.
[*]Get the mac address into a database available to the IP addresses.  That sounds like a huge PITA but it's amazing what the miscreants will do to avoid detection.
[*]Name the box.  The name goes into your database too.
[*]Disable normal domain users from renaming their box.
[*]Track the desk that machine goes to, and if you assign your users to a specific workstation then track the user it goes to as well.
[*]You might consider printing a label with the mac address and machine name right on the system chassis in a way that's difficult to remove and easy to see from over the shoulder of the user.
[/LIST]

This part isn't as hard as you might think.  Carry a laptop with you when you convert workstations to DHCP.  Do the conversion yourself.  As the machine gets a lease, the lease will be recorded on the server.  You can have a terminal open to watch that, and copy and paste into your database as you go.  You could even make a shell script to parse the DHCP entry.

Now, your safety is in redundancy of information.  You need more than one way to get to the miscreant.

Here's some of what you can do with the above information:
[LIST=1]
[*]Use 'host a.b.c.d' to get the hostname of the miscreant's workstation.
[*]Use the database to get the name of the person based on that host.
[*]Run an app to periodically check mac addresses and names against dns reverse lookups to flag names that have changed.
[*]**arp -a | grep <ip address>** from the dhcp server to get the mac from the IP address.
[/LIST]

I'm sorry, it's getting late and I'm losing focus.  I'm sure you can think of things to do with the information you can collect.

The achilles heel to all this is that you need to keep your information up to date in order for it to be of any use.  Even so, you can still use arp -a on the server to get the IP address for the mac even with no planning, and you can use reverse dns lookup to get the current name of it too if you set that up.

---

### Post by 1clue on 2013-08-21
This thread has some interesting stuff for quickly finding relevant information for a lease:

[http://forums.freebsd.org/showthread.php?t=33240](http://forums.freebsd.org/showthread.php?t=33240)

I don't know why they're going through that much trouble though.  On my setup the DHCP server had all the arp entries for the leases, because the DHCP request packet was forwarded over with VLAN information and the arp was registered with the DHCP server's operating system.  But that might have changed.

---

### Post by karthick87 on 2013-08-21
Thankyou again :p

---

### Post by 1clue on 2013-08-22
One thing we used to do with miscreants is give them a static IP with the DHCP server.  They went into a separate VLAN (cable switch) and then we gave them a static address in the DHCP config.

Some people give every host a static IP.  That gives you both a MAC address and an IP address, and you get quick easy lookups.

Setting up each MAC address for your 'normal' work VLANs is a pain in the rear, but doing so gives you the ability to track all sorts of things based on MAC address, and setting static IPs makes it easy to map that to an IP address.  I did it for awhile and then just used grep on the dhcp config file to figure out who was who.  It gets hard to manage though.

You'll want to disable normal domain users from network configuration on their machines, and you'll want to disable unknown network cards in most places.

You'll want to monitor unknowns coming in on your wireless, if you get the same one day after day it might be somebody's phone hitting facebook.  We had our DNS cheat on the facebook.com domain, sending it to a "you better be working" page that printed the IP address, mac address and domain name.  You have been logged.

The whole point of DHCP is that you, sitting at your desk in the IT department, can change network configuration on almost any device on the network.  If you have really reliable servers you could make that most of the servers too, and the switches too.

The ultimate part of that is to use network boot images on all your basic desktop images.  That makes it so you can make changes to your test box, save them to the net boot image and then in the morning EVERYONE who uses that image gets the same config change.  It takes a bit to set up but it's well mapped ground.  You can have several images for different departments or types of use.  I'm a big fan of it but I've never done it in a real world scenario.  The guy who took over after me did, and I was a bit jealous.

The problem with that is you need a bunch of the same type of workstation.  Same basic CPU, roughly the same memory, same type of drives, same monitor resolution, same network card...

---

### Post by SeijiSensei on 2013-08-22
> But tell me how do we identify the culprits in DHCP environment? For example if somebody has done something wrong which violates the company policy and their IP Address is traced, Using that IP Address we cannot make sure to figure out the user who breached the company policy as the IP will get renewed in given lease period. 

There's really no need to have short lease periods on subnets where there are more addresses available than hosts.  If you don't need to recycle addresses, just use long lease periods to create pseudo-static addresses.  You can, of course, create static reservations for specific MAC addresses, but that's more work than using thirty- or ninety-day, or even longer leases.

Moreover, Windows clients request the same IP address when their leases expire.  If the server has not already reassigned the address, they'll get the one they had before.  I don't know how dhclient on Linux handles this, though.  Still, if you use long leases, there won't be much of a problem.

---

