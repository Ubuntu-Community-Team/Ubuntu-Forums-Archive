---
title: "trying to figure out why I can and can't connect to network"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2009-09-18
Ok.. I am going to try to explain this the best I can. I have a Netopia router connected to the DSL line. Connected to that I have a D-Link router and an SMC router. Both of these are configured to be on the same 192.168.1.xx network and they both have their DHCP servers disabled. All three routers have their wireless access enabled and are protected with 128-bit WEP. 

On this network, I have a dedicated web server hard connected to the Netopia router. Hard connected to the D-Link router is a work computer and my girfriend's computer. Connected to the SMC router is an HTPC through a hard connection as well as both my girlfriend's laptop and mine through WiFi. Through WiFi connected to the Netopia is a Spykee robot. Finally, through WiFi connected to the D-Link is a OpenWRT modified LinkSys router to which a ProLite LED sign is connected (constantly downloading and displaying the current weather conditions and forecast). 

I don't think this is the problem, but on both computers connected to the D-Link and the HTPC I am running WinXP. On my girlfriend's laptop is Win98 and on my laptop is Ubuntu Linux 9.04. 

Phew... Now the OpenWRT LinkSys has a static IP programmed into it as does the Spykee robot. From my work computer, I am able to connect to either the OpenWRT router or the Spykee with no problem. I can ping the OpenWrt router from my girlfriends laptop just fine. My laptop, however, can no longer even ping the OpenWRT or the Spykee. Notice "no longer". I was doing that just fine. And I can still access the internet (obviously) and communicate with all three routers with no problems.

I cannot for the life of me figure out what I did to change that. I have a suspicion and I would like to see if this could be the problem. 

I need my laptop to maintain it's IP address, due to port mapping I had to do for certain programs to run. I figured that a static IP might pose a problem, though, if and when I try to connect to other WiFi hotspots. So what I did instead was to go into the Netopia router and, under IP Static ARP, create an entry mapping that IP address to my laptop's MAC hardware address. That way, no matter what happens, that IP can only be assigned to my laptop. 

That is the only thing that I can thong of that I have changed. Is it possible that that would prevent me from seeing just those two IP addresses on this network, even though I can communicate with everything else just fine? If yes, what can I do to make sure that I always have the same IP at home, while retaining the ability to connect to public WiFi hotspots. If no, what on Earth can be causing this?

I have run out of ideas. Any you might have would be great...

---

### Post by t0mppa on 2009-09-18
Sounds a little weird indeed that setting a static ARP would kill connection to other AP's.

