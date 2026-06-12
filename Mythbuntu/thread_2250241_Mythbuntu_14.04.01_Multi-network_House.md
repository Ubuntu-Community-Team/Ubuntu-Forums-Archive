---
title: "Mythbuntu 14.04.01 Multi-network House"
date: 2014-10-27
forum: Mythbuntu
---

### Post by johnfm3 on 2014-10-27
I am building a new Myth Backend Server as my old backend died due to raid failure.

I am trying to offer MythTV to my kids network as well as the parents network (192.168.2.0/26 & 192.168.3.0/26).  My fall back plan is to build a Media network, but I am not quite ready to invest in the dedicated hardware needed such as Wifi an Wifi extenders to get coverage on my whole house.  An I really don't want a backend server on each network sharing the tuner.

My tv tuner is a HDHR Prime unit, ideally I would like add a 3rd network card dedicated for the tuner.  Mainly to prevent direct access to the tuner from the kids network.

What does it take to get MythTV to service all networks?  During the back end setup, there is no option to use 0.0.0.0.  Only Network1, Network2, and Localhost.

John

---

### Post by johnfm3 on 2014-10-27
So after a brief discussion with a moderator, I need to clarify some things...

The home environment is a single house roughly 3200 sqft with 2 floors on a 1/2 acre of land.
I have 2 separate networks, a kids an a parents network with different IP ranges an domain names.
Kids.lastname.local 192.168.3.0/26
Parents.lastname.local 192.168.2.0/26

These networks are separated by a Linux Server routing traffic between the parents, kids, dmz, an the Internet.

Due to the age of the house an the size, wifi doesn't get around very well an I have range extenders for both networks at both ends of the house with both wifi networks (Parents an Kids).  Main reason is the wires, heating duct, an copper water pipes which are between the floors blocking wifi signal from going very far.

The DMZ where my all my servers, media servers, an network gear sit in the Garage.  Wifi access points sit in the middle of the house on the bottom floor in the rec room.


Again, my issue is I would like to have 1 MythTV Frontend clients on the Parents Network as well as on the Kids Network connect to the same MythTV backend which currently has two 1 gig network ports.  1 port used on each network.  But in the GUI Backend setup, there is only a option for 1 network.

Hopefully this clears up any miss understandings.
Thanks,
John

---

### Post by johnfm3 on 2014-10-27
Correction on my first post.  To make this work correctly, am I suppose to have a Slave Server on Each network which connect to the Master backend server?

Is the Master/Slave backend traffic routable?  So if I move my backend to the DMZ an install a slave on each network?  Can the slaves talk to the backend on a different network ip range (assuming routing is allowed: which I control)?

Can the SLAVE backends be VMs?  Is it processor intensive?  Or does it just forward request to the backend?  An what about watching live TV from the tuner to the front end?  Where does the work load need to be, on the Master or Slave backend?

This is what I mean about not ready to buy more hardware.  This can get expensive fast.  Which would not make for a happy wife.

---

### Post by mattlach on 2014-10-27
I'm gathering your intent is to keep the three networks separated?

Could you place the backend server near the routing server, and install three separate NIC's in it, one for each network, set those network adapters up properly in /etc/network/interfaces the server SHOULD be able to listen to all of them, but I see where your concern is, where you have to tell the backend which network to listen to...

Does it actually obey this?   Is there no way to enter multiple address ranges?

---

### Post by johnfm3 on 2014-10-27
mattlach,
Telling the server which port to listen to is exactly the problem.  Where the server is physically located is not as important as the networks it connected too.  Ideally, I would like the backend server to have 2 network ports an listen on both.  This would be the simplest solution for now till more hardware can be purchased.  An maybe setup a 3rd network port to connect to the TV Tuner.  But that's another issue I can deal with.

What I see in the GUI is that I only have the option to listen on 1 port.  An there is NO option to manually enter a 0.0.0.0 for all nic's.

---

### Post by mattlach on 2014-10-27
Hmm..

Is there any way you could set up the requisite rules in your linux routing server to forward ports from the LAN interface on the router on each network, to the IP and port of the Mythbuntu backend?

Then point your frontends at their respective gateway and specific port you have chosen, and have the router do its thing?

This way the backend only needs to listen to one interface.

---

### Post by johnfm3 on 2014-10-27
> **mattlach said:**
> Hmm..

Is there any way you could set up the requisite rules in your linux routing server to forward ports from the LAN interface on the router on each network, to the IP and port of the Mythbuntu backend?

Then point your frontends at their respective gateway and specific port you have chosen, and have the router do its thing?

This way the backend only needs to listen to one interface.

I know I can setup port forwarding.  The question is just that, does the service work in that environment?  If I understand correctly, part of the stream is UDP which is non routable.  Now if only the communications between the tuner an backend is UDP, then all is good as long as both of those are on the same network.  If the stream between the frontend an backend is UDP, then I don't think the setting up port forwarding on my firewall will work.

