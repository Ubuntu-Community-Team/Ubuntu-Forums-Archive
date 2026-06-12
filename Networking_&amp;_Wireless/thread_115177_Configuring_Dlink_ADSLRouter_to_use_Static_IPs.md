---
title: "Configuring Dlink ADSL/Router to use Static IPs"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by Pretzal on 2006-01-10
Help Please - I am going insane!!!

I have a Dlink G604T ADSL/router and have managed, with the help of people like Mips, to share an internet connection between my Ubuntu Desktop and XP laptop. However, for various reasons (unknown) I have not been able to share files between the 2. I am under the impression that if I can assign static IPs I might have a better chance of getting everything to work. I am presently trying to setup my router so that it uses static IPs and then in turn will assign static IPs to the Desktop (which dual boots with XP) and the laptop using XP. I have tried changing the router from a dhcp server to no dhcp and then trying to change the routers IP settings to 192.168.0.1 but it keeps freezing. What am I doing wrong. All I really want to do is get all the computers to play nice and share files. I've tried installing samba and have had no success with that:

[http://ubuntuforums.org/showthread.php?t=111740](http://ubuntuforums.org/showthread.php?t=111740)

I've searched HEAPS of different threads and tried countless How-to's - you name it I've tried it. I have spent about 20 hours trying, now I'm just getting frustrated. Can someone out there lend a hand to a very frustrated noob?

---

### Post by JimmyJazz on 2006-01-10
well basically what you need to do is find your routers IP address its almost always 192.168.0.1 but yours may be different.
Goto Network settings up on the gnome menu choose the Ethernet connection menu item, choose properties, then check the "Enable this connections" box choose static IP from the "Configurations" menu, IP address should be anything like 192.168.0.14 (the number should always start with 192.168.0. with most routers).  The subnet mask should fill itself in by itself and finally the gateway address will be your routers local IP (192.168.0.1 usally). Click 'ok' then "activate" the Ethernet connection, done.

---

### Post by Pretzal on 2006-01-10
Hi, 
thanks for the reply. My router's IP is 10.1.1.1 and the subnet mask is 255.0.0.0 When I go into the networking tab as you suggest and change to static IP and use the following entries:
IP Address: 192.168.0.2
subnet mask:255.0.0.0
gateway: 10.1.1.1
I can no longer connect to the internet and when I try and ping the router I get:
pretzal@Ubuntu:~$ ping 10.1.1.1
connect: Network is unreachable

If I change it back to dhcp everything works again.
I know my router is using DHCP to assign IPs to the other computer between 10.1.1.2 and 10.1.1.254. But as mentioned it seems to go haywire when I try an alter the IP of the router through a browser (firefox and Internet explorer - in XP even)

I have included a couple of outputs from the wired ethernet troubeshooting guide:

pretzal@Ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:09:6B:E4:33:1A
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::209:6bff:fee4:331a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1153632 (1.1 MiB)  TX bytes:259271 (253.1 KiB)

pretzal@Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0

pretzal@Ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider

auto eth0


Any more ideas?

---

### Post by harisund on 2006-01-10
First of all, it doesn't look like your network is a small one, since you have a class A IP address. So 192.168.0.1 isn't going to work (that is class C).

Does your router have a web interface? You can find out by typing is 10.1.1.1 in your browser. 

Assuming it does, turn your DHCP back on, and assign a static ip based on mac address. I hope you know what I am talking about. In other words, enable DHCP server but assign a static ip of 10.1.1.3 to the MAC id of 00:09:6B:E4:33:1A. In other words, when any machine tries to connect to the router, the router will randomly hand out a ip address (of the form 10.1.1.*) but when the machine with the MAC ID of 00:09:6B:E4:33:1A (your Ubuntu machine) tries to connect, it will always be assigned 10.1.1.3. This way your Ubuntu thinks it is getting a dynamic ip address, but the router knows it should give the same ip address to it. 

I know I just typed in a lot of mess. Do post back if I am clear enough. Once this is done (your Ubuntu always gets the same 10.1.1.3) we can fix Samba next..

---

### Post by harisund on 2006-01-10
[QUOTE=JimmyJazz](the number should always start with 192.168.0. with most routers).  The subnet mask should fill itself in by itself and finally the gateway address will be your routers local IP (192.168.0.1 usally). [/QUOTE]

As I mentioned that is only for small home based networks (Class C). Apparently the parent poster doesn't have a network like that. He has a class A address beginning with 10.1.1.* with a network mask of 255.0.0.0

192.168.0.* address have a network mask of 255.255.255.* so don't manually change stuff on your Ubuntu. Get eveything back to default.

---

### Post by mips on 2006-01-10
[QUOTE=Pretzal]Hi, 
thanks for the reply. My router's IP is 10.1.1.1 and the subnet mask is 255.0.0.0 When I go into the networking tab as you suggest and change to static IP and use the following entries:
IP Address: 192.168.0.2
subnet mask:255.0.0.0
gateway: 10.1.1.1
I can no longer connect to the internet and when I try and ping the router I get:
....
Any more ideas?[/QUOTE]

If your routers IP is 10.1.1.1 then assign 10.1.1.10 to your pc, mask 255.0.0.0

---

### Post by heftigrat on 2006-01-10
[QUOTE=Pretzal]I know my router is using DHCP to assign IPs to the other computer between 10.1.1.2 and 10.1.1.254.[/QUOTE]

If you know this for a fact, follow this logic:

- Using a 255.0.0.0 netmask for a 10.0.0.0 network you can assign anything between 10.0.0.1 - 10.255.255.254 to your PC.
- Your router is using the range 10.1.1.[2-254] for DHCP, so don't statically assign anything in that range.
It logically follows that if you assign anything within the Class A range that is not being served via DHCP, you should be able to ping your gateway (router) IP of 10.1.1.1.

(Oh, my recommendation is to try 10.1.2.1, netmask 255.0.0.0, gateway 10.1.1.1, and that should do it).

---

### Post by mips on 2006-01-10
[QUOTE=heftigrat]If you know this for a fact, follow this logic:

- Using a 255.0.0.0 netmask for a 10.0.0.0 network you can assign anything between 10.0.0.1 - 10.255.255.254 to your PC.
- Your router is using the range 10.1.1.[2-254] for DHCP, so don't statically assign anything in that range.
It logically follows that if you assign anything within the Class A range that is not being served via DHCP, you should be able to ping your gateway (router) IP of 10.1.1.1.

(Oh, my recommendation is to try 10.1.2.1, netmask 255.0.0.0, gateway 10.1.1.1, and that should do it).[/QUOTE]

It does not really matter in this case if the router assigns addresses in the 10.1.1.2-254 range. It wont assign anything if it does not receive any requests as DHCP is initiated by the hosts and not server.

The logic is good though as some people might find themselves in a mixed environment with dhcp & static. In that case it would not be so clever to assign a static address in a dynamic environment ;)

