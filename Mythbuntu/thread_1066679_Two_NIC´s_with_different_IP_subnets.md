---
title: "Two NIC´s with different IP subnets?"
date: 2009-02-11
forum: Mythbuntu
---

### Post by Danbc on 2009-02-11
Hi, working on a kinda alternative solution, since my neighbour has setup (or I have for him) a small Mythbuntu client, wich should connect to my Mythbox.

Only problem is that he has his own DSL line (both company lines) so we have set a range on the normal network like this:

me:

Nic1:
IP: 192.168.2.100
Sub: 255.255.255.0
gate:192.168.2.1

Nic2:
IP: 192.168.1.110
Sub: 255.255.255.0
gate:192.168.1.1

Him:
IP: 192.168.1.100
Sub: 255.255.255.0
gate:192.168.1.1

But it doesn´t seem to be working, he can´t see the Mythbox on his network at all, and Im unsure if the NIC2 is doing what it´s supposed to at all...

So anyone have an idea as to how to do this, if at all possible, and preferred in a easely understandable way since Im not that hardcore in the linux world yet :(  (But learning every day!)

---

### Post by dad311 on 2009-02-11
192.168.0.0 - 192.168.255.255 are public IP addresses, they can not be routed over the internet.

If I'm reading this thread correctly, you want to share your mythbuntu box with your neighbor.  If his is true, install Hamachi VPN on both machines.  After installing Hamachi (5-10 min) both machines should act as if they are on the same network.

[http://www.supware.net/HamachiUbuntuHowto/](http://www.supware.net/HamachiUbuntuHowto/)

---

### Post by Danbc on 2009-02-12
Hey Dad311, thanks for trying to help out :)

To clarify a bit, we´ve set a LAN cabel from my network to his (good old drilling in walls and putting the cable in a garden hos under the front lawn kinda thing ;) ), but since we both have routers on our network (with DHCP enabled), they will conflict each other. Come to think about it, I guess I could disable DHCP on our network and assign manually to my PC´s, that would make it a lot easier I think?

---

### Post by dad311 on 2009-02-12
> **Danbc said:**
> Hey Dad311, thanks for trying to help out :)

To clarify a bit, we´ve set a LAN cabel from my network to his (good old drilling in walls and putting the cable in a garden hos under the front lawn kinda thing ;) ), but since we both have routers on our network (with DHCP enabled), they will conflict each other. Come to think about it, I guess I could disable DHCP on our network and assign manually to my PC´s, that would make it a lot easier I think?


The routers(dhcp) should not conflict.  The routers should only assign addresses to the nics that are directly connected to them.

How long(total length) is the ethernet cable between the two houses?

Also will will need to assign ip addresses(addresses and gateway) to the NICs between the houses.

---

### Post by Fire_Chief on 2009-02-12
Does the Myth client need to connect to his network for any reason? Could you connect the client directly to the cable run and just have it sit on your LAN? That way the two networks do not see each other and your DHCP would handle the client box like any other LAN device.

Oh, and DHCP would conflict if you have the two routers connected. Those 4 LAN ports on the back are not special, they behave just like regular switch ports.

Cheers!

---

### Post by JK3mp on 2009-02-12
DHCP shouldn't conflict..and you'd of saved alot by just using hamachi vpn.

---

### Post by nickrout on 2009-02-12
> **Danbc said:**
> Hi, working on a kinda alternative solution, since my neighbour has setup (or I have for him) a small Mythbuntu client, wich should connect to my Mythbox.

Only problem is that he has his own DSL line (both company lines) so we have set a range on the normal network like this:

me:

Nic1:
IP: 192.168.2.100
Sub: 255.255.255.0
gate:192.168.2.1

Nic2:
IP: 192.168.1.110
Sub: 255.255.255.0
gate:192.168.1.1

Him:
IP: 192.168.1.100
Sub: 255.255.255.0
gate:192.168.1.1

But it doesn´t seem to be working, he can´t see the Mythbox on his network at all, and Im unsure if the NIC2 is doing what it´s supposed to at all...

So anyone have an idea as to how to do this, if at all possible, and preferred in a easely understandable way since Im not that hardcore in the linux world yet :(  (But learning every day!)

Is mysql listening on the 192.168.1.0 network?

more fundamentally what does route -n say on each of these machines?

---

### Post by Fire_Chief on 2009-02-13
And is the MythBackend listening on the 192.168.1.0 network? All the docs I've been reading don't mention having a backend on two subnets.

---

### Post by Danbc on 2009-02-13
Wow lot´s of feedback :D


#4 Problem is that they´re not directly connected, they are on a switch, same switch wich the cable to my neighbour is connected to, so the DHCP´s mess with each other.

Cable length is within maximum standard on Cat5E, 30-40m max, so that isn´t a problem, data also flows nicely between us :)

#5 Well, the hope was to set it up so they could access the myth box one way or another either through SAMBA shares or he uses mine as backend for his box. I guess We could do a "box to box" connection, but that would require additional lenght on the cable, since the excisisting cable hits a switch on his network. (As is it´s the case in my end aswell)

#6 Think I´m going to check that Hamachi out, in any case being able to use that kinda tool seems to save me for some troubles at work aswell :D

#7 Ehrrr... Route -n, have to check that when the other side is back from hollyday :) (Looked pretty nice like I totally understood what you are talking about right? ;) I assume it´s the same as a tracert on winblows?

#8
Nothing is really doing anything before we have fixed this routing issue, but well, that was the plan, but I guess that have to be rethought? :D  Then just giving them access to the Sambashares would be sufficient and then he could just transfer my recordings from the Samashares...

Wich I guess means Hamachi?


One of you guys would by any chance know what I did wrong in this case? [http://ubuntuforums.org/showthread.php?t=1066674](http://ubuntuforums.org/showthread.php?t=1066674) I really don´t want to reinstall, coz I finally got everything to work like a charm, and being the Linux noob I am, that took a while :D


In any case I really appricate the help here guys :)

---

### Post by nickrout on 2009-02-13
you do not need hamachi, you simply need to set up your networking correctly.

---

### Post by dad311 on 2009-02-14
> **nickrout said:**
> you do not need hamachi, you simply need to set up your networking correctly.


1) Setup each PC with an 192.168.2.x address.  Run a CROSS-OVER Ethernet cable between the two PCs without using a switch.

2) At this point you should be able to ping PC > PC. 


IMPORTANT!  Connecting a copper wire between two buildings my be harmful to you PC(s).  Each building may have an different electrical ground potential and could fry a PC(s).  Your best solution would be a wireless or fiber connection.

---

### Post by Danbc on 2009-02-14
> **dad311 said:**
> 1) Setup each PC with an 192.168.2.x address.  Run a CROSS-OVER Ethernet cable between the two PCs without using a switch.

2) At this point you should be able to ping PC > PC. 


IMPORTANT!  Connecting a copper wire between two buildings my be harmful to you PC(s).  Each building may have an different electrical ground potential and could fry a PC(s).  Your best solution would be a wireless or fiber connection.

Hmmm... Well, I guess we could just cut the connectors and put new ones on as crossover, didn´t think about that, and would prolly be the easiest solution to the issue.

That´s a winner solution, gonna try that out.. Thanks for the help all, very cool :)

---

