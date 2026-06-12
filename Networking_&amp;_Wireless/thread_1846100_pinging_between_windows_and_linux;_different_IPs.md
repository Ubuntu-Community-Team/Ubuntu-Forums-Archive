---
title: "pinging between windows and linux; different IPs"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by dhirajkhanna on 2011-09-18
Ok I need to be able to ping a windows machine whose IP cannot be changed (160.11.7.21) from a linux machine whose IP cannot be changed (192.168.1.12). Both have only one ethernet card and I have a four port hub available. Is it possible? NAT using iptables?
Help would be appreciated.

---

### Post by haqking on 2011-09-18
> **dhirajkhanna said:**
> Ok I need to be able to ping a windows machine whose IP cannot be changed (160.11.7.21) from a linux machine whose IP cannot be changed (192.168.1.12). Both have only one ethernet card and I have a four port hub available. Is it possible? NAT using iptables?
Help would be appreciated.


you need a router to have knowledge of the other network, other wise your system does a Boolean AND operation on the IP and its mask to decide where the network is, if it decides it is remote then it send it to somewhere who might know such as a router, if the router has no knowledge of the IP the packet is rejected.

Something needs to be able to say yes its over on that segment etc...a hub cant do that as it they are pretty dumb.

---

### Post by Dangertux on 2011-09-18
In theory you could add arp tables for both systems so long as their IP's don't change. I would just suggest getting a router since doing the above would essentially turn one machine into a router.

---

### Post by haqking on 2011-09-18
> **Dangertux said:**
> In theory you could add arp tables for both systems so long as their IP's don't change. I would just suggest getting a router since doing the above would essentially turn one machine into a router.

ahh yeah good point, if they are static then yeah would work. but as your say it would be easier to get a router.

---

### Post by dhirajkhanna on 2011-09-18
Thanks for the replies.
The IPs are static and will not change and a router is not a possibility. So what do I do?

---

### Post by haqking on 2011-09-18
> **dhirajkhanna said:**
> Thanks for the replies.
The IPs are static and will not change and a router is not a possibility. So what do I do?

create a static arp table
```

[s]arp -s ipaddress macaddress
```[/s]
actually my brain aint working right today, hang on i wil be back...that is red flagging me...LOL (too many sunday lunchtime beers ;-)

---

### Post by dhirajkhanna on 2011-09-18
Thanks a lot. I have no idea about arp, guess will google it and get going. Thanks again, appreciate it.

---

### Post by dhirajkhanna on 2011-09-18
Sorry for the ignorance, but creation of this static arp table is to be done on both the machines or just linux? If it has to be done on windows, is there any specific tool I need?

---

### Post by redmk2 on 2011-09-18
> **dhirajkhanna said:**
> Ok I need to be able to ping a windows machine whose IP cannot be changed (160.11.7.21) from a linux machine whose IP cannot be changed (192.168.1.12). Both have only one ethernet card and I have a four port hub available. Is it possible? 
The simple answer is no.  You cant directly connect two hosts that reside on separate networks.> 
NAT using iptables?
IPtables is used to forward data from one network to another and you need 2 network adapters in the host running IPtables to do that.  That would not be a practical solution.> 
Help would be appreciated.
If you can't reconfigure one these hosts then you will need a router/switch to interconnect the to networks.

This is the essence of inter-networking (WAN) as opposed to local networking (LAN).

---

### Post by redmk2 on 2011-09-18
> **dhirajkhanna said:**
> Sorry for the ignorance, but creation of this static arp table is to be done on both the machines or just linux? If it has to be done on windows, is there any specific tool I need?

This will only work in a LAN situation.  You can only communicate via ARP on a local link (LAN).

---

### Post by haqking on 2011-09-18
> **redmk2 said:**
> This will only work in a LAN situation.  You can only communicate via ARP on a local link (LAN).

+1

It was driving me mad...LOL...i had a few guinness for lunch LOL

I thought yeah no worries add a static arp entry, then thought hang on no that wont work.

so yeah back to grabbing a router ;-)

---

### Post by Dangertux on 2011-09-18
Oh wow, good catch that isn't an internal ip...Too much sunday morning reply :-P

