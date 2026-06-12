---
title: "Sharing Cable Modem with Wired Router among 3 computers"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by NewarkDevil5 on 2010-10-18
My one computer has Ubuntu 10.10 (dual boot with XP) on it. I just upgraded last week from 10.4, but that didn't cause this problem as I'm only now trying to set up the network and I didn't have it set up before anyhow.

I want to share my cable modem (Motorola) connection through a NetGear ethernet router with two other computers (one with Windows XP and the other with Ubuntu 10.10). Right now I've got the wiring as follows:

Cable Modem -> Router Uplink jack
Router jack #1 -> Dual Boot Computer
Router jack #2 -> Windows XP Computer
Router jack #3 -> Ubuntu 10.10 Computer

The only computer that actually has internet access is the Dual Boot computer. I'm brand new to networking and really haven't had much success in it.

I've seen where some people have managed to do this by using two ethernet cards on one of their computers, but each one of mine only has one and I really don't want to have to put in another if I can avoid it. The modem has a USB jack on it, but when I tried to hook it up to the dual boot using the USB cord, Ubuntu won't connect to the internet and as such there isn't any connection to share. All I want is to share the modem connection among those three computers and maybe if possible share files and printers.

---

### Post by chili555 on 2010-10-18
It ought to work just as it is wired. All three computers ought to get internet access as shown:

Internet==>Cable Modem==>Router==>Computer

First, check the wiring; make sure the cable modem is indeed attached to the WAN port on the router. Make sure the computers are all attached to the LAN ports. Don't laugh, I've seen wiring errors cause problems before, I've even made them myself.

