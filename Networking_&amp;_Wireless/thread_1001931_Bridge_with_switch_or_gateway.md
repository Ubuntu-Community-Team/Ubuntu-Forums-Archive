---
title: "Bridge with switch or gateway?"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by Xyem on 2008-12-04
I am now in a situation where I don't have a wired connection to the internet and rather than shell out for several wireless devices and lose my Gigabit ethernet I was considering setting up a wired -> wireless bridge.

However, I thought of an issue while I was explaining to a work colleague. The intended layout was like this:

Computer A, B, C, D are connected to each other using a switch ( NetGear GS608 ). Computer A has a wireless interface connected to the router. The wired and wireless interface are bridged which allows B, C, and D to transparently connect to the internet ( and the other computer on the network ) as Computer A would just pass the packets on over the wireless as required.

But, if I am using a switch, when B, C, or D try to send a packet to the router, won't the switch not recognise the ( mac? ) address and drop the packets instead of passing them onto Computer A to be sent over the wireless?

If so, what is the solution? Spoofing the mac of the router ( and all other computers on the wireless side of the network ) on Computer A to get the switch to pass it all "unrecognised" packets? Creating a secondary LAN and set up Computer A to be a gateway ( DHCP server etc. )?

Please advise :)

---

### Post by rickyjones on 2008-12-04
So you have a little network of hard wired computers and the only way to get to the internet is through a wireless connection - right?

If so then make it easy on yourself - pick up a Wireless Bridge. This will connect to the wireless network and then the wired side would plug into your switch. This should act as a router or just expand the other wireless network (essentially plugging in a cable to the wifi network).

-Richard

---

### Post by Xyem on 2008-12-04
Won't this just leave me with the same issue where the switch won't forward packets to it?

By the way, Computer A is an always-on server.

---

### Post by rickyjones on 2008-12-04
The bridge device will take care of sending packets to the correct place. The switch will work the way it always has - it'll move traffic where it needs to. The switch would see the bridge and identify that certain packets go through it. Simple as that.

If computer A is an always on server then an alternative is to share the wireless and create a sub-network behind it in a way.

Either way would work - I just feel a bridging device would be much easier to implement.

-Richard

---

### Post by redmk2 on 2008-12-04
> **Xyem said:**
> I am now in a situation where I don't have a wired connection to the internet and rather than shell out for several wireless devices and lose my Gigabit ethernet I was considering setting up a wired -> wireless bridge.

Bridging is a LAN protocol. It allows you to associate NIC's by MAC address.  So the bridging will allow all your hosts to appear to be on the same LAN segment.  This is layer 2 of the OSI connectivity stack.  No TCP/IP in this layer.  Think more along the lines of using Host A as a router between the wired interface and the wireless interface.> 

However, I thought of an issue while I was explaining to a work colleague. The intended layout was like this:

Computer A, B, C, D are connected to each other using a switch ( NetGear GS608 ). Computer A has a wireless interface connected to the router. The wired and wireless interface are bridged which allows B, C, and D to transparently connect to the internet ( and the other computer on the network ) as Computer A would just pass the packets on over the wireless as required.

Not really you would have to bridge all the interfaces.  Once again think of the technologies.  There are LAN protocols (layer2) such as  Ethernet, ARP and MAC addressing.  Then there are inter-networking layer 3 items such as IP addressing and layer 4 protocols for network transportation (TCP/UDP).> 

But, if I am using a switch, when B, C, or D try to send a packet to the router, won't the switch not recognise the ( mac? ) address and drop the packets instead of passing them onto Computer A to be sent over the wireless?
Switches don't send anything anywhere.  The act more like filters.  Each port learns the MAC address of the device attached to it and allows traffic pass based on that MAC address.  If you move the device to another port on the switch the switch just learns the new MAC address.> 

If so, what is the solution? Spoofing the mac of the router ( and all other computers on the wireless side of the network ) on Computer A to get the switch to pass it all "unrecognised" packets? Creating a secondary LAN and set up Computer A to be a gateway ( DHCP server etc. )?

Please advise :)