John

---

### Post by mattlach on 2014-10-27
> **johnfm3 said:**
> I know I can setup port forwarding.  The question is just that, does the service work in that environment?  If I understand correctly, part of the stream is UDP which is non routable.  Now if only the communications between the tuner an backend is UDP, then all is good as long as both of those are on the same network.  If the stream between the frontend an backend is UDP, then I don't think the setting up port forwarding on my firewall will work.

John

Of course UDP is routable.

How do you think UDP traffic gets out of your house to the Internet?

Many services use UDP, including gaming services and some voice and video chatting services, and they are all routed through a typical router.

You may have to explicitly tell the router to forward it though.  When I add rules to my router (pfSense) I ahve to select traffic type.  There are many options, but TCP, UDP, TCP+UDP, ICMP and  ALL are among them.

---

### Post by johnfm3 on 2014-10-27
> **mattlach said:**
> Of course UDP is routable.

How do you think UDP traffic gets out of your house to the Internet?

Many services use UDP, including gaming services and some voice and video chatting services, and they are all routed through a typical router.

You may have to explicitly tell the router to forward it though.  When I add rules to my router (pfSense) I ahve to select traffic type.  There are many options, but TCP, UDP, TCP+UDP, ICMP and  ALL are among them.

Ok, that's worth investigating.  The Port forwarding route may be a good stop-gap for now.  I really should put in a feature request for the ability to configure multiple listening networks.

---

### Post by johnfm3 on 2014-10-27
So before I go mucking around with my network, is there any chance that via text editor I can force MythTV to listen on ALL network ports?

---

### Post by dannyboy79 on 2014-10-28
i don't think you fully understand how mythtv works. it uses a mysql database for everything, your main backend requires access to the MySQL server and that it accepts connections from other computers IF you have separate frontend's which it sounds like you do, that's the 0.0.0.0 setting. no, you can't make mysql listen on more than 1 port.  currently which network CAN see the mythtv backend, parents or kids?

your problem is purely a routing issue, not a mythtv issue. you need to figure out how to make the traffic from the other subnet make it to the subnet your mythtv backend is in.

Here's a post talking about using MythTV with multiple subnets: [http://www.gossamer-threads.com/lists/mythtv/users/548417](http://www.gossamer-threads.com/lists/mythtv/users/548417)

---

### Post by johnfm3 on 2014-10-28
> **dannyboy79 said:**
> i don't think you fully understand how mythtv works. it uses a mysql database for everything, your main backend requires access to the MySQL server and that it accepts connections from other computers IF you have separate frontend's which it sounds like you do, that's the 0.0.0.0 setting. no, you can't make mysql listen on more than 1 port.  currently which network CAN see the mythtv backend, parents or kids?

your problem is purely a routing issue, not a mythtv issue. you need to figure out how to make the traffic from the other subnet make it to the subnet your mythtv backend is in.

Here's a post talking about using MythTV with multiple subnets: [http://www.gossamer-threads.com/lists/mythtv/users/548417](http://www.gossamer-threads.com/lists/mythtv/users/548417)

My understanding of MythTV is that there is a mythTV backend service which uses SQL to store information an configurations.  The mythtv service handles a lot of the transcoding an scheduling as well as the web interface.  Then you have the front end which is nothing more than a web interface which communicates with the SQL backend which triggers the MythTV service to tackle the tasks as needed.

As I understand it, all transcoding, recording, an such is done on the Master backend server.  But confirming this understanding is what I am looking for.  Any good documentation on this would be great.

Currently the MythTV as a FrontEnd\backend is all in one, including the SQL.   Running Mythbuntu.  So mythTV service could communicate with SQL via 127.0.0.1, although then only my localhost front end would be able to communicate.  But my AppleTV's mod'd with FireCore can not see or talk to the MythTV server if its set to listen on 127.0.0.1.  An if I set the MythTV backend to listen on the kids network, the parents aTV fails to connect.  If I set the MythTV to listen to the parents network, the kids fail to connect.  I do not want traffic allowed between the two networks.

An this may be where slave backend servers may be needed.  With the master backend\sql box sitting on a dedicated media network.

---

### Post by dannyboy79 on 2014-10-28
I linked you to 2 possible solutions since you want to use MythTV across subnets. I am not a networking person and this is all about routing the traffic properly. First of all have you even made it do MySQL accepts a connection from your other subnet?

The purpose of slaves is merely to take some of the load off of the primary backend.

Here's another post which talks about MySQL and multiple subnets. [http://www.howtoforge.com/forums/archive/index.php/t-56785.html](http://www.howtoforge.com/forums/archive/index.php/t-56785.html)

---

