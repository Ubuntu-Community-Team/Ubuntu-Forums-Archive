---
title: "question about mpls"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by tapi0n on 2011-06-04
So I've been reading up on mpls (mutliprotocol label switching). I know there are three different types of mpls' (L3,l2 and virtual). But I was wondering which of these three offers best performance and why they do so? 
I can see advantages in all three of them but I can't quite tell which one to go for should I be asked this question. 

Anyone who's got some insight on this subject?

---

### Post by poolet on 2011-06-04
Well, I need to be admit that is a good but difficult question. 
First of all **which of these three offers best performance and why they do so? **I am afraid that I can't answer that question since each one has their own performance and implement. According to your needs it's the best answer that i found.... why?? 


Well L2 MPLS suggest for ATM, frame relay, etc... Most network engineer support that they should be replace the ATM swiches since they have a lot of problems with overhead (delay) some other they found it a good idea for a small network... My opinion is that frame relay are dead. I don't know any company that used frame relay since 2009.. (i guest) and yes ATM have a lot of delay and you need to be exactly correct with metric...


If your needs it's a network topology with QOS and Ip telephony, then you should used L3 MPLS... L3 is protocol that drop packet's for IP telephony also L3 MPLS support only for cisco IOS and 3500+ swiches ( am not sure about that since i have a lot of time to check the market) 

If you need to build a backup swiches you should need to build a mix topology...At L2 you can do  some tricky staff to avoid money and use IP telephony with IOS but for sure you will have a lot of delay .......My opinion, they differ in the way they transport data. Cisco refer that the drawbacks of L2 are: 

# Limited VLAN address space per switched Ethernet domain
# Scalability of spanning tree protocols (IEEE 802.1d) for network redundancy and traffic engineering
# Ethernet MAC address learning rate, which is important to minimize broadcast traffic resulting from unknown MAC addresses.

Well i agree only with the 2nd one but don't forget that cisco refer that only for competition purposes!!!
My suggestion is to figure out what you need first.. Are your interest about IP telephony?? At the future you will need a spanning tree protocol with bridge loops and ensuing broadcast radiation?? 
Answer the following question you should be able to select the best option for your need.... 

Below are some links that they will help you a lot:::

[http://www.juniper.net/techpubs/en_US/junos/topics/concept/mpls-ex-series-vpn-layer2-layer3.html](http://www.juniper.net/techpubs/en_US/junos/topics/concept/mpls-ex-series-vpn-layer2-layer3.html)

[http://www.cisco.com/en/US/products/hw/routers/ps368/products_white_paper09186a00801df1df.shtml]("http://www.cisco.com/en/US/products/hw/routers/ps368/products_white_paper09186a00801dfhttp://1df.shtml")
 
[http://www.cisco.com/en/US/tech/tk436/tk428/technologies_configuration_example09186a00800a6c11.shtml](http://www.cisco.com/en/US/tech/tk436/tk428/technologies_configuration_example09186a00800a6c11.shtml)

Hope to cover you at all!!

---

### Post by tapi0n on 2011-06-05
I think I'd go with virtual lan after reading some more.
Let's say you're working in a company with 2000 employees in 5 different sites (acros Europe) and need QoS for VoIP.

Why would I go for virtual ones?

In my opinion if you're running a big company like that Layer 2 vpns would push the costs (when using frame relay) and like you said ATM is a dying protocol.

This leaves Layer 3 and Virtual vpns. But seeing that when using Layer 3 you're much more dependent on your service provider (you need to use the Layer 3 protocol used by the edge router of the service provider and routing is taken care of by a Layer 3 routing table of the provider) I can imagine sysadmins don't want to be that dependant of their provider?

Now with the virtual lans it's like being on a big ethernet lan. Which has the following advantages (I think, I could be wrong though):

You're on a lan, which makes centralising your infrastructure a lot easier.
You don't need to worry about protocols used by the provider.

Like you said the mac learning rate would be high. But that would only be in the first fase of setting up your network right?

---

### Post by poolet on 2011-06-05
Absolutely..... You can't be wrong with these stuff... Each network engineer has his own cons and pros about any protocol... According on his needs..... The problem that engineers has to face is security. As my network lecturer says if you want a full security in a network topology then you need to unplug the cable... That is a common problem that network enginners have...

I must admit that I was never good with the network theory. Since it is a boring topic but after reading your article I got in trouble to read 3 -4 articles for MPLS and I have to say that it really helps to refresh your memory...

In our topic now virtual allow computers and devices to communicate with each across large distances  without using cables or wireless devices. Also MPLS s only vpns have to look at the top label in a label stack in order to forward a data packet to another device. That's allows to be much faster and more efficient than other types of networks. 

The most notable disadvantage of an MPLS VPN is that it does not provide any security for the data packets that are sent out. This is because MPLS VPNs depend on each device within the network to forward the data packet to the next device..

source:: 

As i mention at the beginning you can't be wrong with your opinion... There are thousound topic - articles about all these stuff...  
Now if your working at a company that has 2000 employees it much better to use MPLS L3 ( thats my opinion ). The reasons that companys run out virtual mpls is that are more easyer (as you mentioned more faster and you don't need to worry about protocols of ISP )

---

### Post by tapi0n on 2011-06-06
Ok cheers mate I appreciate the input :)

---

### Post by poolet on 2011-06-06
glad  to help :)

---

