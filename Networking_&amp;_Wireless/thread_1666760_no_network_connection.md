---
title: "no network connection"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by Red Kelly on 2011-01-14
Why wont it work! ](*,)

It should be easy all the tutorials and setup guides just say it should just work.

I have 2 computers one laptop and one desktop both with Ubuntu 10.10.
the desk top has 2 network ports one going to a modem and the other to a switch, the laptop connects to the switch. 
I wont to get a network going ultimately so I have internet on the laptop as well but for now I would be happy just to get a signal between the 2. 
I have tried everything I can think of and read and tried things for the last 6 weeks and still cant get the stupid thing working.  Almost all of the tutorials and information is on how to connect to windows networks. and anything I have found about between networking 2 or more Linux based computers is aimed at administration and expects u to know what they are talking about. 
So what setting do I need to set or programs install to get this to work?

I don't know what details to give you except that no matter what i try on the laptop (automatic, manual) auto eth0 always comes up showing no network conection. the same for the auto eth1 on the desktop. (auto eth0 is internet and has a connection).

Really getting sick of this by now. So close to moving back to windows.

---

### Post by grahammechanical on 2011-01-14
I am not an expert but by answering I will bring your post to the top of the forum page.

In my opinion. if I was trying to do what you want to do I would connect the modem to the switch and then connect both computers to the switch.

The desktop is getting a connection because it is connected to the modem. The laptop is not getting an internet connection because it is not connected to the modem through the switch.

Regards.

---

### Post by Red Kelly on 2011-01-14
I found this [http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/) website. going to read for the next few weeks. by the time I finish I should know the thing back to front.

---

### Post by Iowan on 2011-01-14
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a thread that might also help.

---

### Post by Red Kelly on 2011-01-14
Thanks Iowan but that assumes that a network already exists I don't have one and that is my problem.
But thanks anyway have bookmarked it for later.

---

### Post by dandnsmith on 2011-01-15
> **grahammechanical said:**
> 
In my opinion. if I was trying to do what you want to do I would connect the modem to the switch and then connect both computers to the switch.

The desktop is getting a connection because it is connected to the modem. The laptop is not getting an internet connection because it is not connected to the modem through the switch.

Regards.

If it really is a switch, then that may not work - depends on the internet interface. If it is through a routing modem, OK, otherwise there would be nothing to route the threads of conversation.

There is a reasonable chance that the firewall isn't connected/configured correctly. A recent posting showed a user having configured his, not getting the network properly working - but the problem proved to be one of configuration.
Has the term 'masquerading' to get to use the desktop as an automatic proxy come into this at all?

---

### Post by Red Kelly on 2011-01-15
Ok I should clarify here THE PROBLEM IS NOT THE INTERNET!! 
I just wont to get up file sharing. 
At the moment there is no connection between the computers.
I have tried to manualy set the IP addresses and they sometimes say  connected but there is no responce when pinging the other computers IP  address. the connection will also sometimes change to not connected I  can't figger out what is making it change.
When IP addresses are automatic there is no connection. I think I have  just found out that this is because I am using a switch and no computer  is set up as a DHCP server.

---

### Post by dandnsmith on 2011-01-15
If you've checked the IP addresses, and immediately ping and get no response, then there must be either a routing problem or a firewall problem.

Just as a clue, what IP addresses did you set manually?

---

### Post by Iowan on 2011-01-15
Just to cover the bases - The connection between the machines uses a crossover cable, a hub/switch/router, or (possibly) gigabit cards? Addresses are manually configured and in the same subnet? **ifconfig -a** on each machine verifies IP address?

---

