---
title: "create static route to a second router?"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-12-09
I have looked and can find no help using searches.

I have two wireless routers
One made by Gateway, other by Netgear

Gateway wan connects to cable modem.
Netgear wan connects to Gateway lan port.

Gateway router is 192.168.1.1 255.255.255.0
Handing out IP starting at 192.168.1.100

Netgear is getting an IP from Gateway and is 192.168.1.105

Netgear LAN ip is 10.0.0.1 and handing out IP from there to a computer which is 10.0.0.2

How can I make the Gateway router ping the Netgear router and make it so I can share files between my computers hooked to these two different routers?

The netgear router can ping and I can get files from the computers attached to the gateway router.

The Gateway router can not connect to the Netgear router.

So is this a static route issue to setup in the Gateway router? I tried various numbers in that but get no where with it.

here it shows the current Gateway routing table.

---

### Post by SeijiSensei on 2012-12-09
Set one of the routers to use a different subnet, say 192.168.2.0/24.

Check /etc/sysctl.conf and make sure ipv4.net.ip_forward is set to one.

---

### Post by EmmEight on 2012-12-09
Why would you use two different subnets?

Can we just put  everything on the same? 192.168.1.X?

For example:

The gateway would handle 0-99 and the netgear would handle 100-199

192.168.1.0-99 Gateway
192.168.1.100-199 Netgear

Static IPs:
192.168.1.1 --- Gateway
192.168.1.100 ---- Netgear


Then do **_*NOT*_** plug anything into the input/lan port on the Netgear.

The netgear and gateway should communicate via one of the "device" ports (typically 1-4) 

I usually do it like this:

port 4 (or the last port) on the main connects to port 4 (or the last) on the secondary 

I know this seems wrong, but trust me, it works.

Then you should have 2 different SSID's, and 1 wired network. File sharing should be simple in this case, as any device you connect with an Ethernet cable to either router will fall under the subnet 192.168.1.X

This will eliminate all static routing issues.

Once again, do we need a different subnet for some reason I am not understanding?:P

---

### Post by sdowney717 on 2012-12-09
I dont see why I should have to change any config on a PC plugged into the router. the router should be able to do this.