However, as for your problem with the static vs. dynamic addresses, if you're using any of the GUI's to connect to a network, they keep local settings for each network (unlike on Windows, where there's only a global way to determine whether to use dynamic or static IP), so even if you specify a static IP for your home AP, you can still keep all the other AP's you find on DHCP without any problems whatsoever.

If you're manually connecting, then things get a bit more complex, but even then you could simply make a script that swaps between static/DHCP and remembers the static settings for your home AP.

Thus there shouldn't be any need to force a specific IP to your wireless interface through your AP.

---

### Post by rebeltaz on 2009-09-19
I found the static IP setting and see what you mean about different settings for each connection. Every day I see more and more why I prefer Linux over anything Micro$oft. 

After setting the IP there, I removed the static ARP on my router. That didn't have any effect. I still get the "no route to host" error when I try to connect to the OpenWrt. 

Any thing else?

---

### Post by t0mppa on 2009-09-19
Well, I just read through the part describing your network topology. So, you have 4 routers in the same subnet? That sounds a little excessive compared to the number of devices connected, plus the general usage is one subnet per router.

Anyway, so you can access your server, but not the robot, which are both behind router A and then you can't access anything behind router D at all? If they all are on the same subnet, I don't see why the routing would fail to those two specifically. But if I misunderstood something along the way and both of those are on different subnets, then you'd have to add additional gateways to your routing table.

---

### Post by rebeltaz on 2009-09-20
> **t0mppa said:**
> Well, I just read through the part describing your network topology. So, you have 4 routers in the same subnet? That sounds a little excessive compared to the number of devices connected, plus the general usage is one subnet per router.

Anyway, so you can access your server, but not the robot, which are both behind router A and then you can't access anything behind router D at all? If they all are on the same subnet, I don't see why the routing would fail to those two specifically. But if I misunderstood something along the way and both of those are on different subnets, then you'd have to add additional gateways to your routing table.

First let me make sure I understand something. By 'subnet' you mean the first three segments of the IP address - i.e. 192.168.1.xxx ? If so, then yes. Everything is on the same subnet. 

As an addendum: I tried connecting and pinging the OpenWRT through my PocketPC today. I was unsuccessful using that as well whereas I never used to have problems. Oddly enough, though, I was able to ping the robot with the PPC. I had thought maybe an Ubuntu update may have caused the problem, but since the PPC can't connect either, I doubt that is the problem. Also, I have tried connecting wirelessly to the main DSL router (bypassing all of the other routers) with the same results.

As for the reasoning behind number of routers is this: The first router is acting as a DSL gateway and an access point to the web server. My girlfriend's computer and my work computer are about 120 feet way on the other side of the building. Rather than run three Cat-5 cables (the third is for connecting to computers when I am working on them), I ran one cable and use the second router as a switch. The third router is about 150 feet away from the first in my home. (My business and my home are separate buildings on the same one acre lot.) This router is to provide WiFi access to our laptops (the signal from the other two is too weak otherwise) as well as a connection to the HTPC. The fourth router isn't really a router. Since installing OpenWRT, I am using it as a small Linux computer to control the LED sign. I know it sounds excessive, but it was the only way I knew to get the job done effectively.

---

### Post by t0mppa on 2009-09-20
> **rebeltaz said:**
> First let me make sure I understand something. By 'subnet' you mean the first three segments of the IP address - i.e. 192.168.1.xxx ? If so, then yes. Everything is on the same subnet.

To thoroughly understand subnets, you need to know how binary numbers work, which is a bit of a long story to add in here ([Wikipedia]("http://en.wikipedia.org/wiki/Subnetwork") for instance has a broader explanation). Bottom line being, the numbers used on IPv4 addresses are confusing, because the logic tied to IP addresses does not work on a 10-base number system such as humans generally use.

So, 192.168.1.xxx (or 192.168.1.0/24) is a 24 bit subnet, meaning the first 24 out of the total 32 bits (each 8 bits matches to 256 possibilities displayed by the x.x.x.x notation) are always the same and the last 8 bits change. But a subnet could be bigger or smaller as well. Say from 192.168.1.152 to 192.168.1.159 (192.168.1.152/29), giving you 6 spots for hosts (the first one is used as a network address and the last one as a broadcast address by default).

The point of putting a different subnet behind each router is simply to make sure that a) multiple routers don't assign the same address to different devices (if you use static addresses you're are in charge of this yourself) and b) there's only one gateway and thus only one logical path to and from other subnets so as not to create unnecessary traffic (no need to push copies of the same packet through multiple paths, if they all end up in the same place anyway).

> **rebeltaz said:**
> As an addendum: ... I know it sounds excessive, but it was the only way I knew to get the job done effectively.

Ah yes, distance and the decorative impracticality of long wiring would explain that. And since you're using only one piece of equipment that really does routing to separate networks and the rest act as switches, it's not relevant. Just calling them all routers allows their usage to be misunderstood easily.

And since your PocketPC is experiencing same difficulties, the problem more likely would be on the OpenWRT instead, that is the only one (and the device behind it) you had problems with, right?

---

### Post by rebeltaz on 2009-09-20
Ok... I do understand binary and I thought I followed your description until you mentioned 29 bit subnets. What decided how many bits the subnet contains?

I don't know if doing this is a security risk or not, but maybe this will help: the routers are 192.168.1.254, 192.168.1.253 and 192.168.1.252. OpenWRT is 192.168.1.100. The laptop I am having trouble with 192.168.1.5 and my gf's laptop, which works, is 192.168.1.8. The x.x.1.254 is the default IP on the Netopia. The SMC's default IP was 192.168.2.0 and the D-Link's default was 192.168.0.1 - neither of which was on the same subnet. So I changed those to the new .252 and .253 IPs. Odd thing is that before doing that, the laptop could communicate with the OpenWRT. It was quite a while before I tried again after making the changes, so I can't be sure that is what did it. 

The reason I made the changes was, although the network seemed to work with the switches on different subnets(?), I could not access their control panels from any computer without having to disconnect the LAN cable to the switch from the Netopia and reboot the computer, allowing it to be assigned an IP on that switches subnet. I thought that assigning the proper IP to the switches was a good idea. Now I'm not so sure!

BTW - The OpenWrt and the robot are both having problems from my laptop. I want to point out that I can access the OpenWRT from any other computer on the network without any problems.

---

### Post by rebeltaz on 2009-09-21
I have been experimenting, so I have new details that may help in this mystery...

From my laptop, if I connect wirelessly to the main DSL router, I can still connect to the internet, but not to either the DLink switch or the OpenWRT behind it. If I connect wirelessly to the DLink, I can connect to the OpenWRT, but not the internet or any of the other routers/switches. Weird thing is that any computer hard connected to the DLink sees the net and the routers/switches just fine.

Mean anything to you?

---

### Post by t0mppa on 2009-09-21
> **rebeltaz said:**
> Ok... I do understand binary and I thought I followed your description until you mentioned 29 bit subnets. What decided how many bits the subnet contains?