Since a router is absolutely not a possibility , is perhaps an additional interface a possibility? If you can add an additional interfaces to the machine with the public IP you can set the ip of the Windows machine (I think that was the one with the public). You could assign it a valid internal ip connect that interface to the hub.

Then set up a route to the external interface THROUGH the new interface...So why is it we can't have a router again? 

But outside of turning the Windows machine into a router, and or buying a router yeah you're stuck.

Wait...Hold one...

How do you have a non-private IP address if it's connected to a hub with the inability to change it? I am REALLY confused now.
....Ok...

So after doing a little research, you have a Windows machine with an IP address staticly assigned from a netblock that belong's to Nara Women's University. It is also connected to a hub, which leads me to believe that one of the following  conditions is true.

A ) You have a statically assigned public IP doing nothing connected to a hub, with a computer with a private IP
B ) You have a computer with TWO interfaces one with a static and public IP, the other with either no IP or an internal IP of some kind. Connected to a hub that you wish to talk to a computer with an internal IP.

If it is scenario B , then you can set the route in the box with two interfaces so that your other machine with one interface can access the other. You can do this with iptables, or any other type of routing you want (since you say it's Windows)

If it's NOT scenario B I am very confused as to what you are trying to do and it probably won't work. So can you give us some more information.

How many interfaces are involved with this? What is your primary goal (connection sharing?). I assume there is more than just wanting to ping.

---

### Post by haqking on 2011-09-18
> **Dangertux said:**
> Oh wow, good catch that isn't an internal ip...Too much sunday morning reply :-P

Since a router is absolutely not a possibility , is perhaps an additional interface a possibility? If you can add an additional interfaces to the machine with the public IP you can set the ip of the Windows machine (I think that was the one with the public). You could assign it a valid internal ip connect that interface to the hub.

Then set up a route to the external interface THROUGH the new interface...So why is it we can't have a router again? 

But outside of turning the Windows machine into a router, and or buying a router yeah you're stuck.

Wait...Hold one...

How do you have a non-private IP address if it's connected to a hub with the inability to change it? I am REALLY confused now.
....Ok...

So after doing a little research, you have a Windows machine with an IP address staticly assigned from a netblock that belong's to Narra Women's University. It is also connected to a hub, which leads me to believe that one of the following  conditions is true.

A ) You have a statically assigned public IP doing nothing connected to a hub, with a computer with a private IP
B ) You have a computer with TWO interfaces one with a static and public IP, the other with either no IP or an internal IP of some kind. Connected to a hub that you wish to talk to a computer with an internal IP.