---

### Post by heftigrat on 2006-01-10
[QUOTE=mips]It does not really matter in this case if the router assigns addresses in the 10.1.1.2-254 range. It wont assign anything if it does not receive any requests as DHCP is initiated by the hosts and not server.[/QUOTE]

True, true.  Wasn't sure if that would help **Pretzal** (like the name, btw).  Glad you clarified that though, my post was slightly one-sided.  However, just out of curiosity, is it possible for a router to choose not to respond to machines with IP's in the DHCP range that it knows it didn't assign?  Well, let me rephrase, that IS possible, but do you know of any routers that actually WOULD do that in practice?  Just shootin the breeze here.  :rolleyes:

---

### Post by Pretzal on 2006-01-10
wow thanks for the replies guys - you have no idea how happy I was to see them.

There were a couple of different suggestions, so I tried them in order.

Harisund I tried your suggestion and had no problems following your instructions. Everything seemed to work ok. When I initially logged on today I had been assigned 10.1.1.2 but after I tried your suggestion of entering the Mac address and 10.1.1.3 everything functioned normally. After trying Heftigrat's suggestion and then reverting to yours my IP was 10.1.1.3 and functioning normally. Thanks I'd never heard of Class A and C networks in all the browsing that Ive done which is surprising to me. Any tips for samba now? thanks a bunch already!

Heftigrat thanks for your suggestions also. I tried the static IP of 10.1.2.1 and subnet of 255.0.0.0 and gateway 10.1.1.1 and had no problems with that also. It worked beautifully!

Mips I tried yours also and it worked no probs. I thought I had tried this only with 10.1.1.2 and it didnt seem to work - maybe I tried changing the subnet at the same time? Doesnt matter.

So no I am a little torn as to which was is the best to do it because they all work. I'm spoilt for choice! :)

---

### Post by heftigrat on 2006-01-10
[QUOTE=Pretzal]So no I am a little torn as to which was is the best to do it because they both work. I'm spoilt for choice! :)[/QUOTE]