### Post by tgm4883 on 2014-10-29
> **johnfm3 said:**
> An if I set the MythTV backend to listen on the kids network, the parents aTV fails to connect.  If I set the MythTV to listen to the parents network, the kids fail to connect.  I do not want traffic allowed between the two networks.

You can try slave backends, it may fix the issue. Otherwise you are probably looking for an enhancement request which will likely need a patch as this isn't something many people want.

I'm still not sure why you don't want to route the mysql/mythtv traffic between the networks, that is essentially what you are doing anyway.

---

### Post by johnfm3 on 2014-10-29
> **tgm4883 said:**
> You can try slave backends, it may fix the issue. Otherwise you are probably looking for an enhancement request which will likely need a patch as this isn't something many people want.

I'm still not sure why you don't want to route the mysql/mythtv traffic between the networks, that is essentially what you are doing anyway.

Based on what dannyboy said, an some reading I have done, it sounds like the backends are used as a way to offload the Heavy work from the master.  What I really need is some kind of Proxy service to take request from the clients an forward them to the Master.

Regarding the routing, If I was in a position to purchase the hardware to setup a 3rd network for Media then this thread wouldn't have even started.  The reality is that in most cases, a service such as SQL or Appache (web) can be configured to listen to ALL network connections, or limited to the single network a Administrator wants to listen on.  I can guess your thinking about this as a normal home user who has 1 network with a 24 bit mask an uses the router for your DNS, DHCP, an firewall services.  Think Corporate.  Think about what happens when you have a Enterprise level network.  My wife an I both work at Microsoft, an as such have a secured parents network which we don't allow traffic from the kids network.  The parents network has no time boundaries, the proxy an filter rules (squid/dansgardian) are setup different, an allows protocols such as VPN connections to work.  The wifi in the parents network is setup differently using Kerberos for Computer Authentication, tied to Active Directory.

In short, there should be no reason why MythTV has to be limited to listening on 1 port. An if anyone has done it, I would greatly appreciate some guidance.  Other wise this thing can just sit till I have a third network put on line or the time to dig into the configuration files.  I am not missing TV, Netflix an Vudu are doing fine.  I am just trying to set some things up for the holiday specials for the kids an visiting family.

---

### Post by johnfm3 on 2014-10-29
An before its said again by anyone else, yes I could only specifically route just MythTV traffic between networks, an I could directly force it too the MythTV server, but that is also opening up a possible security hole in my network which I don't want to risk.

---