Next, let's concentrate on one computer at a time. Let's start with computer #3 running Ubuntu 10.10. Reboot it and run this terminal command.```
ifconfig eth0
``` Post back with the first two lines, like this example:> eth0      Link encap:Ethernet  HWaddr 99:16:88:9a:5f:df  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0We'll troubleshoot and go on to the next one.

I will be here for several hours, so I can respond rather quickly.

---

### Post by NewarkDevil5 on 2010-10-18
Ironically enough, the computers are at home and I'm at work; didn't figure on getting such a quick response (THANK YOU). I'll respond with the answers to what you posted in about three hours.

---

### Post by PRC09 on 2010-10-18
Maybe this might help.Some ISP  companies have the mac address of your currently attached and connecting computer as the registered user of that connection.When you attach your router they see the mac address is different and blocks everything except your machine.In your router configuration pages there should be a CLONE MAC Address button,log into your router with the currently connecting machine and clone the address.Then save the changes and exit.Reboot the router and all machines and you should now be able to connect with any machine connected to the router.

Edit: This is assuming that your machines are getting an IP address from the router.....

---

### Post by chili555 on 2010-10-18
> **NewarkDevil5 said:**
> Ironically enough, the computers are at home and I'm at work; didn't figure on getting such a quick response (THANK YOU). I'll respond with the answers to what you posted in about three hours.I'll be around and I'll look for your reply. Have a fun day at work!

---

### Post by btindie on 2010-10-18
@[NewarkDevil5]("http://joeb454.ubuntuforums.org/member.php?u=574354"): In the thread that you originally posted to, the guy there was also using a cable modem. He was using MAC cloning on his router, I don't know if this is something you'd also need to do?

---

### Post by NewarkDevil5 on 2010-10-18
> **chili555 said:**
> It ought to work just as it is wired. All three computers ought to get internet access as shown:

Internet==>Cable Modem==>Router==>Computer

First, check the wiring; make sure the cable modem is indeed attached to the WAN port on the router. Make sure the computers are all attached to the LAN ports. Don't laugh, I've seen wiring errors cause problems before, I've even made them myself.

Next, let's concentrate on one computer at a time. Let's start with computer #3 running Ubuntu 10.10. Reboot it and run this terminal command.```
ifconfig eth0
``` Post back with the first two lines, like this example:We'll troubleshoot and go on to the next one.

I will be here for several hours, so I can respond rather quickly.

eth0      Link encap:Ethernet  HWaddr 00:40:ca:68:dd:be  
          inet6 addr: fe80::240:caff:fe68:ddbe/64 Scope:Link

---

### Post by chili555 on 2010-10-18
So, eth0 doesn't get an IP address, but the interface is created, indicating that there is a valid driver. We're half-way done!

Now, let's see why it doesn't connect:```
dmesg | grep eth0
```This is likely to be short, unless there is a problem. Also, see if this shows a link is detected:```
sudo ethtool eth0
```Are there lights, LEDs actually, at both the NIC card and the router indicating a link for computer #3?

---

### Post by NewarkDevil5 on 2010-10-19
> **chili555 said:**
> So, eth0 doesn't get an IP address, but the interface is created, indicating that there is a valid driver. We're half-way done!

Now, let's see why it doesn't connect:```
dmesg | grep eth0
```
[    1.338206] tg3 0000:05:02.0: eth0: Tigon3 [partno(BCM95782A50) rev 3003] (PCI:33MHz:32-bit) MAC address 00:40:ca:68:dd:be
[    1.338212] tg3 0000:05:02.0: eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0])
[    1.338216] tg3 0000:05:02.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.338220] tg3 0000:05:02.0: eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[   16.307472] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.167925] tg3 0000:05:02.0: eth0: Link is up at 100 Mbps, half duplex
[   18.167931] tg3 0000:05:02.0: eth0: Flow control is off for TX and off for RX
[   18.168043] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.024022] eth0: no IPv6 routers present

> This is likely to be short, unless there is a problem. Also, see if this shows a link is detected:```
sudo ethtool eth0
```
sudo: ethtool: command not found

> Are there lights, LEDs actually, at both the NIC card and the router indicating a link for computer #3?

On the router the green light is on stable and the orange is blinking and on the computer the orange is stable and the green is blinking.

---

### Post by CharlesA on 2010-10-19
I would suggest trying a different cable. It looks like it's only using half-duplex, where as most handle full duplex. Are you using CAT5 or CAT5e?

Do the settings on the router look ok?

You can install ethtool by running this:

```
sudo apt-get install ethtool
```

---

### Post by MechaMechanism on 2010-10-19
Lets try the simple approach first.  Buy a five or 8 port Netgear switch.  Run cable modem into the switch.  Then connect the devices to the switch.  Each machine should get it's own IP address.  My ISP is Bresnan.net and their great about giving each device it's own IP address.  If your ISP does not do this, then your out for the money or you can go and get a refund on the switch.

The only problem is that there is no LAN.  The only way for the devices to talk to each other would be over the Internet.  But thats easy enough with SSH.

---

### Post by perspectoff on 2010-10-19
> **MechaMechanism said:**
> Lets try the simple approach first.  Buy a five or 8 port Netgear switch.  Run cable modem into the switch.  Then connect the devices to the switch.  Each machine should get it's own IP address.  My ISP is Bresnan.net and their great about giving each device it's own IP address.  If your ISP does not do this, then your out for the money or you can go and get a refund on the switch.

The only problem is that there is no LAN.  The only way for the devices to talk to each other would be over the Internet.  But thats easy enough with SSH.

I disagree. All routers are switches. It is senseless to buy another switch. The quoted solution is an extremely old solution dating back over 10 years.

Having multiple IP WAN addresses is expensive for most home users, and is to be avoided. (That's the reason routers and LAN IP subnets were created in the first place). 

The problem is somewhere in his settings. For troubleshooting, all computers ought to be set to obtain LAN IP addresses (from the router) by DHCP. (Computers that have static LAN IPs may have LAN IPs that are within the router's DHCP pool, causing problems on some older routers.)

Often there is a firewall or other security setting somewhere (happens frequently with Windows computers) that inhibits LAN recognition and participation. (This is a frequent problem with ZoneAlarm, for example.) Troubleshooting should include turning off firewalls and security until the connection is made, then turning them back on one by one until the connection can't be made. The problem would then be with that security device.

(Also Cat5 vs. Cat5e wiring only differs in the gauge of the wire. I wouldn't waste any time thinking about that.)

Two NIC cards aren't necessary on any of the computers.

While MAC cloning is a good idea, it ought to be a trivial setting in almost every router and easily accomplished. Yeah, he ought to clone the MAC address of the computer known to connect. 

(Even so, it has been many years since I have seen an ISP allow only a single MAC address even for home users. Current ISPs have other methods (other than MAC addresses), nowadays, of assuring that only a single location uses a particular login account.)

---

### Post by MechaMechanism on 2010-10-19
> **perspectoff said:**
> Having multiple IP WAN addresses is expensive for most home users, and is to be avoided.
Wow, that sucks.  I'm glad that I use my ISP because they give out as many WAN IP addresses as you want.  You need to move to where I live. :)

---

### Post by perspectoff on 2010-10-19
> **MechaMechanism said:**
> Wow, that sucks.  I'm glad that I use my ISP because they give out as many WAN IP addresses as you want.  You need to move to where I live. :)

Yeah, cool. That'd be a cheap solution (to move across the world). One reason we have gone to IPv6 is because of the multiple IPs unnecessarily used.

There are thousands of websites coming online everyday. If every one had their own IP address, whew! Fortunately, nowadays there are things like URLs, routers, LANs, virtual hosts, etc. etc.

I haven't heard your rationale since the early days of the Internet, lol.

---

### Post by mcoleman44 on 2010-10-19
Also, you need to make sure that you dont have dhcp turned on in the router settings and in the modem. Your modem is already handing out IP's. So if you have your router handing out IP's also youre going to run into alot of problems.

---

### Post by CharlesA on 2010-10-19
> **mcoleman44 said:**
> Also, you need to make sure that you dont have dhcp turned on in the router settings and in the modem. Your modem is already handing out IP's. So if you have your router handing out IP's also youre going to run into alot of problems.

As far as I know, the modem will only assign one ip address and that is your external ip address.

The router needs to have DHCP enabled in order to give each machine an ip address.

Also: Don't hook a regular switch up to a cable modem, use a router.

---

### Post by mcoleman44 on 2010-10-19
And i find it better to just use the router as a switch. Dont plug the ethernet cable from the modem to the port labeled internet. Just hook it to any port other then that one. I say  this because if you hook it to the Internet port youre router will require you to enter the same credentials you have to have for your modem to connect to the internet. This would be bad because every packet you send through your router will have like an 8 bit packet also carrying your credentials, which will most likely slow down your connection.
 
Please correct me if Im wrong on any of this.

---

### Post by mcoleman44 on 2010-10-19
Well my modem does, but then again its a dsl modem not a cable modem

---

### Post by CharlesA on 2010-10-19
> **mcoleman44 said:**
> And i find it better to just use the router as a switch. Dont plug the ethernet cable from the modem to the port labeled internet. Just hook it to any port other then that one. I say  this because if you hook it to the Internet port youre router will require you to enter the same credentials you have to have for your modem to connect to the internet. This would be bad because every packet you send through your router will have like an 8 bit packet also carrying your credentials, which will most likely slow down your connection.
 
Please correct me if Im wrong on any of this.

Doesn't work like that. You store the credentials on the router and it authenticates for you - most of the time only once, since it's an "always on" connection.

It doesn't have to authenticate multiple times per session.

---

### Post by eronstuc on 2010-10-19
I have four computers on my network and they are all on a router
 am using a router from Netgear. You mentioned wired and allthese onnections are wired.
 up to
For the internet connection I am using comcast. This was set up by then to connect to the main computer through the ethernet cable from their box to the ethernet port on the main computer. Just remove this from that location and plug it into the internet connection on the router.

You then connect ethernet cables to the ports to your various computers. My longest cable is 50 feet. The others are in th 15 to 30 feet range as the other computers are various distances from the main computer and the router.

Your router will take on the default gateway address of 192.168.1.1 and connect to the interbnet using the default dhcp of the router. All the other connections will be assigned numbers which will vary.

Mine range fro 192.168.1.2 to 192.168.1.7. However all this will be determined by the brand of router youa re using. This is usually available in a pdf file which was made part of your install. You may wish to change to assigining fixed addresses as it will make knowing which computer you contact more consistent as with dhcp the addresses will change.

regards,

Gary

---

### Post by mcoleman44 on 2010-10-19
Well it must just be dsl, because with my netgear router I have to enter the credentials of the modem for it to connect, unless I hook it to a regular port. And if I have DHCP turned on on both modem and router my speed is cut in half. Im sorry if I confused anyone, I just figured dsl would apply to cable.

---

### Post by CharlesA on 2010-10-19
> **mcoleman44 said:**
> Well it must just be dsl, because with my netgear router I have to enter the credentials of the modem for it to connect, unless I hook it to a regular port. And if I have DHCP turned on on both modem and router my speed is cut in half. Im sorry if I confused anyone, I just figured dsl would apply to cable.

For the most part, the same things apply for DSL vs cable. DSL normally uses a username and password to authenticate while cable normally just uses the modem's MAC address.

I think that the reason it's doing that is because the router isn't configured correctly. Just a guess, but it makes sense.

See the attached screenshot.

---

### Post by chili555 on 2010-10-19
My DSL modem has but one input, the internet and but one output, either a single computer or a router. Since it has but one output, it has no way, nor any need to run a DHCP server. It is simply going to pass along the public IP address to whatever is connected to it.

If a computer is connected to it, the computer must supply authentication; username and password. It can do so with pppoeconf or its frontend, Network Manager.

If a router is connected, the router gives an IP address via DHCP to all computers attached to it. A computer may specify a static address, ideally outside the range of the DHCP server. Authentication can be in the router or in the computers; not both.> Dont plug the ethernet cable from the modem to the port labeled internet. Just hook it to any port other then that one. 

Please correct me if Im wrong on any of this. You stand corrected; it will not work as you suggest.

The question remains; why won't the Broadcom tg3 get an IP address.> [ 18.168043] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 29.024022] eth0: no IPv6 routers present
This looks pretty healthy; it just doesn't work!

---

### Post by chili555 on 2010-10-19
> The only computer that actually has internet access is the Dual Boot computer.Please go to that computer and run:```
ifconfig eth0
```Please let us know the IP address. Also run:```
route -n
```Please let us know the gateway address.

Ideally, both will have the same prefix, possibly 192.168.x.x.

---

### Post by CharlesA on 2010-10-19
Could also run this on a machine that is having problems getting an ip address.

```
sudo dhclient
```

But yeah, post the ifconfig of the one that works and that'll help us narrow it down.

---

### Post by perspectoff on 2010-10-19
> **mcoleman44 said:**
> Also, you need to make sure that you dont have dhcp turned on in the router settings and in the modem. Your modem is already handing out IP's. So if you have your router handing out IP's also youre going to run into alot of problems.

I don't believe the Motorola Surfboard cable modem has DHCP, nor NAT. 

Also, DSL comes from telephone lines, not cable.

---

### Post by perspectoff on 2010-10-19
> **CharlesA said:**
> For the most part, the same things apply for DSL vs cable. DSL normally uses a username and password to authenticate while cable normally just uses the modem's MAC address.

I think that the reason it's doing that is because the router isn't configured correctly. Just a guess, but it makes sense.



Nah, that's not true. It depends on the ISP, not on whether it uses cable or DSL. 

I have used user/password authentication on both cable and DSL, and MAC address verification for both cable and DSL, as well.

---

### Post by CharlesA on 2010-10-19
> **perspectoff said:**
> I don't believe the Motorola Surfboard cable modem has DHCP, nor NAT. 

Correct. It just "passes on" whatever external ip is assigned by the ISP.

> Also, DSL comes from telephone lines, not cable.

It's the same principle as a cable modem, since there really isn't anything different, the modem part just converts the signal from the line into something the computer can understand and vice verse.

> **perspectoff said:**
> Nah, that's not true. It depends on the ISP, not on whether it uses cable or DSL. 

I have used user/password authentication on both cable and DSL, and MAC address verification for both cable and DSL, as well.

Thanks for the info. I guess that's just how the companies I've used have done it.

---

### Post by perspectoff on 2010-10-19
> **mcoleman44 said:**
> Well it must just be dsl, because with my netgear router I have to enter the credentials of the modem for it to connect, unless I hook it to a regular port. And if I have DHCP turned on on both modem and router my speed is cut in half. Im sorry if I confused anyone, I just figured dsl would apply to cable.

The type of modem you are talking about is a combined router/modem. AT&T, for example, distributes such a combined router/modem (2Wire).

You are correct that when a combined modem/router is used in conjunction with another router (like the Netgear router) one of them must have the DHCP service turned off (since only one DHCP is allowed on a LAN).

But AFAIK, the Motorola Surfboard is a modem only, not a router/modem combination. It has no DHCP service.

---

### Post by mcoleman44 on 2010-10-19
It will work as I suggest Because Ive used that setup for every network I've ever setup. It may not work on your hardware or on OP's hardware but it will work. And yes I'm aware that dsl uses a phone line and cable uses cable. And my motarola Modem Does have dhcp. I can choose the pool it chooses ips from.

---

### Post by linuxonbute on 2010-10-19
Of course the OP said he is new to networking so it might just be worth asking if all his cables are straight and not crossover cables:P

---

### Post by CharlesA on 2010-10-19
> **mcoleman44 said:**
> It will work as I suggest Because Ive used that setup for every network I've ever setup. It may not work on your hardware or on OP's hardware but it will work. And yes I'm aware that dsl uses a phone line and cable uses cable. And my motarola Modem Does have dhcp. I can choose the pool it chooses ips from.

In that case, it is giving out private IP addresses, not public ones, and doing NAT as well.

---

