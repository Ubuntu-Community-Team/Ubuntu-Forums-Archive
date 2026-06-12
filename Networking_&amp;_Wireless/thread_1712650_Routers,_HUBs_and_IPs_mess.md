---
title: "Routers, HUBs and IPs mess"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by GTMoraes on 2011-03-23
Hello There

I'm having a rather irritating issue here.

tl;dr version:
I have two routers. One of them feeds the internets to another. Users on one router can't see users from the other router. I need network capabilities between the both routers and I cannot set up a static IP to everybody. How should I proceed?

Long version:
My interwebs setup is like this:

Phone line goes on the ground level of the house. Goes to a Thomson TG508 modem and it connects to the internet. A cable from the thomson goes to a 8-Port generic HUB and connects to a general-use PC (with a precious printer, available to the LAN) and (will) connect to a Home Theater PC (that I wish to control over the LAN). From the HUB, goes a cable for the D-Link DI-524, a Wireless Router, on the First Floor. This router feeds 4 computers on the north wing, 2 computers on the 2nd floor, a random number of computers (visitors, smartphones...) on the ground level and provides Wireless connection for the bedrooms on the first floor.

With this scenario, I, connected to the Wireless, have network capabilities with everybody that's connected to the Wireless Router. I can't see anybody when I'm on the General-Use PC (which's directly connected to the HUB).
I've heard about setting a static IP to everybody, so every computer can see each other, independent of the router in use. But the fact that many computers and phones comes and goes here, I find this scenario hard to be applied.

Is there any other way I could use?

---------
Forgot to say: I can't leave connected the Wireless router only (now). There won't be cables for the HTPC and the Gen. Use PC.

If there's no workaround, I'll buy longer cables and make the Wireless the only router.

---

### Post by GTMoraes on 2011-03-24
bump

---

### Post by GTMoraes on 2011-03-25
anything?

---

### Post by confusedstingray on 2011-03-25
how do you have the d-link wired for your setup you do not need the wan port just use it as a wifi switch.

it sound like you got 2 subnets 1 from the modem which works with everything up to the dlink
and 1 from the dlink your wireless network that works with everthing connected to the dlink 

need a little more info 

1) which device is doing DHCP 
2) what is the ips infront of the dlink  and what are the ips after the dlink
with that info should be able to give you some direction to solve your issue

---

### Post by GTMoraes on 2011-03-27
> **confusedstingray said:**
> 
it sound like you got 2 subnets 1 from the modem which works with everything up to the dlink
and 1 from the dlink your wireless network that works with everthing connected to the dlink 
You got it

AFAIK, there are two devices doing DHCP here. The Thomson modem (which output goes to a HUB, and from this hub goes to the Wireless router) and the D-Link Wireless router.
I don't know if the HUB does DHCP. Everything connected on it shows up on "Connected" list on the Thomson Modem setup. It's a cheap HUB anyway.

Everybody connected on the D-Link is 192.168.0.x
Everybody cable-connected thru the HUB/Modem is 192.168.1.x
Following this logic, the D-Link should be 192.168.1.something, probably. I don't know if that really matters

I've disconnected all computers from the HUB, leaving only me, the modem and the D-Link directly connected with cable to it.
On the Thomson Setup page, I can see this on Connected list:
"My Host - 192.168.1.63
 GTMoraes-Aspire - 192.168.1.66"
I've tried pinging the "My Host". It doesn't answer. 192.168.1.65 answers, but Google Chrome can't connect to it. I suppose this is the IP set by the modem to the D-Link

Connected on the Wireless, I can access the D-Link and the Thomson modem (192.168.0.1 and 192.168.1.1, respectively). With cable, I can only connect to the Thomson modem.

I don't want to/can't remove the HUB.

Feel free to ask anything else

---

### Post by dandnsmith on 2011-03-27
If you want full connectivity on your network, ie all PCs to internet, and any PC to any other, I'd turn off DHCP on the D-Link, leave it on on the Thomson.

That should take care of all the routing.

If you want the 2 groups separated into mutually inaccesible subnets, I'm not sure how you do it without being able to distinguish between the traffic to the D-Link and the traffic to the other PCs connected to the hub.

---

### Post by GTMoraes on 2011-03-27
Disabling DHCP on the D-Link disables the automatic distribution of IPs over the wireless LAN (Rendering a impossible connection without manually setting up a IP), but your proposition is correct. I need to make the D-Link let Thomson handle the DHCP server

Clicking around on the D-Link setup page, I've ran thru this:
WAN:
IP Address	192.168.1.65  (192.168.1.x comes from the Thomson)
Subnet Mask	255.255.255.0
Gateway		192.168.1.1
DNS 		192.168.1.1

	WAN Settings: 
	Please select the appropriate option to connect to your ISP. 
[X]	Dynamic IP Address - 	Choose this option to obtain an IP address automatically from your ISP. (For most Cable modem users)
[ ]	Static IP Address - 	Choose this option to set static IP information provided to you by your ISP.
[ ]	PPPoE - 	Choose this option if your ISP uses PPPoE. (For most DSL users)
[ ]	Others - 	PPTP , BigPond Cable , L2TP and Telia.


As stated before, I can ping 192.168.1.65 when I'm using cable
The solution looks simple, setting the D-Link to bridge mode so it will only connect the devices and let the Thomson modem handle the DHCP, just like the HUB does. But apparently there is no 'Bridge' mode on the D-Link

Any clues?

------
The Thomson does PPPoE. I'm not a network pro, but I can configure the SNMP, Dynamic routing and the TR-069 configuration on the Thomson. I don't know what they mean or what they do, but might help you guys solving this

---

### Post by GTMoraes on 2011-03-27
I've made it =)
The biggest error here was that I was connecting the Thomson to the WAN port on the D-Link (It's a DI-524, by the way). I was supposed to connect it to one of the LAN ports.
So, what I did:
Resetted the D-Link
Disconnected everything and just let my netbook connected on the D-Link
Set up the D-Link's IP to 192.168.1.98 (the Thomson DHCP starts from 1.100)
Saved. Resetted.
Disconnected and Reconnected (for IP Refresh)
Logged on D-Link, disabled DHCP.
Saved configurations. Disconnected and Reconnected.
Plugged the cable coming from the Thomson on a LAN port (not WAN)
Connected to the Internet.

I've checked on the Thomson admin page, the computers are now listed in there!
I can see the computer with the printer. I'll set up the printer later

Thank you confusedstingray and dandnsmith for the DHCP and IP tips. It really led me to the right place =)

Problem solved.

---

### Post by dandnsmith on 2011-03-28
> The biggest error here was that I was connecting the Thomson to the WAN port on the D-Link (It's a DI-524, by the way). I was supposed to connect it to one of the LAN ports.

I noticed that hadn't been mentioned, and forgot to specifically say it. Some routers you can't plug such a lead in, as the sockets are different.

Glad you've solved it.

---