lol, glad to hear it!  There's no end to the possibilities as long as you stay within the 10. network.  :p

You may want to check out this [IP Subnetting Tutorial]("http://www.ralphb.net/IPSubnet/index.html"), as well as the [wiki about subnets]("http://en.wikipedia.org/wiki/Subnetwork").  I haven't combed through the tutorial, so I won't make any claims that it's the end-all-be-all, but the definition at Wikipedia.org should definitely be accurate.  Have fun!  :)

---

### Post by mips on 2006-01-10
heftigrat,

Thing is a client with a static address configured by a user will not send out dhcp request as it is not configured for DHCP. A server also cannot stop a client from using any IP address if the client is statically configured which will result in IP address conflicts. In effect DHCP has no real way of denying any client an IP address. 

You can hardcode the MAC addresses into the DHCP server which boils down to manual allocation and it becomes an administrive nightmare depending on the size of your network (been there done that, never want to do it again), home network is easy.

Some DHCP servers can prevent roaming from one subnet to another, this might be usefull if you want to block certain clients but is not really a solution.

The thing that makes it so hard is that you have to keep tight control of all your MAC addresses and basically have a whitelist which means you only allow certain addresses.

Another option is to have port security enabled on your switches so only a know MAC address is allowed on a certain port, another white list method. Another possibility is router access list but I dont ever recall using access lists to control layer 2 stuff.

IBM AIX & OS/2 Warp dhcp servers will prevent clients from roaming but that does not stop new clients joining an existing network.

**So in general I would answer your question with a 'no'**. Stopping clients from obtaining IP addresses is outside the scope of DHCP and basically contradicts DHCP. If you want to stop clients using DHCP you have to find other methods of doing so.