Each subnet has a mask that defines its range, which essentially just has its bit number of 1's and the rest are 0 (ie. a 29 bit mask has 29 1's and 3 0's in the end), which shows what part of the address is network portion and which is host portion. 24 bits is simply used normally, since it's very easy to figure it out on the base-10 numeral system.

Say for example an IP of 192.168.1.155 in a 29 bit subnet would have (red shows the numbers made irrelevant by the mask):
```

* IP address: 192.168.1.155      (11000000.10101000.00000001.10011011)
* Subnet mask: 255.255.255.248   (11111111.11111111.11111111.11111000)
* Network Portion: 192.168.1.152 (11000000.10101000.00000001.10011[COLOR="Red"]000[/COLOR])
* Host Portion: 0.0.0.3          ([COLOR="Red"]00000000.00000000.00000000.00000[/COLOR]011)

```

So, you could read it as the 4th spot (host portion 0.0.0.0 being the first one) in the 192.168.1.152/29 subnet.

> **rebeltaz said:**
> I don't know if doing this is a security risk or not, but maybe this will help: the routers are 192.168.1.254, 192.168.1.253 and 192.168.1.252. OpenWRT is 192.168.1.100. The laptop I am having trouble with 192.168.1.5 and my gf's laptop, which works, is 192.168.1.8. The x.x.1.254 is the default IP on the Netopia. The SMC's default IP was 192.168.2.0 and the D-Link's default was 192.168.0.1 - neither of which was on the same subnet. So I changed those to the new .252 and .253 IPs. Odd thing is that before doing that, the laptop could communicate with the OpenWRT. It was quite a while before I tried again after making the changes, so I can't be sure that is what did it.

No, it's not a security risk, since those are simply the addresses used on your local network. 192.168.x.x are reserved as private addresses (ie. they're not mapped for Internet and thus can be used on any number of different locations around the globe) and are used by default on pretty much all routers of this size. The private network is invisible and inaccessible beyond your Netopia router and thus to Internet all your devices in the network seem to be just one big device with the IP your ISP assigned to your Netopia.

> **rebeltaz said:**
> The reason I made the changes was, although the network seemed to work with the switches on different subnets(?), I could not access their control panels from any computer without having to disconnect the LAN cable to the switch from the Netopia and reboot the computer, allowing it to be assigned an IP on that switches subnet. I thought that assigning the proper IP to the switches was a good idea. Now I'm not so sure!

It really should work either way, just a matter of configuring everything to do the correct thing. Since you're using static IP addresses and don't need to limit access between the computers behind different routers, having them all function as merely switches on the same network is probably the way of least effort for configuring the network.

> **rebeltaz said:**
> I have been experimenting, so I have new details that may help in this mystery...

From my laptop, if I connect wirelessly to the main DSL router, I can still connect to the internet, but not to either the DLink switch or the OpenWRT behind it. If I connect wirelessly to the DLink, I can connect to the OpenWRT, but not the internet or any of the other routers/switches. Weird thing is that any computer hard connected to the DLink sees the net and the routers/switches just fine.

Mean anything to you?