My advice is to not bridge anything. All of wired hosts should be placed in the same IP network segment ie; [COLOR="Green"]192.168.1.0/24[/COLOR]. The wireless interface should be in a different network (maybe [COLOR="Blue"]192.168.2.0/24[/COLOR].  Host A is a multi-homed host (wired/wireless) and as such should be configured to be used as a router between the 2 networks.

How would a typical packet travel from host B to the internet? From host B to A via the switch using Layer2 protocols.  It is then routed from the wired interface to the wireless interface and on to the internet using layer 3 and 4 protocols.

---

### Post by Xyem on 2008-12-05
Last night I had a bash at the bridging and I did hit the problem where Computer A would only receive packets for itself because of the switch. Other than that, the bridge seemed to be working in some sense ( bwm-ng showed activity on eth1 and br0 but nothing on wlan0 ).

redmk2: So basically, create a ( second ) network of all the wired computers and have Computer A act as a router/gateway with a DHCP server and the like? Won't this cause issues with Samba/Windows shares due to the differing subnets(?) as there are other computers on the "other end" of the wireless..

Thanks for the help so far, very informative :)

---

### Post by bab1 on 2008-12-05
Bridging of multi-homed hosts can cause routing loops.

---

### Post by redmk2 on 2008-12-05
> So basically, create a ( second ) network of all the wired computers and have Computer A act as a router/gateway with a DHCP server and the like?  Yes we would have have 2 networks.  I would set the IP addresses manually (no DHCP).> Won't this cause issues with Samba/Windows shares due to the differing subnets(?) 
Samba can be told to listen on both (specific) interfaces. Another reason to setup static IP addresses. 
> ...as there are other computers on the "other end" of the wireless..
 What does this mean?  What is 'the "other end"'?

---

### Post by psusi on 2008-12-05
A switch is also a bridge.  If you set up a computer as a bridge, it will behave the same as if you had a switch sitting there with one port happening to be wired and one wireless.  It will take care of forwarding packets to the right place.

You can't just go and make a new subnet because you need to be on the same subnet as the router if you want to reach the Internet.  If you want you can create a whole separate network for the wired computers and have the one act as a router itself doing ip masquerading, but that's probably more complex than needed.

Once you set up the bridge interface to connect the wired and wireless ports, it should correctly forward packets back and forth between the other wired computers and the wireless router.

---

### Post by bab1 on 2008-12-05
> **psusi said:**
> A switch is also a bridge. Not so.  See [here]("http://searchnetworking.techtarget.com/expert/KnowledgebaseAnswer/0,289625,sid7_gci851025,00.html").  The effect may be the same in some cases but the devices are distinctly different. 
>  If you set up a computer as a bridge, it will behave the same as if you had a switch sitting there with one port happening to be wired and one wireless.  It will take care of forwarding packets to the right place.****

You can't just go and make a new subnet because you need to be on the same subnet as the router Why can't you have 2 routers in the chain.  Each router is a hop.> if you want to reach the Internet.  If you want you can create a whole separate network for the wired computers and have the one act as a router itself doing ip masquerading, but that's probably more complex than needed.  Huh???> 

Once you set up the bridge interface to connect the wired and wireless ports, it should correctly forward packets back and forth between the other wired computers and the wireless router.But it did not work.  As Xyem said > Other than that, the bridge seemed to be working in some sense ( bwm-ng showed activity on eth1 and br0 **but nothing on wlan0** ).


---

### Post by psusi on 2008-12-05
> **bab1 said:**
> Not so.  See [here]("http://searchnetworking.techtarget.com/expert/KnowledgebaseAnswer/0,289625,sid7_gci851025,00.html").  The effect may be the same in some cases but the devices are distinctly different. 

There isn't anything in that article that contradicts what I said, but since you take issue with it, let me clarify.  A bridge forwards packets between network segments when they are addressed to a device on the other segment.  A switch essentially treats every port as its own network segment and bridges between them.  Bridging the two interfaces in Linux makes the computer behave just like a two port switch would, including the use of the 802.1D spanning tree protocol.

> **bab1 said:**
> 
Why can't you have 2 routers in the chain.  Each router is a hop.

I said you can, but configuring the computer to be an IP masquerading router behind the IP masquerading wireless router is a bit overkill, and it sounded like the OP would rather have the computers be able to directly speak with the wireless router.

> **bab1 said:**
> 
Huh???But it did not work.  As Xyem said

That does not mean it can't when configured correctly.

---

### Post by bab1 on 2008-12-05
So you are saying that if 2 hosts with differing IP networks are connected to a switch they will communicate.  Bridging is not built into switches as far as I know.

---