[http://www.dhcp.org/](http://www.dhcp.org/)
[http://www.dhcp-handbook.com/dhcp_faq.html](http://www.dhcp-handbook.com/dhcp_faq.html)
[http://www.quepublishing.com/content...s/A010802.html](http://www.quepublishing.com/content...s/A010802.html)
[http://www.rhyshaden.com/dhcp.htm](http://www.rhyshaden.com/dhcp.htm)

---

### Post by heftigrat on 2006-01-10
[QUOTE=mips]Thing is a client with a static address configured by a user will not send out dhcp request as it is not configured for DHCP.
...
**So in general I would answer your question with a 'no'**. Stopping clients from obtaining IP addresses is outside the scope of DHCP and basically contradicts DHCP.[/QUOTE]

Thanks for the info, but that wasn't my question.  I understand just a little bit about DHCP and the difference between static and dynamic.  ;) 

My question was probably most related to the MAC address whitelist you referred to, but more so to reserved DHCP IP's assiciated with MAC addresses.  What I'm saying is, if a router is smart enough to say, "OK, I will only assign this IP to a machine making a request from this MAC," shouldn't it also be smart enough to say, "Have I assigned an IP to this machine attempting to reach the Internet?" and block all packets within the DHCP range that it has not assigned IP's to?  I'm not saying it should block DHCP requests.  I am probably still mixing layers, but I wanted to try to make my original question clear.

Thanks again for the info, I'll have to comb through it all sometime.

---

### Post by JimmyJazz on 2006-01-10
oops sorry I was assuming you where using a standard home router.

---

### Post by enricodc on 2006-01-10
BTW, this has been great information for me too, lurking in the background. 

I'll be trying pretty much the same thing over the weekend (set up ADSL modem-router and Samba server). Pretzal's frustration with Samba could be mine in a few days but at least I won't have problems setting up the router.

Thanks!

---

### Post by Pretzal on 2006-01-10
oops sorry I was assuming you where using a standard home router.

No worries - I'm lookin at it and it looks like a standard home router to me!

---

### Post by Pretzal on 2006-01-10
[QUOTE=JimmyJazz]oops sorry I was assuming you where using a standard home router.[/QUOTE]

No worries - I'm lookin at it and it looks like a standard home router to me!

---

### Post by mips on 2006-01-11
[QUOTE=heftigrat]...
  What I'm saying is, if a router is smart enough to say, "OK, I will only assign this IP to a machine making a request from this MAC," shouldn't it also be smart enough to say, "Have I assigned an IP to this machine attempting to reach the Internet?" and block all packets within the DHCP range that it has not assigned IP's to?  I'm not saying it should block DHCP requests.  ...[/QUOTE]

The answer to this would be no as far as my knowledge goes..

The reason for this is as follows:
DHCP server is a seperate process that runs on a router or server and does not concern itself with the routing functions at all and vice versa. Routing and DHCP operate independantly from each other.

You wil manually have to configure access list on the router to deny traffic from certain addresses.

---

### Post by heftigrat on 2006-01-12
[QUOTE=mips]DHCP server is a seperate process that runs on a router or server and does not concern itself with the routing functions at all and vice versa. Routing and DHCP operate independantly from each other.[/QUOTE]

Of course.  The angle I'm coming from is definitely having access lists that are able to reference the DHCP client table, so the DHCP server doesn't have to do anything at all, except accurately maintain the table.  From what I know about routers this would have to be coded into the firmware to allow the user/admin the functionality to create such acl's.  I'm convinced it could be done though.  ;)

---

### Post by mips on 2006-01-12
Probably could be done. The only thing is big companies dont usually make use of the DHCP server on a router. Lets just say you have 200 routers in an area, that is 200 new administration tasks. Anyway the user interface on a server is much easier to use and you dont want to give any tom dick & harry or desktop/server support person access to your routers.

Therefore companies use servers. In the old days they used distributed DHCP servers, basically one per siteand this usually ran on the local file/mail server. These days they run one+backup central dhcp server for an entire region serving thousands of pc's. The only thing you have to do is configure ip helper addresses once off on all routers and this is easily done via a script

Hey, maybe try and sell the idea to Cisco or Juniper ;)

---

### Post by heftigrat on 2006-01-12
> **mips]Probably could be done. The only thing is big companies dont usually make use of the DHCP server on a router.[/QUOTE]
Depends on how big the company is, I s'pose.

[QUOTE=mips]Lets just say you have 200 routers in an area, that is 200 new administration tasks.[/QUOTE]
Sure, but that's no problem.  Any good admin/engineer knows they'll probably touch all 200 of those routers within a month at most just for other admin stuff.   said:**
> Anyway the user interface on a server is much easier to use and you dont want to give any tom dick & harry or desktop/server support person access to your routers.
Would be a one-liner on any robust Cisco (using my method).  I prefer the Cisco IOS command line anyhow.  :p  As for tom/dick/harry/dumbass_who's_gonna_screw_up_your_net, well...I'm Tier 1/2 tech support and have access to ... hmmm ... I think it's in the many hundreds of routers.  I only managed to screw up a dozen or so.  hehe, jk  :D

[QUOTE=mips]Therefore companies use servers. In the old days they used distributed DHCP servers, basically one per siteand this usually ran on the local file/mail server. These days they run one+backup central dhcp server for an entire region serving thousands of pc's. The only thing you have to do is configure ip helper addresses once off on all routers and this is easily done via a script[/QUOTE]
I'll have to agree with you on that one.

[QUOTE=mips]Hey, maybe try and sell the idea to Cisco or Juniper ;)[/QUOTE]
Don't I wish!  There's probably some reason they haven't done that already.  Probably has something to do with your crazy theory that DHCP should be run from a server seperate from the gw router.  :rolleyes:  Uh oh, brainstorm:  a DHCP server that could write to a shared client table on the router, now THAT might be something.  Hmmm...*calls Cisco*...nope, they hung up on me.  hehe, roffle.

---

### Post by mips on 2006-01-13
[QUOTE=heftigrat]
What kind of company are you talking about anyhow?  If you're talkin ISP, or even just a corporation with many remote sites running VPN, each location _should_ have its own capable admin - well, only in a perfect world.  You and I know that never happens.  ha!
[/QUOTE]

One admin per site ? I wish ! More like a Telco's own internal networks, excluding the ISP part. Try about 1000 routers & switches in one province. Excludes hundreds of wireless AP's, UPS snmp  management modules, fiber/utp cabling. Plus then you have to do design work & install the stuff and on top of this provide consultation/support on the odd external clients network.

How many people ? 3 !

---

### Post by heftigrat on 2006-01-13
[QUOTE=mips]One admin per site ? I wish ! More like a Telco's own internal networks, excluding the ISP part. Try about 1000 routers & switches in one province. Excludes hundreds of wireless AP's, UPS snmp  management modules, fiber/utp cabling. Plus then you have to do design work & install the stuff and on top of this provide consultation/support on the odd external clients network.

How many people ? 3 ![/QUOTE]
Like I said, in a perfect world.  ;)

---