### Post by dannyboy79 on 2014-10-29
make it so mysql can listen to multiple networks. [http://www.cyberciti.biz/faq/unix-linux-mysqld-server-bind-to-more-than-one-ip-address/](http://www.cyberciti.biz/faq/unix-linux-mysqld-server-bind-to-more-than-one-ip-address/)

---

### Post by johnfm3 on 2014-10-29
> **dannyboy79 said:**
> make it so mysql can listen to multiple networks. [http://www.cyberciti.biz/faq/unix-linux-mysqld-server-bind-to-more-than-one-ip-address/](http://www.cyberciti.biz/faq/unix-linux-mysqld-server-bind-to-more-than-one-ip-address/)

Sure thing.   As explained in your link you provided, SQL is listening on Port 3306.  Yet the Frontend clients talk to the backend on port 6544 an 6543.  So what do I need to do to get the backend service listening on those ports on both networks as well?

---

### Post by tgm4883 on 2014-10-29
> **johnfm3 said:**
> Sure thing.   As explained in your link you provided, SQL is listening on Port 3306.  Yet the Frontend clients talk to the backend on port 6544 an 6543.  So what do I need to do to get the backend service listening on those ports on both networks as well?

Patch MythTV.

---

### Post by tgm4883 on 2014-10-29
> **johnfm3 said:**
> An before its said again by anyone else, yes I could only specifically route just MythTV traffic between networks, an I could directly force it too the MythTV server, but that is also opening up a possible security hole in my network which I don't want to risk.

I'm not sure why you think putting a machine on both networks is more secure than forwarding certain port traffic to a certain machine. I'd think that would be less secure.

---

### Post by johnfm3 on 2014-10-29
> **tgm4883 said:**
> Patch MythTV.

I will check my mythtv version when I get home tonight.  Since its a new install with a new download as of 10 days ago, I suspect its fully updated.

---

### Post by johnfm3 on 2014-10-29
> **tgm4883 said:**
> I'm not sure why you think putting a machine on both networks is more secure than forwarding certain port traffic to a certain machine. I'd think that would be less secure.

I would be curious as to why you think its less secure.

---

### Post by dannyboy79 on 2014-10-29
> **tgm4883 said:**
> Patch MythTV.isn't there a config file somewhere he can manually change the ip to 0.0.0.0?

---

### Post by johnfm3 on 2014-10-29
> **dannyboy79 said:**
> isn't there a config file somewhere he can manually change the ip to 0.0.0.0?

This is how simple I would have thought this would have been :-(  Not this long drawn out thread.  I figured I would have felt stupid for asking a silly easy question an I would have been on my way.

Shoot a spot to put both IPs separated by comma or space in a config.  Something.

---

### Post by dannyboy79 on 2014-10-29
> **johnfm3 said:**
> I will check my mythtv version when I get home tonight.  Since its a new install with a new download as of 10 days ago, I suspect its fully updated.
he's saying "patch mythtv" because i believe there's currently no way to make it listen on all networks so it would require patching a file and then recompiling mythtv from source.

may i suggest you join the mythtv-users irc channel on freenode, there has to be others who have done the same thing you're after

---

### Post by johnfm3 on 2014-10-29
> **dannyboy79 said:**
> he's saying "patch mythtv" because i believe there's currently no way to make it listen on all networks so it would require patching a file and then recompiling mythtv from source.

may i suggest you join the mythtv-users irc channel on freenode, there has to be others who have done the same thing you're after

DannyBoy: Thanks for that suggestion.  I have also sent a message to the MythTV-Developers via there web page interface.

At this point, I will dig into this next weekend when I have a free day an report what I find.

---

### Post by dannyboy79 on 2014-10-29
> **johnfm3 said:**
> DannyBoy: Thanks for that suggestion.  I have also sent a message to the MythTV-Developers via there web page interface.

At this point, I will dig into this next weekend when I have a free day an report what I find.this post here makes it seem as though mythtv does already listen on all networks. [https://code.mythtv.org/trac/ticket/10763](https://code.mythtv.org/trac/ticket/10763)
do you use dns or hosts file for your dns serving purposes? have you first ensured network packets can make it from the kids network to your mythtv backend server? have you first ensured network packets can make it from the parents network to your mythtv backend server?

---

### Post by tgm4883 on 2014-10-29
> **johnfm3 said:**
> I will check my mythtv version when I get home tonight.  Since its a new install with a new download as of 10 days ago, I suspect its fully updated.

I meant you need to write a patch for the software.

> **johnfm3 said:**
> I would be curious as to why you think its less secure.

Because you are exposing the entire machine to both networks, including any attacks from the less secure network. If that machine gets compromised, it now has access to attack machine on either network bypassing your network firewall completely (which I'm pretty sure is what you are trying to avoid). 

IMHO, the correct way to set this up securely would be to put the MythTV backend on the less secure network (I'm assuming that would be the kids network), then setup your network firewall to forward any traffic from your parents network that is specifically for the MythTV box to the MythTV box on the kids network, while blocking all other traffic to the kids network. You wouldn't be allowing any traffic originating from the kids network to the parents network though the firewall.

> **dannyboy79 said:**
> isn't there a config file somewhere he can manually change the ip to 0.0.0.0?

No. That would make mysql listen on all but not MythTV.

---

### Post by johnfm3 on 2014-10-29
> **dannyboy79 said:**
> this post here makes it seem as though mythtv does already listen on all networks. [https://code.mythtv.org/trac/ticket/10763](https://code.mythtv.org/trac/ticket/10763)
do you use dns or hosts file for your dns serving purposes? have you first ensured network packets can make it from the kids network to your mythtv backend server? have you first ensured network packets can make it from the parents network to your mythtv backend server?

Dude, you are so right...  But the GUI forces you to chose a IP.
For everyone, this is a copy from first reply

[COLOR=#FF0000]The code is designed such that if you specify the BackendServerIP for that host, it will only listen on that address and localhost (127.0.0.1 or ::1).  If you do not specify anything, it will poll the addresses defined on that system, and listen on any [/COLOR][[COLOR=#FF0000]&#8203;RFC1918[/COLOR]]("http://tools.ietf.org/html/rfc1918#page-4")[COLOR=#FF0000] private network address.  That means anything in the 10.0.0.0/8, 172.16.0.0/12, or 192.168.0.0/16 address ranges, things that would be used were you running a system behind a NAT router.
[/COLOR][COLOR=#FF0000]There are only three reasons to define BackendServerIP on a host:
[/COLOR]

[LIST]
[*][COLOR=#FF0000]You are running a backend on that host, and the backend needs that address defined, both for proper configuration, and so clients on the network know how to access it. [/COLOR]
[*][COLOR=#FF0000]You want to limit the frontend from listening everywhere, and only want to allow access on a specific IP address, or only localhost. [/COLOR]
[*][COLOR=#FF0000]You are operating without NAT, directly on an internet routeable address, and need to force the frontend to listen there, when it will by default ignore it as it is not an RFC1918 private address. [/COLOR]
[/LIST]
[COLOR=#FF0000]
[/COLOR]So basically, I need to find the config file an remove the entry entered by the GUI.  Whats going to stink is I will have to set that setting, then remove it any time I open the backend config interface.

I have a DNS slave service listening on both networks running on my Linux (SLES 11 sp3) Firewall which redirects DNS request to my DNS server.

Yes, I have confirmed that WHEN my MythTV Backend is configured to listen on the Parents network, the Parents MythTV client can connect.  But the Kids client fails.  Also, when I change the MythTV to listen on the Kids network the Kids Client can connect, but the parents fails.  So I know that the Front End clients on both networks work when allowed access.  Based on what was just shown to me, it looks like I can allow MythTV to listen to ALL Private IP networks (10.0.0.0/8 172.16.0.0/12 192.168.0.0/16).  Just need to know where the Magic setting is.

---

### Post by dannyboy79 on 2014-10-29
you could try changing the master backends config.xml file but as tgm pointed out i don't believe it's that simple. again, i would check on the mythtv-users irc channel

Also, note from that link i provided you it specifically says, "**Binding to all doesn't happen anymore for reasons above my pay grade**, 
however, one of them was the problem with some distributions setting 
the bindv6only sysctl to 1, causing those users to loose IPv4 connectivity. "

---

### Post by tgm4883 on 2014-10-29
The setting in mythtv-setup that you are talking about is for the location of the master backend, not what address to listen on. The bug report that was posted is not related, as it's specifically talking about the network control functionality that exists in the frontend (eg. to control a frontend via telnet commands).

I've been talking with upstream and the backend can listen on any private address, but multiple addresses is not. IP forwarding is not supported, but may work so it's worth at least a test. Regarding adding that functionality, upstream said "since it's a minority configuration, one that actually requires some work to reproduce it's not going to be a high priority". That said, you could certainly supply a patch for review.

---

### Post by johnfm3 on 2014-10-29
So it looks like I am left with only one solution.

waiting on mythtv till I can purchase more hardware to allow 1 master backend server per network.  The bummer is in this situation I will not know what my kids are doing with out having to log on an look at random.  Where 1 backend server means we all share.  Then both backend servers can share the tv tuner, giving the parents network 1 tuner, the kids network 1 tuner, an recording the last tuner.  Or purchase another tuner so each backend can have 3 dedicated tuners.

In my thoughts for what they are worth, this whole thing is kind of silly an very short sighted that a service is unable to listen to multiple networks.  Especially since SQL an Apache have the ability to listen on different ports.  But I guess if you only expect to be used in a home environment, why do more.

Meanwhile, I will go back to PLEX an XBMC as a combined package an see if their newest releases work like the old ones to accommodate my needs.  At least PLEX could talk to Roku's (if I so choose to pull them out).

---

### Post by tgm4883 on 2014-10-29
> **johnfm3 said:**
> So it looks like I am left with only one solution.

waiting on mythtv till I can purchase more hardware to allow 1 master backend server per network.  The bummer is in this situation I will not know what my kids are doing with out having to log on an look at random.  Where 1 backend server means we all share.  Then both backend servers can share the tv tuner, giving the parents network 1 tuner, the kids network 1 tuner, an recording the last tuner.  Or purchase another tuner so each backend can have 3 dedicated tuners.

In my thoughts for what they are worth, this whole thing is kind of silly an very short sighted that a service is unable to listen to multiple networks.  Especially since SQL an Apache have the ability to listen on different ports.  But I guess if you only expect to be used in a home environment, why do more.

Meanwhile, I will go back to PLEX an XBMC as a combined package an see if their newest releases work like the old ones to accommodate my needs.  At least PLEX could talk to Roku's (if I so choose to pull them out).

I almost didn't respond to this, but I felt it was kinda silly and needed a response. A couple things

[LIST=1]
[*]Your specific situation is clearly in the minority (almost 70% of the users only have 1 host). 
[*]You're talking about an open source project where none of the developers are paid to work on it. They are a very small team and work on it in their spare time. 
[/LIST]

Personally I still think it's worth testing the port forwarding solution, although upstream doesn't believe it will work. Upstream does think it would be an interesting project though if someone wanted to do it

> <stuartm> you have to understand that since different parts of the code were written by different people at different times they found different solutions to the same problem of how to reach the backend from the frontend
<stuartm> and despite mechanisms like SSDP being added, they weren't used to their full potential because that meant making a lot of changes that would need to be carefully tested which takes time and energy
<stuartm> I think it would make an interesting project for someone though
<stuartm> scrap BackendServerIP as it's currently used, have frontends use SSDP on startup to find the backend(s), each frontend should cache the name of the backend and it's IP to make for faster reconnects, but if it's unable to connect on the old IP it can try SSDP again to find the new IP
<stuartm> that would let the backend listen on as many different networks as you want
<stuartm> you'd even be able to move a frontend between networks and the frontend would automatically rediscover the correct backend

But in the end, you are using a tired, old argument. <insert software project here> is bad because it doesn't support <insert something that less than 1% of users do> so I am going to threaten to use <insert other software project here> instead. Nobody cares that you are leaving MythTV for something else. The developers don't get paid to do this, they do it because they think it's a fun project to work on. They work on stuff that they actually use (one of the reasons livetv isn't so great). If you want to see your changes made to MythTV, you have about 3 choices.

1) Develop and submit a patch fixing this issue upstream
2) Pay a developer to do #1
3) Convince a developer to spend their spare time to do #1 for free

I would have thought that working at Microsoft you would understand and appreciate limited developer time and not sinking a bunch of effort and spare (non-paid) time into fixing something that affects 1 person.

---

### Post by johnfm3 on 2014-10-29
> **tgm4883 said:**
> I almost didn't respond to this, but I felt it was kinda silly and needed a response. A couple things

[LIST=1]
[*]Your specific situation is clearly in the minority (almost 70% of the users only have 1 host).
[*]You're talking about an open source project where none of the developers are paid to work on it. They are a very small team and work on it in their spare time.
[/LIST]

Personally I still think it's worth testing the port forwarding solution, although upstream doesn't believe it will work. Upstream does think it would be an interesting project though if someone wanted to do it



But in the end, you are using a tired, old argument. <insert software project here> is bad because it doesn't support <insert something that less than 1% of users do> so I am going to threaten to use <insert other software project here> instead. Nobody cares that you are leaving MythTV for something else. The developers don't get paid to do this, they do it because they think it's a fun project to work on. They work on stuff that they actually use (one of the reasons livetv isn't so great). If you want to see your changes made to MythTV, you have about 3 choices.

1) Develop and submit a patch fixing this issue upstream
2) Pay a developer to do #1
3) Convince a developer to spend their spare time to do #1 for free

I would have thought that working at Microsoft you would understand and appreciate limited developer time and not sinking a bunch of effort and spare (non-paid) time into fixing something that affects 1 person.


If there was an option to pay a developer to solve this, I would.  I bet it would be pretty simple.  If MySQL an Apache (2 large projects which are being used by MythTV) are able to listen on multiple ports, I suspect that permitting MythTV Backend Service to do so would not be that hard to do.  I would pledge a $250 donation for the fix to my system and a promise that its added in the next release.

As far as my understanding of Developer time cause I work at Microsoft.  I work for a company that has no issues dumping mass resources into a internal product which is used to allow for testing of external products.  As a Lab Engineer, my understanding of Infrastructure is my specialty.  Including DNS/DHCP/AD/Proxy/Firewalls an such.  At work I have a bigger concern of a Service not supporting Teaming of NIC's than whether I can listen on multiple network cards on different networks.

An if the code is so hard set on only listening to 1 port, maybe that's my solution.  Create a Virt NIC, Bridge the 2 physical an the Virt.  With MythTV listening on the Virt.  Then do some fancy internal routing.  But it shouldn't have to be that way.  Not when 2 of the services used in MythTV are designed to listen on all ports.


I would be willing to dig into this, but I have yet to hear where in the config's the BackEnd Service gets the value to listen from.  I can accept that the GUI is unable to allow this, but that GUI has to change a setting somewhere.  Whether its a config file, or a SQL DB.  Where is that?  No one has provided that information.

---

### Post by johnfm3 on 2014-10-29
Ok, I have been sitting at my mythtv box for the last hour trying to locate any reference to the IP mythTV is set to listion on.  Other than the following lines in the backend log files, I was unable to find anything.

/var/log/mythtv/mythbackend.log:Oct 26 21:29:31 mybuntu mythbackend: mythbackend[2584]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 192.168.3.7:6543
/var/log/mythtv/mythbackend.log:Oct 26 21:37:15 mybuntu mythbackend: mythbackend[3368]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 192.168.3.7:6544

This is not cool.  Can someone at least explain to me if this was by design due to Federal Regulatoins?

Is this setting in SQL?  Or has it be hard coded in the binarys as a way to deny users from changing it?

---

### Post by dannyboy79 on 2014-10-30
As i've suggested multiple times, go to mythtv-users on freenode IRC and ask the developers, you may get a quicker answer. it may be a simple edit of a source file before recompiling from source.

---

### Post by johnfm3 on 2014-10-30
> **dannyboy79 said:**
> As i've suggested multiple times, go to mythtv-users on freenode IRC and ask the developers, you may get a quicker answer. it may be a simple edit of a source file before recompiling from source.

Done.  Email sent.

Meanwhile after a bit of digging I have found the setting.  Its located in the Mythconverg DB, in the Settings Table.  An its read-only.

After a quick install of plex an xbmc, both could listen on all network cards without configuration change.  I suspect what I am going to do is set MythTV on localhost (127.0.0.1) an use it only for recording tv.  An use Plex an XBMC for serving media to the external clients.

If I come up with a reasonably sane solution as a result of the email sent to MythTV-Users, I will post it here for others to make use of.  Changing an Compiling Source is not something I would see as sane.

---

### Post by dannyboy79 on 2014-10-30
i would set the main backend server to listen to the parents network so that the parents can use mythtv-frontends. what exactly do you want the kids network to be able to do within mythtv-frontend? if it's only playback videos and nothing to do with livetv or scheduling than you could just use something like [https://www.mythtv.org/wiki/Mythlink.pl](https://www.mythtv.org/wiki/Mythlink.pl) and share the folder which has the symlink human readable files over NFS or SAMBA and just use whatever media player for the kids network that you want like xbmc or plex or whatever.

if kids network do need to create recording schedules than they could just use mythweb. only thing they're really missing with the mythtv-frontend functionality is livetv (well unless you also have like mythmusic and mythvideo setup but again there's other solutions for distributing media across subnets)

---

### Post by johnfm3 on 2014-10-30
Currently LiveTV is the only reason I am doing this.  An I could do this 1 way easier.  Just use PLEX which can listen on both networks to provide the stored videos an saved TV Recordings.  An like you said, MythWEB can be accessed by all networks.  The only thing missing is the LiveTV for the kids.  Which is why I just went out an bought a new HDHomeRun TV Tuner (w/3 internal tuners).

Better yet, all my clients have native PLEX an XBMC clients.  I was looking at replacing them with Apple TVs if I could get MythTV working for my environment.

---

### Post by johnfm3 on 2014-10-30
So I have one more option...

add a 3rd network.  10.0.0.0/8.  Set the MythTV server W/SQL on that network.  An only listen on the 1 nic.

On the parents an kids network, install a slave MythTV Backend server with nics on media an kids or parents.

the question is then, if a child client chooses a livetv show to watch, where is the transcoding taking place?  If its on the Master backend, then I can build my slave servers as VM's on my XEN virtualization server.  If the transcoding has to be done by the Slave Backend, then the slaves must by physical servers.

If I could offload all the heavy work off the Master backend, could it run on my XEN Virt Server?  I am running a HP DL360 G5 with Dual P4's an 16Gb of ram with a Raid 10 SATA 1T array.  If this is the case, I would only need 1 more machine to build 2 physical Slave Backend Servers (1 for each network).

It just comes down to where the heavy work is being done.

---

### Post by dannyboy79 on 2014-10-30
mythtv is very flexible about where you want the "jobs" to be done whether its on the master or whichever slave you choose. transcoding is considered a "job". it's all defined within the mythtv-setup on the master and any slaves.

---

### Post by johnfm3 on 2014-10-30
> **dannyboy79 said:**
> mythtv is very flexible about where you want the "jobs" to be done whether its on the master or whichever slave you choose. transcoding is considered a "job". it's all defined within the mythtv-setup on the master and any slaves.

Then I think I will need take some time an build out 2 slave servers to act a proxies basically on my XEN server.  An see how that does.  Wont happen right away.  I am waiting to see if any Dev's have any decent paths to get MythTV service to listen on multiple Networks.

I am going to say this whole process is kind of disappointing.

---

### Post by johnfm3 on 2014-10-30
Well, I can say that MythTV-Users is already going down the same path as here.  Acceptance that the Master Backend can only listen on 1 NIC.  And suggesting port forwarding.  Which in my case is not an option.

I am going to play around with slave backends an VMs for a while.  Probably wont see any further post on this thread for quite a while.

---

### Post by dannyboy79 on 2014-10-30
did you specifically ask them to point you in the direction for where that's hard coded in the source files so you could modify and recompile? that's up to you.

---

### Post by johnfm3 on 2014-10-30
> **dannyboy79 said:**
> did you specifically ask them to point you in the direction for where that's hard coded in the source files so you could modify and recompile? that's up to you.

Done.  Asked.

---

### Post by johnfm3 on 2014-10-30
About my only other option I have until I can add a third network is this....

What about creating a Virtual Nic on the MythTV Backend an give it eth2.  Set it too 10.0.0.1 an tell mythtv to listen on that.  The configure Ubuntu to forward all traffic from ports 3306, 6544, & 6543 on the 2 physical networks (eth0 an eth1) to the Virt NIC.

Then I can setup MythTV, keep all added routing an traffic local to the box.  Not muck up the rest of my network.  An do so with the hardware I currently have, not forcing me to buy new hardware.

---

### Post by johnfm3 on 2014-10-30
Do the frontend clients even need to talk to SQL?  Maybe able to keep SQL on 127.0.0.1 since the Master Backend service an SQL are the same box.

---

### Post by tgm4883 on 2014-10-30
> **johnfm3 said:**
> Do the frontend clients even need to talk to SQL?  Maybe able to keep SQL on 127.0.0.1 since the Master Backend service an SQL are the same box.

Yes, the clients talk to SQL to figure out where the master backend is

---

### Post by johnfm3 on 2014-10-30
Ok, so I am  finding all kinds of information on how to create a Virt Ethernet device which can listen on a physical device such as ETH0:0.  But what if I want to create ETH2 as a internal eth device like localhost?

To bad I can not just forward all traffic from ETH0 an ETH1 to L0.  I would just tell the backend to listen on localhost an do that.

Although, I wander if I can create a virt L0:0 with a 127.0.0.2???

hmm, something to try which could be a fun way to blow up my system.

---

### Post by johnfm3 on 2014-10-31
So this was probably one of the best explainations on the background of MythTV's ability to listen to 1 network connection...

[COLOR=#FF0000]MythTV listens on multiple ports for various services, but it only listens on one address (plus 127.0.0.1).  The way MythTV's networking has always been set up, it stores a single IP address for the database, queries the database for the backend's single address, and then connects to that single address.

MythTV previously listened on all interfaces, however during the addition of support for IPv6, stock network settings on certain distros meant that listening on all interfaces meant only listening on IPv6 addresses on all interfaces.  The various listen sockets were changed to only listen on discrete addresses, and because of the aforementioned way backend discovery happens, this did not change behavior of the frontend connecting to the backend (although there were some issues with other non-MythTV interfaces).  There are plans to move backend discovery independent of the database, and allow the user to select or the backend to auto-select multiple addresses to listen on, but this has not yet been implemented.
[/COLOR]
This being said, I am going to use it as it is an wait for the future release to look at how I want to implement this.  My setup will probably be a Stand Alone setup with MythTV an SQL on localhost (127.0.0.1) an allow the MythWEB to be used to schedule recordings (which can currently be accessed on all networks).  Then use Plex Media Server to serve the Recorded content an my Video Library to the clients on both the networks.

---

### Post by tgm4883 on 2014-10-31
> **johnfm3 said:**
> So this was probably one of the best explainations on the background of MythTV's ability to listen to 1 network connection...

[COLOR=#FF0000]MythTV listens on multiple ports for various services, but it only listens on one address (plus 127.0.0.1).  The way MythTV's networking has always been set up, it stores a single IP address for the database, queries the database for the backend's single address, and then connects to that single address.

MythTV previously listened on all interfaces, however during the addition of support for IPv6, stock network settings on certain distros meant that listening on all interfaces meant only listening on IPv6 addresses on all interfaces.  The various listen sockets were changed to only listen on discrete addresses, and because of the aforementioned way backend discovery happens, this did not change behavior of the frontend connecting to the backend (although there were some issues with other non-MythTV interfaces).  There are plans to move backend discovery independent of the database, and allow the user to select or the backend to auto-select multiple addresses to listen on, but this has not yet been implemented.
[/COLOR]
This being said, I am going to use it as it is an wait for the future release to look at how I want to implement this.  My setup will probably be a Stand Alone setup with MythTV an SQL on localhost (127.0.0.1) an allow the MythWEB to be used to schedule recordings (which can currently be accessed on all networks).  Then use Plex Media Server to serve the Recorded content an my Video Library to the clients on both the networks.

I find it slightly funny that you ignored multiple people on the mailing list that mentioned that what you are doing is the less secure method as opposed to doing the port forwarding.

---

### Post by johnfm3 on 2014-11-03
> **tgm4883 said:**
> I find it slightly funny that you ignored multiple people on the mailing list that mentioned that what you are doing is the less secure method as opposed to doing the port forwarding.

I am not ignoring them, unable to comply at this time.  An I have tried to tell everyone that.  Further more I totally disagree with your traffic forwarding comment in the contex as the suggestions are being provided.  Its one thing to forward traffic to a dedicated media network where the router doesn't allow cross traffic communication.  But to forward traffic from the parents network to the MythTV server on the kids network (or vise versa) is a security risk.  Which is why it will not be done on my network.  An as I have said before, once I have the new hardware to spin up a dedicated Media network, both the kids an parent networks will be able to communicate with the MythTV server in a secure manor.

One of the users on the thread gave me the best answer.  The one I posted in my prior post.  With that response I would have said Thanks for helping me understand an nothing more would have come of it.  An if that would have just came out first instead of everyone fighting with me as to how I have MY (note mine, not yours) network setup, we could have been far more productive.  An they wouldn't have had to deal with my top posting which everyone got all bent out of shape over.

In the end, since MythTV does not support listening on multiple networks, an one is willing to tell me if its possible to compile it to do so, I went with my only option.  I completed the plex setup.  Now both networks can talk to the MythTV/Plex server.  I do believe this is more secure, for reasons that is not relevant for this thread.  Maybe we should setup a network an services security debate thread an see how many people have different views on this.  Would be kind of interesting to hear all the different thoughts on this topic.

---