### Post by psusi on 2008-12-05
> **bab1 said:**
> So you are saying that if 2 hosts with differing IP networks are connected to a switch they will communicate.  Bridging is not built into switches as far as I know.

No, I am not.  Bridging takes place at the Ethernet layer, not the IP layer.  Switches bridge every port to every other port, which is why any device can send Ethernet frames to any other device on the same network.

It helps to think of the difference between a hub and a switch.  A hub just forwards the electrical signals directly between all ports without any intelligence, creating a single network segment for all the connected hosts.  A switch is smart enough to look at the destination mac address and only forward the packet to the correct port.  That process is also known as bridging.  It used to be that most people would use hubs to connect most of the computers on the network, then connect the two hubs to each other with a bridge, which was essentially just a 2 port switch.

---

### Post by bab1 on 2008-12-05
Bridge devices are for bridging 2 differing IP networks via MAC tables.  See the [**BSD man pages**]("http://www.mirbsd.org/htman/i386/man4/bridge.htm") Yes I know the difference between layer 2 and Layer 3. 

That being said, your notion of not having to define routing at host A has led me to think of other solutions.  How about no routing or bridging configuring.  Place all the hosts on the same IP network (such as 192.168.1.0/24) and add a 2nd switch (a $10 4 port device) to connect both the original switched (hosts a,b,c,d) and the wlan0 interface to each other and the router.  See my attached jpg

---

### Post by psusi on 2008-12-05
> **bab1 said:**
> Bridge devices are for bridging 2 differing IP networks via MAC tables.  See the [**BSD man pages**]("http://www.mirbsd.org/htman/i386/man4/bridge.htm") Yes I know the difference between layer 2 and Layer 3. 

No, bridges connect two networks at layer 2.  A ROUTER forwards IP packets between two IP networks.

> **bab1 said:**
> 
That being said, your notion of not having to define routing at host A has led me to think of other solutions.  How about no routing or bridging configuring.  Place all the hosts on the same IP network (such as 192.168.1.0/24) and add a 2nd switch (a $10 4 port device) to connect both the original switched (hosts a,b,c,d) and the wlan0 interface to each other and the router.  See my attached jpg

The problem the OP has is that he does not HAVE a wire to the router ( switch A in your diagram ), so he wants to bridge his switch to the one with the router via the wireless.

---

### Post by sanemanmad on 2009-01-20
Dont worry about your switch dropping the packets, the switch will know where to send the packets (think of a cheap wireless router, essentially a switch with a WLAN card built-in and they're bridged :) . See my point. It will work.

---

### Post by Xyem on 2009-01-20
My apologies to everyone who has contributed their knowledge, the forum wasn't e-mailing me and it wasn't showing up in my subscribed threads with unread messages.

I think that the physical set-up ( at least, my description of it ) is causing confusion. Would it be easier if I doodled a diagram ( or used Dia ) of it?

I'll try again to describe it in words.

In my room I have 4 computers ( A, B, C, D ) connected together with this [wired switch]("http://www.netgear.com/Products/Switches/DesktopSwitches/GS608.aspx") using their eth0 interfaces. Computer A also has a wlan0 interface.
Elsewhere in the house, there are several laptops and a computer ( E ) which connect to the router ( Linksys WRT54G ) using wireless and wired connections. Computer A also connects to the router through wlan0.

What I would like to do is get computer A to bridge the network attached to its eth0 and the one on its wlan0 so that computer B could "talk" to computer E through its eth0/only interface:
*Computer B -> ( Wired ) -> Computer A -> ( Wireless ) -> Router -> ( Wired ) -> Computer E*
Also, this would mean computer B could get its IP through DHCP:
*Router -> ( Wireless ) -> Computer A -> ( Wired ) -> Computer B*

So far, when I bridge eth0 and wlan0 on computer A I witness the following:
Pinging computer A from computer B with a large packet size shows ( in bwn-ng ) activity on eth0 and br0 ( this is how I expect it would behave ) on computer A.
Pinging computer E from computer B in the same way results in no activity at all ( and ping shows errors ). Pinging E and B from A is fine.

From this, I concluded ( with my limited network knowledge ) that the switch between computer A and B is dropping the packets because computer E is not attached to it, instead of sending them to computer A to be "relayed" over the wireless.

Thanks for your patience and sharing your knowledge, it's very appreciated, enlightening and will be put to good use.

---

