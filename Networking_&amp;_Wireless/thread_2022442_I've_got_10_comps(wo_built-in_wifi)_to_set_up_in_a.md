---
title: "I've got 10 comps(w/o built-in wifi) to set up in a place with wifi, but no wired"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by yanom on 2012-07-10
I've got 10 Ubuntu computers without built-in wifi to set up in a place with wifi, but no wired internet. I need some way to get this wifi signal to these computers. I've identified two solutions -

some sort of router that decodes the wifi signal that I can then hook up (directly or with a switch) 10 ethernet cables to so that they can all be online

or (more likely)

small USB wifi adapters that I can plug into each computer. I'd need a recommendation on some usb dongles that will work out-of-the-box or with drivers easily obtainable for Ubuntu.

I'm on a budget of $50-70 USD and I've got to make this happen soon. does anyone know how I can make this work? :confused:

---

### Post by sanderj on 2012-07-11
@ solution 1: the wifi-router should be able to connect a wifi network. Maybe you need "WDS" for that. BTW: 10 ethernet ports is a lot ... maybe you need an additional ethernet switch.

@ solution 2: you could buy 10 cheap USB wifi devices, for example [http://dx.com/p/ultra-mini-nano-usb-2-0-150mbps-802-11b-g-n-wifi-wlan-wireless-network-adapter-white-67532](http://dx.com/p/ultra-mini-nano-usb-2-0-150mbps-802-11b-g-n-wifi-wlan-wireless-network-adapter-white-67532) . 
FYI: I've bought this wifi device, and it works, but it detects less networks than my built-in wifi adapter. So it only works for strong (=nearby) wifi signals.

---

### Post by Kirk Schnable on 2012-07-11
@Solution 1:  WDS might do the trick, but there is another approach you could take.  If you have a WiFi Access Point somewhere, you can connect another router to it as a Client Bridge.  This mode is supported in a number of router firmwares, for example DD-WRT.  You can install DD-WRT on a lot of consumer routers, like many Linksys models, depending on your technical level.  Otherwise, the Ubiquiti AirRouter (available from some vendors on Amazon.com as well as some official resellers as seen on the official site: Ubnt.com but they don't sell to consumers directly) has been a great WiFi tool in my house, and happens to support Client Bridge mode and a lot of features you usually need custom firmware for, out of the box.

@Solution 2:  Yeah, you'll have degraded performance with wireless USB dongles.  Also, I'm not sure what sort of environment this is (office, school, Internet cafe...) but if theft of the USB dongles is a concern, you might be better off with wireless PCI cards.

Just my two cents.

Kirk

---

### Post by pqwoerituytrueiwoq on 2012-07-11
usb plug
[http://www.newegg.com/Product/Product.aspx?Item=33-166-052](http://www.newegg.com/Product/Product.aspx?Item=33-166-052) 150Mbps
[http://www.newegg.com/Product/Product.aspx?Item=33-315-091](http://www.newegg.com/Product/Product.aspx?Item=33-315-091) 150Mbps
   it is small so less likely to get broken off but range may be a issue
mini pci slot
[http://www.newegg.com/Product/Product.aspx?Item=33-166-047](http://www.newegg.com/Product/Product.aspx?Item=33-166-047) 150Mbps
pci slot
[http://www.newegg.com/Product/Product.aspx?Item=33-166-021](http://www.newegg.com/Product/Product.aspx?Item=33-166-021) 54Mbps
[http://www.newegg.com/Product/Product.aspx?Item=33-166-011](http://www.newegg.com/Product/Product.aspx?Item=33-166-011) 150Mbps

all those are known to work in ubuntu that last one will need 12.04 or at the very least a backported kernel

---

### Post by kurt18947 on 2012-07-11
It seems like it'll be tough with that budget.  If you have a router that could be repurposed as a bridge that would sure help.  You'd still need a switch for 10 PCs though afaik.   Kirk brought up an issue I hadn't considered .  I have an Edimax EW7811Un which works very well with RealTek's driver.  It sure would be easy to steal though.  There are knock-offs on Amazon that can be bought for $6 - $7 each but I don't know if they use the same chipset or if they're Linux friendly.

---

### Post by SeijiSensei on 2012-07-11
Are the ten computers physically close enough to create a wired network among them?  If so, I'd put a wifi card on one of them and make it a NAT router.  (It can still function as a workstation while acting as a router.) Connect its ethernet port to a switch and connect the rest of the computers to the switch.  

This [TP-LINK TL-WN722N Wireless Adapter](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045) works well with Linux as it uses the Atheros chipset.  It costs about $20.  

The switch(es) are a different story.  With ten computers you'd need a 16-port switch if you want to buy only one device.  Unfortunately 16-port switches tend to be used in professional applications and are rather pricey compared to 8-port devices.  You can buy two of these [Rosewill switches](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166035) for about $25.  Don't bother with Gigabit speeds; it would be overkill given you're using wifi for the upstream connection.

Finally you need to buy the ethernet cables.  Depending on length they'll cost about $2-5 each.  A [seven-foot cable]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812119159") costs $4 at Newegg.

I don't think there's any way to stay inside your budget installing wifi devices in these machines.  Ten of those TP-Link adapters alone will run you $200.  My solution comes in around $85-90.

It's possible you'll encounter a bandwidth bottleneck over the single wifi connection.  If that occurs, buy a second adapter and use [bonding]("http://www.cyberciti.biz/tips/debian-ubuntu-teaming-aggregating-multiple-network-connections.html") to have them work in concert.

---

### Post by sanderj on 2012-07-11
> **SeijiSensei said:**
> Are the ten computers physically close enough to create a wired network among them?  If so, I'd put a wifi card on one of them and make it a NAT router. 

Brrrr ... IMHO that's asking for complexity and trouble. Just let a router-appliance do its work.

---

### Post by pqwoerituytrueiwoq on 2012-07-11
i should have thought of that considering i set up a machine to do that last sunday
although i was using a single hardware port (eth0 and eth0:1)

rc.local script for system acting as the router
by using rc.local the setting are temporary and a screw up can be fixed by reboot :)
```
echo 1 > /proc/sys/net/ipv4/ip_forward
while [ 0`pidof NetworkManager` -eq 0 ]; do
    sleep 1
done
while [ "`ifconfig eth0 | grep 'inet addr:'`" = "" ]; do
    sleep 2
done
while [ "`ifconfig eth1 | grep 'inet addr:'`" = "" ]; do
    sleep 2
    ifconfig eth1 10.0.0.1 netmask 255.255.0.0
done
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -P FORWARD ACCEPT
service isc-dhcp-server start
exit 0
```eth0 is hardwire
from my dhcpd.conf fille (for dhcp)
```
shared-network 224-29 {
    subnet 10.0.0.0 netmask 255.255.0.0 {
        range 10.0.0.100 10.0.0.199;
        option routers 10.0.0.1;
        option domain-name-servers 8.8.8.8,8.8.4.4;
    }
}
host dhcp-server {
   hardware ethernet 00:00:00:00:00:00 ;
   deny booting ;
}
```that mac address  (00:00:00:00:00:00) should be the wireless cards mac (i think, if i am wrong there are only 2 addresses)
it will assign google's public dns server

this is the [switch]("http://www.newegg.com/Product/Product.aspx?Item=33-320-047") i was using i had got it on sale for $10 some time last year

you don't need two 8 ports switches a 8 and 4 port will work and you can add 1 more system later

---

### Post by SeijiSensei on 2012-07-11
> **sanderj said:**
> Brrrr ... IMHO that's asking for complexity and trouble. Just let a router-appliance do its work.

Are you basing that on actual experience?  I've built a number of NAT routers on Linux boxes without ever having problems.  

If he takes the router appliance route, he'll still need the switches, since no inexpensive router will have enough ports to support ten client machines.  I bought this [ASUS router](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320023) a while back after reading a lot of reviews.  It works well, and I could flash it with DD-WRT.  It would add another $25 or so to his costs, though, when the cost of the wifi adapter is subtracted.

---

### Post by sanderj on 2012-07-11
> **SeijiSensei said:**
> Are you basing that on actual experience?  I've built a number of NAT routers on Linux boxes without ever having problems.  


Yes, actual experience: linux boxes handling IPv6 tunnels. I found it harder to setup (because of the CLI, versus the GUI of modems/routers), and harder to maintain/troubleshoot.

> **SeijiSensei said:**
> 


If he takes the router appliance route, he'll still need the switches, since no inexpensive router will have enough ports to support ten client machines.  I bought this [ASUS router](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320023) a while back after reading a lot of reviews.  It works well, and I could flash it with DD-WRT.  It would add another $25 or so to his costs, though, when the cost of the wifi adapter is subtracted.

Maybe I misunderstand you, but you will always need 10+ ethernet ports (linux or no linux). 

FWIW: The OP could daisy chain two 8-port switches for that. If he finds a modem/router that can act as a Wifi-client, two el-cheapo 8-port switches could be connected to the modem/router.

Considering his tight budget, second-hand hardware would be the best solution.

---

### Post by SeijiSensei on 2012-07-11
> **sanderj said:**
> Maybe I misunderstand you, but you will always need 10+ ethernet ports (linux or no linux). 

FWIW: The OP could daisy chain two 8-port switches for that. If he finds a modem/router that can act as a Wifi-client, two el-cheapo 8-port switches could be connected to the modem/router.

That's precisely the solution I suggested.  Two of those Rosewill 8-port switches will run him about $25.  So his budget with a router and the other hardware I proposed would be

```

 1 - ASUS wifi router                   $43 
 2 - Rosewill switches @ $12 each        24
10 - 7' Ethernet cables @ $4 each        40
 1 - 3' Ethernet cable to daisy-chain     3
 
Total without shipping                 $110

```

Making one of the computers a NAT router would save him about $23 when the router is replaced with a wifi adapter.

---

### Post by miegiel on 2012-07-11
I'd avoid using 10 USB WIFI dongels if posible. That's just asking for trouble.

Regarding ethernet cables: It is probably cheaper to buy enough cable and RJ-45 plugs and borrow a pair of RJ-45 pliers to make your own cables. Premade ethernet cables are sold at ridiculous prices.

---

### Post by sanderj on 2012-07-11
> **SeijiSensei said:**
> That's precisely the solution I suggested.  Two of those Rosewill 8-port switches will run him about $25.  So his budget with a router and the other hardware I proposed would be

```

 1 - ASUS wifi router                   $43 
 2 - Rosewill switches @ $12 each        24
10 - 7' Ethernet cables @ $4 each        40
 1 - 3' Ethernet cable to daisy-chain     3
 
Total without shipping                 $110

```

Making one of the computers a NAT router would save him about $23 when the router is replaced with a wifi adapter.

OK, good point, that would save money indeed. He should then take into account the higher electricity bill and possibly a Wifi adapter.

Anyway: enough solutions for the OP. I would certainly consider buying second-hand stuff to lower the cost (and to be more sustainable and environmental friendly)

---

### Post by pqwoerituytrueiwoq on 2012-07-11
> **SeijiSensei said:**
> That's precisely the solution I suggested.  Two of those Rosewill 8-port switches will run him about $25.  So his budget with a router and the other hardware I proposed would be

```

 1 - ASUS wifi router                   $43 
 2 - Rosewill switches @ $12 each        24
10 - 7' Ethernet cables @ $4 each        40
 1 - 3' Ethernet cable to daisy-chain     3
 
Total without shipping                 $110

```Making one of the computers a NAT router would save him about $23 when the router is replaced with a wifi adapter.
OP has 10 systems
you can plug 3 boxes in to the router and the rest into the switch and one from the switch to the router so you would only need 1 switch
one 4 port router +one 8port switch = 10 ports  (2 excluded for connecting router and switch)

---

### Post by yanom on 2012-07-11
> **sanderj said:**
>  So it only works for strong (=nearby) wifi signals.

sorry - I forgot to mention this, but the WiFi signal is coming from the church accross the street and is rather weak.

---

### Post by miegiel on 2012-07-11
> **yanom said:**
> sorry - I forgot to mention this, but the WiFi signal is coming from the church accross the street and is rather weak.

Is an antenna in the church tower an option? :D Across a street (100m) doesn't have to be a problem if there is direct line of sight and no interference of other wifi networks. No walls, only air and windows, no windows is even better. PC cases, monitors and desks can shield your antenna too. If both buildings have windows through which the antennas can see each other, across a street should work fine. And having only one antenna in a good position is allot better than neither.

---

### Post by sanderj on 2012-07-11
> **yanom said:**
> sorry - I forgot to mention this, but the WiFi signal is coming from the church accross the street and is rather weak.

Ah. That probably makes the "10 USB-wifi-dongles" unfeasible.

I would go for a wifi access pointer that can act as a client. Make sure the Wifi AP "sees" to church AP; put it in a Window.

---

### Post by Kirk Schnable on 2012-07-11
@Running one computer as a NAT bridge for the rest of them: No, I would absolutely not do that, mainly for the reason of "oh no, he shut off his computer, now nobody can get on the Internet!"

@ASUS Router: Are we sure the ASUS router we're recommending will run DD-WRT or otherwise support the client bridge mode he needs?  NewEgg has some Buffalo routers which I believe all support DD-WRT.

@WiFi being across the street: If you weren't on such a tight budget, I'd say spring for a high gain directional antenna so you know you have a reliable link.  

If you eventually get some more budgeted for this project down the road, you'd benefit from having your network between the 10 computers be wired.  Then, if the WiFi bridge doesn't suit your needs, you can look at other options like Motorola Canopy (expensive) or some Ubiquiti airMax equipment (much cheaper).  At my work, we recently setup a 5.8Ghz Ubiquiti PowerBridge and the entire link cost us $500 for 100Mbps.  Not bad at all in the bridging market.  Reliable so far.

My two cents.

Kirk

---

### Post by SeijiSensei on 2012-07-11
> **Kirk Schnable said:**
> @Running one computer as a NAT bridge for the rest of them: No, I would absolutely not do that, mainly for the reason of "oh no, he shut off his computer, now nobody can get on the Internet!"

How about putting a large label next to the power switch that reads, "Don't turn me off!"?  Really, there are fairly straightforward solutions to problems like this.

> @ASUS Router: Are we sure the ASUS router we're recommending will run DD-WRT or otherwise support the client bridge mode he needs?  NewEgg has some Buffalo routers which I believe all support DD-WRT.
> **SeijiSensei said:**
> I bought this [ASUS router](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320023) a while back after reading a lot of reviews.  It works well, and **I could flash it with DD-WRT**.

I don't see why he'd need any bridging.  It's a router.  One side talks to the wifi, the other side talks to the LAN switches.  What bridging does he need?

---

### Post by Kirk Schnable on 2012-07-11
> **SeijiSensei said:**
> How about putting a large label next to the power switch that reads, "Don't turn me off!"?  Really, there are fairly straightforward solutions to problems like this.
I generally try to avoid solutions like that. I find in my environment they don't always work as well as they should.

> **SeijiSensei said:**
> I don't see why he'd need any bridging.  It's a router.  One side talks to the wifi, the other side talks to the LAN switches.  What bridging does he need?
True. You could do it that way if your router supported it.

Sorry, I missed the bit about the firmware flashing already being done.

Kirk

---

### Post by kurt18947 on 2012-07-12
> **Kirk Schnable said:**
> 

<snip>

@WiFi being across the street: If you weren't on such a tight budget, I'd say spring for a high gain directional antenna so you know you have a reliable link.  

<snip>

Kirk

Cantenna?  Here are a couple links:

[http://www.turnpoint.net/wireless/cantennahowto.html](http://www.turnpoint.net/wireless/cantennahowto.html)

[http://www.wikihow.com/Make-a-Cantenna](http://www.wikihow.com/Make-a-Cantenna)

---

### Post by Kirk Schnable on 2012-07-12
A cantenna probably would help and be more within the budget this project is aiming for right now, good thought Kurt.

Kirk

---