Example given here
[http://documentation.netgear.com/wgr614v7/enu/202-10178-01/WGR614v6-07-19.html](http://documentation.netgear.com/wgr614v7/enu/202-10178-01/WGR614v6-07-19.html)

> You must configure static routes only for unusual cases such as multiple routers or multiple IP subnets located on your network.

However, when I try this plugging in a static route into the Gateway router, the ip of the Netgear router jumps to another IP address.

---

### Post by sdowney717 on 2012-12-09
> Once again, do we need a different subnet for some reason I am not understanding?

No not really, but it should be possible to just set a static route to any subnet as the netgear site says.
And I am trying to learn something new.

```
This router's address on your LAN is 192.168.1.100.
Your company's network is 134.177.0.0.
```

Example shows a radically different set of IP's

---

### Post by sdowney717 on 2012-12-09
Is this the correct numbers to put in those boxes??
It gives met an error

---

### Post by SeijiSensei on 2012-12-09
When a packet arrives for a host, the router must determine what the default gateway is for that host's subnet.  If you have two routers serving the same subnet, how is the router supposed to know where to send the packet?

If you must put everything into 192.168.1, then you need to subnet that into at least two /25's, with the lower subnet covering 1-127 and the upper subnet covering 129-254.  You can use the netmask 255.255.255.128 to create that division.  However it's just a lot easier to use separate "class-C" subnets like 192.168.1.0/24 and 192.168.2.0/24.

---

### Post by ahallubuntu on 2012-12-09
Forget "static route."  Look at what EmmEight said.  Your goal is to be able to share files between the two routers, right?  So put everything on one subnet.

To clarify what EmmEight said (I think we are saying the same thing): turn the Netgear into an access point.  Disable DHCP on the Netgear and set its LAN IP to be something like 192.169.1.250, out of the DHCP range of the Gateway.

It can be tricky trying to do both of those at the same time, depending on how your Netgear handles changes to router settings.  If you disable DHCP first, then you will lose your local IP while setting it up.  So you might have to set a static IP briefly on the computer you are configuring it with.  Say 10.0.0.2 .  Then change the Gateway from 10.0.0.1 to 192.168.1.250, apply settings, then remove your static IP.

Then, put a piece of tape over the "WAN/Internet" port of the Netgear so you never use that port.  And connect the ethernet cable from one of the Gateway LAN ports to one of the Netgear LAN ports.  Now, the Netgear is an access point - a wireless switch, basically.  The Gateway is in charge and doing DHCP for everyone.  All computers connected to either router will be on the same network and can share files etc.  To configure the Netgear from now on, use 192.168.1.250 not 10.0.0.1 .

---

### Post by EmmEight on 2012-12-09
Thanks Ahallubuntu!

Just so we are clear the underlined is a subnet:

_10.0.0_.X

Typically devices (computers, printers, etc) can communicate EASIER if they are on the same subnet.

The numbers you chose are arbitrary, and can be changed at your will :P

192.168.1.X Is common for home use,
10.0.0.X is common for business/home use

But once again, feel free to change them.

I agree with ahallubuntu, putting a peice of tape over the typical "input/lan" (sometimes yellow) plug on your secondary router (netgear) is good practice. It seems counterproductive to not plug anything into it, but to use your secondary  (netgear) router as an access point/switch seems to be the goal here.

If I where you:

Pick ***_ONE_*** subnet to use (you can pick whatever you like :P) 
Assign a STATIC IP to both the gateway and the netgear.
192.168.1.254 Gateway
192.168.1.255 Netgear
Disable DHCP on the netgear
Start a spreadsheet with all the devices you plan to connect to your home network
Be sure to include computer names and description

[I][B][U]To connect the two routers:

Netgear

[/U][/B][/I]Use an ***_OUTPUT_*** plug (or device or whatever)

[I][U][B]Gateway

[/B][/U][/I]Use an ***_OUTPUT_*** plug (or device or whatever)

---

### Post by ahallubuntu on 2012-12-09
I would leave the Gateway alone and not change anything on it.

I'd change only the Netgear.

And typically, the port on the back I'm talking about putting tape over (and not using) is called the "WAN" or "Internet" port.  It's the port you NORMALLY use to connect a router up to another network or to an internet source.  The ports labeled "LAN" on the Netgear (typically there are four, numbered 1-4) are used as normal, but use one of them (pick one, doesn't matter) to connect up to one of the Gateway's LAN ports.

Don't use an IP of 192.168.1.255 on your local network; that IP is often used as a "broadcast" address on the network.

---

### Post by sdowney717 on 2012-12-09
If I set the Netgear router to assign from 192.168.1.175 and up, then, ok, I can get it working that way, but I dont want to get it working that way.

If I want to work it out can no one help with the static routing?

It should be possible to do the static route idea. I also saw both my Gateway and Netgear support RIP which means routers can communicate some extra info to help them connect. I turn that on and makes no difference.

---

### Post by steeldriver on 2012-12-09
the config you need is explained pretty well here - with a picture

[http://kb.netgear.com/app/answers/detail/a_id/965/~/using-wpn824,-wgr614,-or-wgt624-routers-as-an-access-point](http://kb.netgear.com/app/answers/detail/a_id/965/~/using-wpn824,-wgr614,-or-wgt624-routers-as-an-access-point)

---

### Post by sdowney717 on 2012-12-09
in the past I set the netgear router to turn off DHCP and let the gateway assign.

But I was always confused about some things.
I could never get into the Netgear router afterwards so had to do factory resets.

I had no idea which router was connecting the wireless laptop and what do you set the netgear router's wpa security password too? Match the Gateway router? something else? Can the Gateway router handle wireless DHCP thru the netgear?

I seem to remember issues with connecting. I could not get into Netgear admin again, So I turned on DHCP again.

That is one reason I want to learn the static routes.

Also what does the netmask assignment do, like a poster said splitting up the network? What do these octet numbers netmask mean?

---

### Post by EmmEight on 2012-12-09
Thanks ahallubuntu!

Good tip on leaving the Gateway alone, and I didn't realize .255 was a broadcast address. 

Either way, let us know if this is working or if you need more clarification.

):P

---

### Post by sdowney717 on 2012-12-09
[http://wiki.mikrotik.com/wiki/Manual:Simple_Static_Routing](http://wiki.mikrotik.com/wiki/Manual:Simple_Static_Routing)

see it can be done.
I just dont know how.

Apparently it is very very complicated and difficult.

[IMG]http://wiki.mikrotik.com/images/7/70/SR1.png[/IMG]

---

### Post by EmmEight on 2012-12-09
sdowney717:

If the device you are using is 10.1.1.1

And the router you are trying to connect to is 10.1.2.1

You will ***_NOT_*** be able to bring up the web client without being on the same subnet.

Correct me if I am wrong on this.

In other words, 192.168.1.X shoudln't be able to pull up the web client for 10.0.0.X

I am sure there is a workaround, But I don't know it.

It was my understanding that the octects in the subnet mask are used for forming an IP address. 

Can someone else explain this better?

---

### Post by sdowney717 on 2012-12-09
Here is another discussion about this involving 5 routers, very complex answers and ultimately no solution

[http://www.techrepublic.com/forum/discussions/46-137319](http://www.techrepublic.com/forum/discussions/46-137319)

I know it can be done, but I likely wont figure it out soon. Maybe needs a network administrator with a doctorate.

---

### Post by ahallubuntu on 2012-12-09
> **sdowney717 said:**
> in the past I set the netgear router to turn off DHCP and let the gateway assign.

But I was always confused about some things.
I could never get into the Netgear router afterwards so had to do factory resets.

That's probably because you didn't change the Netgear's LAN IP address to be on the new subnet (e.g. 192.168.1.250) like I suggested.  It was probably still set to 10.0.0.1 but if you were on the 192.168.1 subnet, you would not be able to get to 10.0.0.1 anymore from there.  You could get to 192.168.1.250 though because it would be on the same subnet.

---

### Post by sdowney717 on 2012-12-09
Well, just tried to change the Netgear router and it wont let me

Gateway router hands out adresses from 192.168.1.100 - 150

So I set Netgear to start at 151 and gives error? They are not in the same range.

---

### Post by sdowney717 on 2012-12-09
here is the wan side assignment coming in from Gateway router.

---

### Post by sdowney717 on 2012-12-09
Well, it's hosed itself, had to do a factory reset.

researching the error said to disconnect wan wire, change settings, then reconnect on lan side.

But I was left with nothing again. 
[http://forum1.netgear.com/showthread.php?t=28425](http://forum1.netgear.com/showthread.php?t=28425)

I am back online with it at the factory reset of 10.0.0.1
I really wanted to easily backup copy some 50gb worth of pictures across the LAN.
But will just have to do it using chrome remote desktop and some cloud service.

Funny how you have to go across the internet to work on the intranet.:(

here it is using chrome remote desktop from my ubuntu PC

---

### Post by ahallubuntu on 2012-12-09
Sorry, I don't know how to do with with the static route approach.  Maybe you can do it that way, although I'm not sure how/why it's better than what I suggested.  I've been using the "access point" approach for years with a second router and find it works well for me.

---

### Post by sdowney717 on 2012-12-09
When I tried it I had DHCP on.
Although I thought that would be ok as long as the assigned IP range did not overlap.
Maybe I will try again later sometime with DHCP off.

---

### Post by EmmEight on 2012-12-09
Thumbs up to ahallubuntu...

Why try to reinvent the wheel?

I have been using 4+ routers/switches in my smart home for years, and never once have I had any static routing issues.

I understand that you want to learn how for the sake of learning, But can we not swallow our pride and just do it a more traditional way?

I mean, if it's not broken don't fix it right?

I might be missing something?

---

### Post by ahallubuntu on 2012-12-09
> **sdowney717 said:**
> When I tried it I had DHCP on.
Although I thought that would be ok as long as the assigned IP range did not overlap.
Maybe I will try again later sometime with DHCP off.

Again, if you don't change the IP of your Netgear router from 10.0.0.1, you won't be able to access it if you move to a subnet of 192.168.1.X

Yes, you could have both routers doing DHCP if you want, as long as you make sure the ranges do not overlap, but why bother?  Why not let one router do everything?  It seems easier to administer to me.  All I have to worry about is the one-time switch of the (Netgear in your case) to a new IP, like 192.168.1.250, and disabling DHCP.  As I said, the trick there is that you might have to do a quick temporary static IP on your computer to do those two steps one at a time (disable DHCP...then change the IP of the Netgear).  I run DD-WRT firmware which lets me change multiple settings one at a time then Apply them all at once, but many routers apply settings immediately after you change one.

---

### Post by sdowney717 on 2012-12-09
> Again, if you don't change the IP of your Netgear router from 10.0.0.1, you won't be able to access it if you move to a subnet of 192.168.1.X

Yes, you could have both routers doing DHCP if you want, as long as you make sure the ranges do not overlap,

I had changed it to 192.168.1.151 and told it start assigning from 192.168.1.152 but I got that error.
look at what I had typed into the fields.

first pic shows netgear, second shows gateway assignment ranges

---

### Post by EmmEight on 2012-12-09
Do ***_NOT_*** use the netgear to assign IP address.

That is the gateways job.

You set the IP address correctly,

leave the other field blank

DISABLE DHCP ON THE NETGEAR;)

---

### Post by sdowney717 on 2012-12-09
here is another article on static routes between 4 different subnet with 4 routers.
[http://think-like-a-computer.com/2011/08/24/ip-routing/](http://think-like-a-computer.com/2011/08/24/ip-routing/)

[IMG]http://thinklikeacomputer.files.wordpress.com/2011/06/routing.jpg?w=630[/IMG]

Do you thing that If I changed netgear from 10.0.0.1 to something like 
192.168.111.x ranges, then static routing would work for me?

Also later down in the article they talk of dynamic routing using RIP, which both routers have. The router is supposed to be able to do this automatically. I notice I can activate RIP in the Gateway when switching from 'gateway' to 'router' operation mode. But then I loose connectivity with the other router.

---

### Post by EmmEight on 2012-12-09
Sure try it,

You will need to have the first two of the 4 octects the same no matter what.

Right world?

I am still confused why we are so set on using static routing?

I mean its a home right? Not a hospital/college campus?

Seems like we could do things a lot simpler and leave static routing out of the equation.

But if you want the headache go for it!:guitar:

---

### Post by sdowney717 on 2012-12-09
> **EmmEight said:**
> Sure try it,

You will need to have the first two of the 4 octects the same no matter what.

Right world?

I am still confused why we are so set on using static routing?

I mean its a home right? Not a hospital/college campus?

Seems like we could do things a lot simpler and leave static routing out of the equation.

But if you want the headache go for it!:guitar:

I dont know, maybe cause nothing works so why does it matter?
I set the router to 192.168.111.1 and it is working as before when on 10.0.0.1
I then added a static route to the gateway, but still getting no ping to that router.

Hey why cant i even ping the assignment of the netgear at 192.168.1.100? Is that a feature or a bug?:p

Does a wgt624ver3 not allow itself to be pinged?

---

### Post by sdowney717 on 2012-12-09
Everytime I set a static route in the Gateway to the Netgear, the DHCP of the Gateway gives the Netgear a different IP address.

If you create a static route, do you have to have the IP assigned by the Gateway to the Netgear as static, meaning dont let the Gateway use DHCP to assign an IP to the Netgear????? 

Or in otherwords, in the Netgear setup assign a static IP in the range that the Gateway uses????

---

### Post by EmmEight on 2012-12-09
> 
I dont know, maybe cause nothing works so why does it matter?
I set the router to 192.168.111.1 and it is working as before when on 10.0.0.1
I then added a static route to the gateway, but still getting no ping to that router.

Hey why cant i even ping the assignment of the netgear at 192.168.1.100? Is that a feature or a bug?:razz:[INDENT]I dont know, maybe cause nothing works so why does it matter?
I set the router to 192.168.111.1 and it is working as before when on 10.0.0.1
I then added a static route to the gateway, but still getting no ping to that router.

Hey why cant i even ping the assignment of the netgear at 192.168.1.100? Is that a feature or a bug?:razz:

Does a wgt624ver3 not allow itself to be pinged?****[/INDENT]

Does a wgt624ver3 not allow itself to be pinged? 	



Well obviously it does work, hence why myself and many other users have been using multiple routers/switches/hubs for years.. Ironically I actually have the _***same ***_setup at home. I am using it now to type this.

Please answer the following:

1. What exactly is the long term goal or *"The Big Picture"* .

2. Do we need to use static routing to succeed at [I]"The Big Picture"

3. [/I]Would you be emotionally alright if we did it another way? 

4. We can do a step-by-step if you need (Drag the little mouse to the little house) But we need more information.

Can you give us a more detailed understanding of your set up/long term goal?):P

---

### Post by sdowney717 on 2012-12-09
I just tried putting Netgear on static and created a route but still not working.

---

### Post by EmmEight on 2012-12-09
Thanks for the quick response!

But, it would be nice if you could answer our questions. 

I am wondering if you even read the threads or if you just use it for sloppy note taking:lolflag: 

As always, happy to help, even happier to give step by step instructions; 

Kind of hard to tell you where to drag the little mouse, if we don't know where the little house is ):P

---

### Post by sdowney717 on 2012-12-09
> **EmmEight said:**
> Thanks for the quick response!

But, it would be nice if you could answer our questions. 

I am wondering if you even read the threads or if you just use it for sloppy note taking:lolflag: 

As always, happy to help, even happier to give step by step instructions; 

Kind of hard to tell you where to drag the little mouse, if we don't know where the little house is ):P

HaHa, yes both!
I can likely turn off DHCP and make it work. but that is not my original intent of the static route. I posted some links to see if anyone could help figure it out. the links show it can be done, make the router do some routing. It is apparently very mysterious.

---

### Post by EmmEight on 2012-12-09
Good Luck with "Static Routing"

Does anyone else have any input?

Anything at all?

Don't bother asking questions, obviously they wont be answered.

This has been at the top of the forums for the better half of the day. 

Anyone else?

Bueller?

):P

---

### Post by sdowney717 on 2012-12-09
This describes step by step what happens when the PC does not know where to send the packet. It defaults to the 0.0.0.0 entry

Then it looks at the gateway for that entry which will be the router and the PC passes the packet onto the router.

The router then looks up in its routing table what to do with the packet, if it finds an entry it passes it on.

[http://think-like-a-computer.com/2011/08/24/the-routing-table/](http://think-like-a-computer.com/2011/08/24/the-routing-table/)

> From everything learned so far we can now trace the exact steps taken when one computer communicates with another on a different subnet. Now our router is aware of two subnets and it knows that it is directly attached to both of them via it’s respective interfaces. This is what happens when our PC  with IP 192.168.111.55 communicates with a PC on the other subnet (192.168.1.9):
Using the same methods above the PC looks at the destination IP address of 192.168.1.9 and looks at it’s routing table to find a match.
As the PC doesn’t know of the 192.168.1.x network the closest match it finds is the 0.0.0.0 match (that means ANYWHERE). This entry already explained above is the default gateway and it’s scope covers every IP range. In this entry it finds the gateway of 192.168.111.254. The PC now knows that to get to the 192.168.1.x network it must forward the packets onto 192.168.111.254 and does so.
The router receives these packets on interface 192.168.111.254 and examines it’s own routing table. It finds a match for this network (192.168.1.0) which states it is directly attached to (on-link) through the interface assigned with IP 192.168.1.254. The router sends the packet out through this interface and on it’s way. As the packet is now on the destination network it goes directly to the machine and the job of the router is done.
The exact same thing happens when 192.168.1.9 sends a packet back to 192.168.111.55. The PC looks at it’s local routing table and the closest match it finds is the 0.0.0.0 network with interface 192.168.1.254 (due to it’s own default gateway being set to this).
The PC sends the packets to the router with IP 192.168.1.254. The router checks it’s routing table and finds a match for the 192.168.111.0 network out the 192.168.111.254 inteface and sends it on its way directly to 192.168.111.55.


Here is my PC routing table

```
scott@scott-P5QC:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
scott@scott-P5QC:~$ 

```

So when I ping 192.168.111.2, it has no idea what to do with it, so it just passes the decision to gateway router 192.168.1.1

Gateway router looks up in it's table and says oh, packet 192.168.111.x goes to ???

Maybe I need an static entry in the Netgear router also???

---

### Post by sdowney717 on 2012-12-10
Just some more info on linking different subnets.

[http://www.dd-wrt.com/phpBB2/viewtopic.php?t=57727&sid=54f98c83b24a2fac5687234842db9b53](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=57727&sid=54f98c83b24a2fac5687234842db9b53)

[http://www.dd-wrt.com/wiki/index.php/Linking_Subnets_with_Static_Routes](http://www.dd-wrt.com/wiki/index.php/Linking_Subnets_with_Static_Routes)

I tried another Netgear router but not working. In fact I searched the netgear forum and several posters said static routes dont work with netgear so who knows.

I will try using the Gateway and a Verizon router, yank out the 2 Netgears.

---

### Post by sdowney717 on 2012-12-11
I made some progress on doing this!

I can now ping the Verizon router!

the verizon router is at 
wan side 192.168.1.100
lan side 192.168.200.1

I added a static route in ubuntu like this

> scott@scott-P5QC:~$ sudo route add -net 192.168.200.0 netmask 255.255.255.0 gw 192.168.1.100 dev eth0


The connected PC on the Verizon router is at 192.168.200.30 and does not respond to a ping.
However the router does! 
How can I make the win7 connected PC respond to a ping?

```

scott@scott-P5QC:~$ ping 192.168.200.1
PING 192.168.200.1 (192.168.200.1) 56(84) bytes of data.
64 bytes from 192.168.200.1: icmp_req=1 ttl=64 time=0.648 ms
64 bytes from 192.168.200.1: icmp_req=2 ttl=64 time=0.511 ms
64 bytes from 192.168.200.1: icmp_req=3 ttl=64 time=0.540 ms
64 bytes from 192.168.200.1: icmp_req=4 ttl=64 time=0.502 ms
64 bytes from 192.168.200.1: icmp_req=5 ttl=64 time=0.534 ms
^C
--- 192.168.200.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.502/0.547/0.648/0.052 ms

scott@scott-P5QC:~$ ping 192.168.200.30
PING 192.168.200.30 (192.168.200.30) 56(84) bytes of data.
^C
--- 192.168.200.30 ping statistics ---
24 packets transmitted, 0 received, 100% packet loss, time 23183ms

scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2012-12-11
I ran traceroute, so what is this telling me?

route command shows the routing, the last one is what I added but does not show gateway only a '.'?

I also remember the metric header has to do with how many routers, since I have 2, how would the route add command be adapted to input metric of 2?

```
scott@scott-P5QC:~$ sudo traceroute -I -n 192.168.200.1
traceroute to 192.168.200.1 (192.168.200.1), 30 hops max, 60 byte packets
 1  192.168.200.1  0.658 ms  0.988 ms  1.349 ms


scott@scott-P5QC:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         wr850g.hr.cox.n 0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.200.0   .               255.255.255.0   UG    0      0        0 eth0
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2012-12-11
I rebooted and still getting into 192.168.200.1

The traceroute to 192.168.200.30 shows stars, and someone had said that means a firewall??

> ```
scott@scott-P5QC:~$ sudo traceroute -I -n 192.168.200.1
[sudo] password for scott: 
traceroute to 192.168.200.1 (192.168.200.1), 30 hops max, 60 byte packets
 1  192.168.1.1  1.223 ms  1.692 ms  2.178 ms
 2  192.168.200.1  3.288 ms  3.698 ms  4.031 ms
scott@scott-P5QC:~$ sudo traceroute -I -n 192.168.200.30
traceroute to 192.168.200.30 (192.168.200.30), 30 hops max, 60 byte packets
 1  192.168.1.1  1.179 ms  1.639 ms  2.114 ms
 2  192.168.1.100  3.191 ms  3.537 ms  3.805 ms
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *^Cscott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2012-12-11
When not editing the router table in Ubuntu, 
I still connect and it shows differently with a redirect.
So maybe this here means the static route in the Gateway router is actually working?

```
scott@scott-P5QC:~$ ping 192.168.200.1
PING 192.168.200.1 (192.168.200.1) 56(84) bytes of data.
64 bytes from 192.168.200.1: icmp_req=1 ttl=64 time=1.35 ms
From 192.168.1.1: icmp_seq=2 Redirect Host(New nexthop: 192.168.1.100)
64 bytes from 192.168.200.1: icmp_req=2 ttl=64 time=1.25 ms
From 192.168.1.1: icmp_seq=3 Redirect Host(New nexthop: 192.168.1.100)
64 bytes from 192.168.200.1: icmp_req=3 ttl=64 time=1.25 ms
From 192.168.1.1: icmp_seq=4 Redirect Host(New nexthop: 192.168.1.100)
64 bytes from 192.168.200.1: icmp_req=4 ttl=64 time=1.28 ms
From 192.168.1.1: icmp_seq=5 Redirect Host(New nexthop: 192.168.1.100)
64 bytes from 192.168.200.1: icmp_req=5 ttl=64 time=1.28 ms
From 192.168.1.1: icmp_seq=6 Redirect Host(New nexthop: 192.168.1.100)
64 bytes from 192.168.200.1: icmp_req=6 ttl=64 time=1.24 ms
64 bytes from 192.168.200.1: icmp_req=7 ttl=64 time=0.898 ms
^C
--- 192.168.200.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6005ms
rtt min/avg/max/mdev = 0.898/1.224/1.355/0.137 ms
scott@scott-P5QC:~$ 

```

Then when adding the route into the Ubuntu router table, the speed increases and no redirect shows
The 'metric' should be the number of routers I think. So for me is 2

```
scott@scott-P5QC:~$ sudo route add -net 192.168.200.0 netmask 255.255.255.0 gw 192.168.1.103 metric 2 dev eth0
[sudo] password for scott: 
scott@scott-P5QC:~$ ping 192.168.200.1
PING 192.168.200.1 (192.168.200.1) 56(84) bytes of data.
64 bytes from 192.168.200.1: icmp_req=1 ttl=64 time=0.772 ms
64 bytes from 192.168.200.1: icmp_req=2 ttl=64 time=0.533 ms
64 bytes from 192.168.200.1: icmp_req=3 ttl=64 time=0.521 ms
64 bytes from 192.168.200.1: icmp_req=4 ttl=64 time=0.523 ms
64 bytes from 192.168.200.1: icmp_req=5 ttl=64 time=0.545 ms
^C
--- 192.168.200.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.521/0.578/0.772/0.101 ms
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2012-12-11
pretty sure it is pinging that verizon router as I unplugged the ethernet cable and then it cant ping it so it is getting there.

Now what is going on with the windows 7 PC at 192.168.200.30 to prevent a ping? or a connection. I went thru and made sure services were on and I turned off the firewall.

What I could try is a pingable device plugged into that router to see if it can ping it, what can I use, would the netgear router respond to a ping?

---

### Post by sdowney717 on 2012-12-11
Ok, I turned on logging to show inbound allowed and not allowed packets in the Verizon router.

The ping from my Ubuntu PC at 192.168.1.103 shows up in the log to the verizon router at 192.168.200.1

But when I ping the windows7 PC, the log shows nothing. This must mean that the ping is not coming in at all. And that must mean the Gateway router is dropping the packets. So it is not the win7 pc not responding to a ping.

---

### Post by sdowney717 on 2012-12-11
I added another static route in the Gateway router 
as 
192.168.200.30   255.255.255.255   192.168.100

reboot Gateway router, by the way if you dont reboot, it wont use your created static routes!

Now it is allowing the transfer to 192.168.200.30 good
And
Not allowing the transfer to 192.168.200.33 good as no rule exists for it.
couple pics of router logs to show this.

So maybe the windows7 PC is not responding to pings.

---

### Post by sdowney717 on 2012-12-11
I think I will someday get this working.
Inside the verizon router is a diagnostic ping test
It cant ping the win7 PC, so the *win7 PC is blocking pings*

It CAN ping the attached Netgear router

---

### Post by sdowney717 on 2012-12-11
IT IS RESPONDING TO PINGS!

I set win7 to home networking
I turned FIREWALL OFF
then it pinged

```
scott@scott-P5QC:~$ ping 192.168.200.30
PING 192.168.200.30 (192.168.200.30) 56(84) bytes of data.
64 bytes from 192.168.200.30: icmp_req=1 ttl=127 time=17.4 ms
64 bytes from 192.168.200.30: icmp_req=2 ttl=127 time=22.2 ms
64 bytes from 192.168.200.30: icmp_req=3 ttl=127 time=21.1 ms
64 bytes from 192.168.200.30: icmp_req=4 ttl=127 time=19.9 ms
^C
--- 192.168.200.30 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 17.432/20.205/22.270/1.798 ms
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2012-12-11
Almost there, I can see something about folders, but when click wants connection info.
What to do!

---

### Post by sdowney717 on 2012-12-11
some reason the windows folder shares can not mount??
When I click on c$, I get a connection screen but the password does not work.

I marked this solved as I was able to create a working static route to another router.
Internet - cable modem - first router - second router
first router assigns ip to wan of second router, that is the GATEWAY
Destination IP is what the second router assigns to an attached device on it's lan.


The key is understanding the guides terminology which is very confusing.
Their are just three parts

The destination ip, netmask, gateway

Dest ip is the lan ip of the computer or router on the other network where you want the packets to go.

like 192.168.200.0 for a group of ip or 192.168.200.30 for a single ip

Net mask
like 255.255.255.0 for a group of ip or 255.255.255.255 for a single ip

Gateway, the assigned wan ip of the router on the other network, which ***IS*** the lan ip for that router assigned by the first router. That was never made very clear to me! 
For me it is 192.168.1.100

you have to reboot the router, cant just click apply.
You may have to create more than one static route.
The router table also shows the routes on it's own routers lan 
Second picture shows my working router table.

Hopefully I dont need to do the route add to the ubuntu machine so I will reboot to see if it still works.
As it shows, I had removed those entries and it still connected to the win7 pc, so i quess not.
> ```
scott@scott-P5QC:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         wr850g.hr.cox.n 0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2012-12-11
ok, following this guide on windows 7 sharing, everything is now working!
I can access and modify the shares.
[http://www.swerdna.net.au/susesambawin7.html](http://www.swerdna.net.au/susesambawin7.html)

Also you wont see the machine in Network folder as it is on a different subnet, you need to click in Nautilus menu 'connect to server'

Then type in the ip of the server and it takes you to the shares.
I did not need a password.

I managed most of what I did on the win7 machine using google chrome remote desktop.!

Editing.
I was able to connect with windows firewall off.
However, when I turned it on I could not connect

So tried a few things like port 139 but still not working with firewall on.
[http://empegbbs.com/ubbthreads.php/topics/344175/Windows_file_and_printer_shari](http://empegbbs.com/ubbthreads.php/topics/344175/Windows_file_and_printer_shari)
[http://www.ehow.com/how_6939996_open-windows-firewall-port-139.html](http://www.ehow.com/how_6939996_open-windows-firewall-port-139.html)

Any ideas?

---