If it is scenario B , then you can set the route in the box with two interfaces so that your other machine with one interface can access the other. You can do this with iptables, or any other type of routing you want (since you say it's Windows)

If it's NOT scenario B I am very confused as to what you are trying to do and it probably won't work. So can you give us some more information.

How many interfaces are involved with this? What is your primary goal (connection sharing?). I assume there is more than just wanting to ping.


ha ha now im really confused.

It struck me that ok thats a WAN IP so where does a hub come in ? LOL

I am pretty sure there is alot more to this not presented here

---

### Post by redmk2 on 2011-09-18
> **Dangertux said:**
> Oh wow, good catch that isn't an internal ip...Too much sunday morning reply :-P

I assume that by *internal ip * you mean [**[COLOR="DarkSlateGray"]RFC1918[/COLOR]**]("http://en.wikipedia.org/wiki/Private_network") IP addressing.> 

Since a router is absolutely not a possibility , is perhaps an additional interface a possibility? If you can add an additional interfaces to the machine with the public IP you can set the ip of the Windows machine (I think that was the one with the public). You could assign it a valid internal ip connect that interface to the hub.
There is no reason that you can't use RFC1918 private addressing in a multi-homed host (router (IPtables)).  This is not done on commercial for obvious reasons, but you can internetwork using a Linux host as a router. The question is why do it.  If you have to add a NIC to provide a local (to the Windows host) IP address, you might as well change the address on the first host.> 

Then set up a route to the external interface THROUGH the new interface...So why is it we can't have a router again? 

But outside of turning the Windows machine into a router, and or buying a router yeah you're stuck.

The point I'm making here is more a theoretical notion than a practical one.  Private IP addresses can be routed, but it is a bad habit to get into and most commercial devices are not setup to allow this.

---

### Post by redmk2 on 2011-09-18
> **haqking said:**
> ha ha now im really confused.

It struck me that ok thats a WAN IP so where does a hub come in ? LOL

I am pretty sure there is alot more to this not presented here

I'll bet that the IP address is irrelevant.  The IP addresses are either routable on not.  WAN or LAN does not describe the interface (in this case) properly.  Public IP addresses are just that public.  They can be used for LAN or WAN interfaces.

Think of the two hosts as just on separate networks with only a hub in available to the user to connect them physically.  Can't be networked, even if you can stick the cables into the holes.  :D

---

### Post by Dangertux on 2011-09-18
> **redmk2 said:**
> There is no reason that you can't use RFC1918 private addressing in a multi-homed host (router (IPtables)).  This is not done on commercial for obvious reasons, but you can internetwork using a Linux host as a router. The question is why do it.  If you have to add a NIC to provide a local (to the Windows host) IP address, you might as well change the address on the first host.

The point I'm making here is more a theoretical notion than a practical one.  Private IP addresses can be routed, but it is a bad habit t get into and most commercial devices are not setup to allow this.

Yes I do mean RFC1918, and I understand what you're saying.

What I don't understand is what the point of this is?  Why can't the ip's be changed? If it's only a local network meaning they are essentially connected physically to eachother through a hub, just change the ip addresses.

However, what I think is happening is there may be 3 interfaces involved. 1 on the Linux machine and 2 on the windows machine. I'm not positive. Nor am I sure what the final destination is supposed to be. Do we just want them to ping eachother? Easy change one of the ip addresses. 

Are we trying to share the probably existing public internet connection. If that is the case some form of routing needs to be done, either with a router or an additional interface. The ip address scheme isn't so important as the physical connections being made here. 

Am I being clear? I don't feel like I am but it's the weekend so what do you expect hehe

Ok yah , that was about as clear as mud... Um.. Try it this way.

I understand that the two ip addresses mentioned are not routable. But in order to come up with an actual solution, we need to know the goal. IE : internet connection sharing. Or...I just want to play a lan game vs the other PC.

---

### Post by dhirajkhanna on 2011-09-18
ok i can't divulge too many details here as i'm dealing with military networks (and not some women's university :) )
the windows machine is interfaced on ethernet with an ip router of a satcom bearer. The IP cannot be changed. The linux machine runs another application which gathers data from a ship's sensors and sends it to the windows machine....the linux machine ip cannot be changed either. router is definitely an option, but not in the current scenario.

---

### Post by Dangertux on 2011-09-18
> **dhirajkhanna said:**
> ok i can't divulge too many details here as i'm dealing with military networks (and not some women's university :) )
the windows machine is interfaced on ethernet with an ip router of a satcom bearer. The IP cannot be changed. The linux machine runs another application which gathers data from a ship's sensors and sends it to the windows machine....the linux machine ip cannot be changed either. router is definitely an option, but not in the current scenario.

Oh hey I worked on DCGS too when I was in the military :-P

Umm if it's the system or a similar system to what I'm thinking of just add the route in the ground stations terminal :-) 

Either using the route manager or the route add command

:-)

---

### Post by redmk2 on 2011-09-18
> **dhirajkhanna said:**
> ok i can't divulge too many details here as i'm dealing with military networks (and not some women's university :) )
the windows machine is interfaced on ethernet with an ip router of a satcom bearer. 

The IP cannot be changed. The linux machine runs another application which gathers data from a ship's sensors and sends it to the windows machine....the linux machine ip cannot be changed either. router is definitely an option, but not in the current scenario.

Not as you have described currently.

---

### Post by uRock on 2011-09-18
I have cleaned up the thread. Feel free to restart the off topic conversation in the Cafe, otherwise please keep the thread on the topic of getting th OP's network working.

---