Ok, this sounds like a more consistent problem to fix. Just open up a terminal and run a **route -n** from the two problem cases above and compare the results (or post them on a reply, if you can't figure them out). Sounds like you have some problematic routing rules on the laptop that are messing things up.

---

### Post by rebeltaz on 2009-09-22
> **t0mppa said:**
> Ok, this sounds like a more consistent problem to fix. Just open up a terminal and run a **route -n** from the two problem cases above and compare the results (or post them on a reply, if you can't figure them out). Sounds like you have some problematic routing rules on the laptop that are messing things up.

Ok.. I understand the subnet deal now. You said to run the command _FROM_ the two "problem cases". I wasn't sure exactly what you meant, but I ran the command on the Ubuntu laptop with these results:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0

There is no 192.168.1.0 on my network (unless that is reserved for internal usage) and I have no idea what 169.254.0.0 is.

---

### Post by t0mppa on 2009-09-22
Oh sorry, by the two cases I meant when wirelessly connecting your laptop to the two AP's you mentioned, where the other one could get online, but not to the OpenWRT and then vice versa.

If you look at the mask, you'll see that the first line refers to 192.168.1.x addresses, and since they don't have a gateway, the rule just means they're on your local network and don't need to be routed to via any other device. The 169.254.0.0/16 is classified as a self-assigned link-local range (also not used on Internet scale) and is the product of an Avahi daemon running on the kernel by default. The last one is called a default rule, which is used when none of the others apply and it gets directed to your gateway at 192.168.1.254.

All in all, that's the default set up, so can't see anything wrong with it, since the .254 is the Netopia router that's connected to your DSL line. And I guess this would be the case for when you connect wirelessly straight to Netopia. How about the D-Link part?

Also, since you said the wired connections work perfectly, have you tried one with your laptop or does that just apply to the Windows boxes? And how does wireless work for your GF's laptop (which also has Windows)?

If there's a difference of Windows vs. Ubuntu in connectivity, then it's a matter of configuring Ubuntu properly. If the difference is wired vs. wireless though, then you need to look at the router configurations.

---

### Post by rebeltaz on 2009-09-22
> **t0mppa said:**
> 
All in all, that's the default set up, so can't see anything wrong with it, since the .254 is the Netopia router that's connected to your DSL line. And I guess this would be the case for when you connect wirelessly straight to Netopia. How about the D-Link part?

Also, since you said the wired connections work perfectly, have you tried one with your laptop or does that just apply to the Windows boxes? And how does wireless work for your GF's laptop (which also has Windows)?

If there's a difference of Windows vs. Ubuntu in connectivity, then it's a matter of configuring Ubuntu properly. If the difference is wired vs. wireless though, then you need to look at the router configurations.

I can connect just fine with my GFs laptop running windows regardless of which router I connect wirelessly to. I haven't tried connecting my laptop to any router with a wired connection, but I'll try that tomorrow. 

I did run 'route -n' on my laptop with it connected to the D-Link router (through which i can connect to the OpenWRT) and the response was identical to what I posted for the other router...

---

### Post by t0mppa on 2009-09-23
> **rebeltaz said:**
> I can connect just fine with my GFs laptop running windows regardless of which router I connect wirelessly to. I haven't tried connecting my laptop to any router with a wired connection, but I'll try that tomorrow. 

I did run 'route -n' on my laptop with it connected to the D-Link router (through which i can connect to the OpenWRT) and the response was identical to what I posted for the other router...

Ok, so it complains about route not found and yet all the routing rules are perfectly fine and things work on Windows, so it isn't a router specific issue. What about that port mapping you were talking about on your original post, did you add some firewall rules to your laptop there?

---

### Post by rebeltaz on 2009-09-23
> **t0mppa said:**
> Ok, so it complains about route not found and yet all the routing rules are perfectly fine and things work on Windows, so it isn't a router specific issue. What about that port mapping you were talking about on your original post, did you add some firewall rules to your laptop there?

No... supposedly, the firewall is completely disabled on my laptop. I did install the GUI front-end and when I run that, it shows the firewall as not enabled. And the port forwarding was done via Netopia's settings.

---

### Post by t0mppa on 2009-09-25
Well, then I'm running out of ideas what could affect the connection between D-Link & Netopia, since it works for all of your other computers.

---

### Post by JKyleOKC on 2009-09-25
When you cascaded the additional routers to act as switches, did you plug the cables from the "real" router into the WAN port on each, or into one of the LAN ports?

I haven't tried this so cannot vouch for its accuracy, but I've seen advice in other forums that when setting up a secondary router to act as a wireless access point, the cable from the primary router should go to one of the LAN ports rather than to the WAN port. The reason is to avoid double-NAT (Network Address Translation) effects, which can automatically block incoming packets that are not part of an established connection. That is, a device on one of the secondaries could not originate a connection to one on the others, but might be able to receive from it!

Rather than so many secondary routers, it might be simpler to use multi-port switches in their stead!

---

### Post by rebeltaz on 2009-09-25
> **t0mppa said:**
> Well, then I'm running out of ideas what could affect the connection between D-Link & Netopia, since it works for all of your other computers.

I know... I'll tell you, when I have problems, they're not your average everyday problems! :confused: I appreciate all of your help, though.

If and/or when I figure it out, I'll post here in case anyone else every has this problem...

> **JKyleOKC said:**
> When you cascaded the additional routers to act as switches, did you plug the cables from the "real" router into the WAN port on each, or into one of the LAN ports?

Rather than so many secondary routers, it might be simpler to use multi-port switches in their stead!

I just checked to make sure I hadn't accidentally plugged one into the WAN port, but yes - they are all plugged into LAN ports. As for why the routers instead of switches... that's just what I had laying around. I mean, doesn't everyone have half a dozen routers just laying around doing nothing? :)

---

### Post by rebeltaz on 2009-10-09
I just wanted to let you, and anyone else whose interested, know that for some reason, I am now able to connect to the OpenWrt LinkSys router as if nothing had ever happened. I haven't changed any settings, connections or parameters. I do recall Ubuntu's Update Manager installing several updates a few nights ago. I think whatever those updates did, that is what fixed my broken connection.

Anyway, just lettin' y'all know....

---

### Post by t0mppa on 2009-10-10
For once it works this way then. Usually it's users posting on these forums about random update x, which killed their wireless or networking, etc. :)

---

