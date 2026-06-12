---
title: "brctl - unidirectional"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by Groggster on 2011-12-02
Hello! I am building a bridge, consisting of four network devices, and i can't quite get it to work properly. So i have created the bridge, and ARP-requests reach the destination, however, when the destination answers to the ARP-request, it is not forwarded by the bridge. It does not even seem to receive the packages. 
This according to Wireshark. Now, using Wireshark, i found that if i start pinging two separate machines, only ARP-requests from one machine gets delivered. If i stop pinging for a couple of seconds from the machine that is being forwarded, the other machines ARP-requests are forwarded instead. I can go about controlling what packages are to be received, but seeing as how the destination can't answer, all traffic fails in the network.

Now, i am using virtual machines (vmware), could that be the problem?

---

### Post by jonobr on 2011-12-02
Hey there


It sounds that with your diligent testing that you have found a bug,kinda reminds me of [this]("https://bugs.launchpad.net/ubuntu/+source/iputils/+bug/664165")
arps not being correctly formed..

Maybe if you could post the wireshark trace, and the mac destination I could have a nosey.......

---

### Post by Groggster on 2011-12-02
I can absolutely supply this information, however, i will wait until tomorrow, since i have shut down the entire network for now, due to a severe level of frustration.

---

### Post by jonobr on 2011-12-02
had many of those days myself!
Have a good evening

---

### Post by Groggster on 2011-12-03
So, i hope i got this right... The file C1 is a Wireshark capture from client 1, C2 is a capture from  clent 2, and obviously Switch is a capture from the bridge/switch. The picture Topology is a quick drawing of my testing topology. I do not have a capture for C3, since this is a client without a GUI, so i could not run Wireshark without some tinkering, and i thought this was unnecessary.

In the presented test, i have sent ICMP-packages from C1 to C2, from C2 to C3 and from C3 to C1. Notice that the switch seems to take turns forwarding packets, and as the clients receive the ARP-requests, they actually do answer, but it does not show up in the switch capture.

I have also done tests with only two clients. In this scenario the switch/bridge does not alternate between forwarding C1 or C2, but rather forwards whoever starts transmitting first. If i stop the ICMP-traffic from the client being forwarded, the packages from the other machine is forwarded instead, even if i start the traffic again.

---

### Post by jonobr on 2011-12-05
Hello


I had a look at your traces, thanks for posting.

I would agree with you that looking at these traces, I can see the arp being issued correct to all F's , the client when it sees the arp relating to it on the respective collision domain responds, and yes, there is no sign of that on the switch trace.

The response packets seem to be correctly formatted, and dont related to the launchpad bug I sent you.

Im going to have to take a pen and piece of paper and all your traces, and map out all hardware address , but again iot does look ok.
In fact it looks as if your switch is just silently discarding any response packets.

In the meantime, stupid question, do you have any firewall or iptables stuff going on your clients or your endpoints that may be dropping these?

I feel silly asking but what the heck.........

---

### Post by jonobr on 2011-12-05
Hi there


I just finished the pen and paper thing , and all the mac addresses do check out, I was hoping to run across some error on the macs but no.

I can look at all the traces provided and see that they are what they say they are and all looks well.

One question I have which I did notice while I was doing this.
Your ICMP requests which go unanswered,
the pings which go out have the correct target device mac address already in there. That seems to be the case for the pings used.
Seems to show the Macs have at this point already been learned and can be put into a packet to the destination? Have you populated your arp cache yourself?

PS , I think on this one, Im going to have to dust off the RFC, its been a while :-0

---

### Post by Groggster on 2011-12-06
Hey! No, i am not using any form of firewall, or anything of that sort. In fact, i can connect all the clients to each other directly, and then everything works just fine!

Yes, i forgot to mention that, i actually did try to manually enter an ARP-record in the clients, but this did not fix the problem. And as you can see, the switch does not even seem to receive the ICMP-packet, even though the addressing seems to be correct. I have also verified that the switch mac address table is correct, so as you would expect, that part of the switch seems to be working properly.

This is screwing with my head...

---

### Post by jonobr on 2011-12-06
Manually inserting arp entries is ok, but you know yourself, defeats the purpose of Arping.

I find a lot strange here, in particular as you said the pings aren't even seen by the switch.
You would expect to see that traffic traversing.
I expected that maybe you had limited your packet capture , but unless you have specifically filtered for arp, you should see it.

I wish I could say , aha, you have the wrong thing in here or there,
but from your traces, everything seems ok,
if there was a router in between the C's clocking ICMP and not passing the arp that would also make sense , but given its one subnet again that doesn't hold water.

I hate to admit when I beaten but all looks ok to me and ready to work.:confused:

---

### Post by Groggster on 2011-12-13
After getting a hold on a physical machine i can now safely say that yes, these issues were caused by VMware, and not by the configuration or the OS. I copy/pasted all of my configuration into the physical machine, and it worked like a charm! Thanks for your time though!

---

### Post by jonobr on 2011-12-13
Thanks for posting back.

It didnt make a lot of sense to me why this wasnt working and with Vmware, Im still not sure why the interface was not seeing the ICMP request going around.

The only thing I can figure is that in vmware, "its arp Jim , but not as we know it.." 

have a good one

jonobr

---

